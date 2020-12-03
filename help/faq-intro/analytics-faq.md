---
description: Questions fréquemment posées sur les fonctionnalités et problèmes liés à l’utilisation d’Analytics avec le service Experience Cloud Identity.
keywords: Experience Cloud Identity Service
seo-description: Questions fréquemment posées sur les fonctionnalités et problèmes liés à l’utilisation d’Analytics avec le service Identity.
seo-title: Questions fréquentes sur Analytics et le service Identity
title: Questions fréquentes sur Analytics et le service Identity
uuid: 35ed79a9-eccc-4b54-8451-606f091c73b7
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: tm+mt
source-wordcount: '989'
ht-degree: 100%

---


# Questions fréquentes sur Analytics et le service Identity {#analytics-and-id-service-faqs}

Questions fréquemment posées sur les fonctionnalités et problèmes liés à l’utilisation d’Analytics avec le service Identity.

## Serveurs de suivi {#section-9a2ad7842e364c869e1650480d17f8ef}

**Comment puis-je trouver les informations de mon serveur de suivi ?**

Chaque élément de code AppMeasurement correctement configuré contient les informations de votre serveur de suivi.

Cependant, il arrive parfois que les clients divisent leur fichier Analytics AppMeasurement en fichiers distincts. Par exemple, certains clients placent des variables de configuration dans un fichier, utilisent un second fichier pour les modules externes, puis placent le code AppMeasurement dans un troisième fichier. Cela n’est pas recommandé.

Si vous ne trouvez pas les informations de votre serveur de suivi, il se peut que votre instance Analytics ne soit pas correctement configurée. Contactez l’[Assistance clientèle](https://helpx.adobe.com/fr/marketing-cloud/contact-support.html) si vous ne trouvez pas les informations de votre serveur de suivi.

**Que se passe-t-il si j’utilise le service Identity et que je change de serveur de suivi ?**

Aucun changement pour les utilisateurs qui ont déjà été authentifiés par le service Identity. Les visiteurs historiques qui ne sont pas passés au service Identity et qui sont toujours identifiés avec un cookie Analytics seront détachés du service. Le nombre d’utilisateurs affectés dépend de la durée d’activité du service Identity. Par exemple, une mise en œuvre où le service Identity a été actif depuis une semaine aura plus d’utilisateurs historiques qu’une mise en œuvre où le service Identity a été actif depuis six mois, puisque les utilisateurs qui sont revenus sur le site ont effectué la migration.

## Mise en œuvre et configuration {#section-6028f55d5b514ae6a631c6a79f42fb89}

**Dois-je configurer un CNAME pour effectuer le suivi des visiteurs sur plusieurs domaines ?**

Si vous disposez d’un site d’accès principal où les clients peuvent être identifiés avant de se rendre sur d’autres domaines, un CNAME peut activer le suivi inter-domaines dans les navigateurs qui n’acceptent pas les cookies tiers (comme Safari).

Dans les navigateurs qui acceptent les cookies tiers, un cookie est défini dans le [domaine demdex.net](https://docs.adobe.com/content/help/fr-FR/audience-manager/user-guide/reference/demdex-calls.html) lors de la demande pour récupérer un identifiant visiteur. Ce cookie permet au service Identity de renvoyer le même identifiant visiteur Experience Cloud sur tous les domaines configurés à l’aide du même ID d’organisation. Dans les navigateurs qui rejettent les cookies tiers, un nouvel identifiant visiteur Experience Cloud est attribué pour chaque domaine.

Même lorsqu’un CNAME est configuré, si le site d’entrée principal n’est pas visité en premier, les visiteurs sont identifiés différemment sur le site secondaire et sur le site principal dans les navigateurs qui n’acceptent pas les cookies tiers.

**Pourquoi le paramètre Experience Cloud ID (MID) n’est-il pas présent dans la demande Analytics ?**

Si le service Identity renvoie correctement les informations, mais que le paramètre `MID` n’apparaît pas, vérifiez que vous avez effectué la mise à niveau vers une version prise en charge d’AppMeasurement.

**Mon site peut-il utiliser du code H et AppMeasurement pour JavaScript avec le service Identity ?**

Oui. Tant que les deux fichiers font référence au même fichier VisitorAPI.js, vous pouvez utiliser un mélange de code H et AppMeasurement pour JavaScript sur l’ensemble de votre site.

Cependant, le code H n’est pas pris en charge avec le code visitorAPI.js version 1.6 ou ultérieure. Si vous souhaitez effectuer la mise à niveau vers visitorAPI.js 1.6 (ou version ultérieure), vous ne pouvez pas continuer à utiliser le code H.

**Qu’est-ce qu’une période de grâce et comment la configurer ?**

Voir [La Période de grâce du service d’identité](../reference/analytics-reference/grace-period.md) et contacter le service [d’assistance clientèle](https://helpx.adobe.com/fr/marketing-cloud/contact-support.html).

**Pourquoi dois-je migrer vers la collecte de données régionales (RDC) pour utiliser le service Identity ?**

La collecte de données régionales offre des avantages en termes de performances globales et est requise pour vous assurer que votre implémentation sera prête pour les fonctions à venir qui exploiteront le réseau global de notes de périphérie d’Adobe. Voir [Conditions requises pour Analytics : collecte de données régionales. ](../reference/requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f)

## Création de rapports {#section-123cd55a32e54a45a23beb140becfa8f}

**Quelles sont les causes possibles d’écarts lors de l’utilisation d’Analytics avec le service Identity ?**

Causes possibles d’écarts lors de l’utilisation du service Identity :

* Utilisation continue du cookie s_vi hérité. Cela contribue à des incohérences dans la collecte des données.
* Doublon comptant les visiteurs lorsqu’ils naviguent d’un questionnaire à une fenêtre contextuelle.

## Cookies {#section-b7d5384fbedd47b09e1030211c39a3d1}

**Que se passe-t-il dans Analytics lorsque le service Identity ne peut pas définir le cookie AMCV ?**

Il existe trois scénarios possibles dans lesquels cela affecte les données Analytics pour les nouveaux visiteurs :

1. Un utilisateur final quitte une page avant que les cookies AMCV ne soient définis correctement (dans la fenêtre de délai d’attente de 30 secondes).

   Si un visiteur quitte une page avant qu’elle ne soit chargée, l’accès Analytics n’est pas envoyé. Analytics ne recevra pas de données de ce scénario et considérera que les données ont été perdues lors d’une fermeture anticipée de la page. D’après nos tests qui comprenaient des géographies éloignées, nous avons constaté que ce scénario représentait en moyenne moins d’1 % du trafic. Il est important de noter que ce scénario se produit parfois même sans la présence du service Identity. C’est une conséquence de l’inclusion du code de la collecte de données Analytics au bas de la page.

1. Un service Identity ou un Analytics ID n’est pas attribué à un utilisateur final dans la fenêtre de délai d’attente de 30 secondes en raison d’une connexion lente ou de la « rotation » du navigateur.

   Le service Identity et l’Analytics ID ne sont pas définis et le visiteur reçoit un ID côté client. Cela permet de capturer les données Analytics, mais le profil du visiteur est interrompu lorsque, sur une page suivante, un identifiant Analytics est défini. L’identifiant côté client ne correspond pas non plus à un profil de visiteur existant stocké dans Audience Manager ou Analytics. Cet identifiant côté client s’affiche également sous la forme de deux visiteurs différents dans Analytics si deux domaines distincts sont envoyés dans la même suite de rapports.

1. Un ID de service Identity n’est pas affecté à un utilisateur final dans la fenêtre de délai d’attente de 30 secondes, mais un ID de suivi Analytics standard lui est affecté et la période de grâce n’est pas activée.

   Le scénario 3 produit le même résultat que le scénario 2 en ce sens qu’un ID côté client est utilisé.

>[!TIP]
>
>L’utilisation des dernières mises à jour de VisitorAPI.js et AppMeasurement.js avec les paramètres par défaut devrait éviter tout impact sérieux ou perceptible résultant des trois scénarios peu probables ci-dessus.

>[!MORELIKETHIS]
>
>* [Assistance clientèle](https://helpx.adobe.com/fr/marketing-cloud/contact-support.html)

