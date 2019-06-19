---
description: Questions fréquemment posées sur les fonctionnalités et les problèmes liés à l’utilisation d’Analytics avec le service d’ID.
keywords: Service d’identification
seo-description: Questions fréquemment posées sur les fonctionnalités et les problèmes liés à l’utilisation d’Analytics avec le service d’ID.
seo-title: Questions fréquentes sur Analytics et le service d’ID
title: Questions fréquentes sur Analytics et le service d’ID
uuid: 35 ed 79 a 9-eccc -4 b 54-8451-606 f 091 c 73 b 7
translation-type: tm+mt
source-git-commit: cce8f5559baa0598fedaccf2fece6ec90cb641b7

---


# Questions fréquentes sur Analytics et le service d’ID{#analytics-and-id-service-faqs}

Questions fréquemment posées sur les fonctionnalités et les problèmes liés à l’utilisation d’Analytics avec le service d’ID.

## Serveurs de suivi {#section-9a2ad7842e364c869e1650480d17f8ef}

**Comment puis-je trouver les informations relatives à mon serveur de suivi ?**

Chaque bloc de code AppMeasurement correctement configuré contient les informations relatives à votre serveur de suivi.

Toutefois, les clients peuvent parfois diviser leur fichier Analytics AppMeasurement en fichiers distincts. Par exemple, certains clients peuvent placer les variables de configuration dans un fichier, utiliser un deuxième fichier pour les modules externes, puis placer le code AppMeasurement dans un troisième fichier. Cette pratique n’est pas recommandée.

Si vous ne trouvez pas les informations relatives à votre serveur de suivi, votre instance Analytics n’est certainement pas configurée correctement. Si vous ne trouvez pas les informations relatives votre serveur de suivi, contactez l’[Assistance clientèle](https://helpx.adobe.com/marketing-cloud/contact-support.html).

**Que se passe-t-il si j’utilise le service d’ID et que je change de serveur de suivi ?**

Aucun changement pour les utilisateurs qui ont déjà été authentifiés par le service d’ID. Les visiteurs historiques qui ne sont pas passés au service d’ID et qui sont toujours identifiés avec un cookie Analytics seront détachés du service. Le nombre d’utilisateurs affectés dépend de la durée d’activité du service d’ID. Par exemple, une mise en œuvre où le service d’ID a été actif depuis une semaine aura plus d’utilisateurs historiques qu’une mise en œuvre où le service d’ID a été actif depuis six mois, parce que les utilisateurs qui sont revenus sur le site ont effectué la migration.

## Implémentation et configuration {#section-6028f55d5b514ae6a631c6a79f42fb89}

**Dois-je configurer un CNAME pour effectuer un suivi des visiteurs dans tous les domaines ?**

Si vous disposez d’un site d’accès principal où les utilisateurs peuvent être identifiés avant de se rendre sur d’autres domaines, un CNAME peut activer le suivi interdomaines dans les navigateurs qui n’acceptent pas les cookies tiers (tels que Safari).

Dans les navigateurs qui acceptent les cookies tiers, un cookie est défini dans le [domaine demdex.net](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html) durant la requête de récupération d’un identifiant visiteur. Ce cookie permet au service d’ID de renvoyer le même identifiant visiteur Experience Cloud sur tous les domaines configurés à l’aide du même ID d’organisation. Dans les navigateurs qui n’acceptent pas les cookies tiers, un nouvel identifiant visiteur Experience Cloud est attribué pour chaque domaine.

Même si un CNAME est configuré, si le site d’accès principal n’est pas le premier site visité, les visiteurs sont identifiés différemment sur le site secondaire et le site principal dans les navigateurs qui n’acceptent pas les cookies tiers.

**Pourquoi le paramètre Experience Cloud ID (MID) ne figure-t-il pas dans la requête Analytics ?**

Si le service d’ID renvoie correctement les informations mais que le paramètre `MID` n’apparaît pas, vérifiez que vous avez effectué la mise à niveau vers une version prise en charge d’AppMeasurement.

**Mon site peut-il utiliser du code H et AppMeasurement pour JavaScript avec le service d’identification ?**

Oui. Tant que les deux fichiers renvoient au même fichier VisitorAPI.js, vous pouvez utiliser un mélange de code H et AppMeasurement pour JavaScript sur votre site.

Cependant, le code H n’est pas pris en charge par le code visitorAPI.js 1.6 ou version ultérieure. Si vous voulez passer à visitorAPI.js 1.6 (ou version ultérieure), vous ne pouvez pas continuer d’utiliser du code H.

**Qu’est-ce qu’une période de grâce et comment puis-je la configurer ?**

Voir [Période de grâce du service d&#39;ID](../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md) et contactez le service d&#39;assistance [clientèle](https://helpx.adobe.com/marketing-cloud/contact-support.html).

**Pourquoi dois-je migrer vers la collecte de données en temps réel (RDC) pour utiliser le service d’ID ?**

La migration RDC offre des avantages de performances générales et elle est requise pour vérifier que votre mise en œuvre sera compatible avec les fonctions à venir qui exploiteront le réseau global de notes de périmètre d’Adobe. Voir [Conditions requises pour Analytics : collecte des données régionale](../mcvid-reference/mcvid-requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f).

## Création de rapports {#section-123cd55a32e54a45a23beb140becfa8f}

**Quelles sont les causes possibles d’écarts lors de l’utilisation d’Analytics avec le service d’ID ?**

Causes possibles d’écarts lors de l’utilisation du service d’ID :

* Utilisation permanente du cookie s_vi hérité. Ce type d’utilisation contribue aux écarts dans la collecte de données.
* Double comptabilisation des visiteurs lors de leur navigation d’une enquête vers un pop-up.

## Cookies {#section-b7d5384fbedd47b09e1030211c39a3d1}

**Que se passe-t-il dans Analytics lorsque le service d’ID ne peut pas définir le cookie AMCV ?**

Il existe trois scénarios possibles selon lesquels les données Analytics sont, dans ce cas, affectées pour les nouveaux visiteurs :

1. Un utilisateur final quitte une page avant que les cookies AMCV ne soient correctement définis (dans une fenêtre de délai d’attente de 30 secondes).

   Si un visiteur quitte une page avant la fin de son chargement, l’accès Analytics n’est pas envoyé. Dans ce scénario, Analytics ne reçoit pas de données et considère que les données sont perdues en raison d’une fermeture anticipée de la page. Sur la base de nos tests, qui ont inclus les zones géographiques périphériques, nous avons constaté que ce scénario représente en moyenne moins de 1 % du trafic. Il est important de noter que ce scénario se produit parfois même sans présence du service MCID ; il s&#39;agit d&#39;un artefact de l&#39;inclusion du code de collecte de données Analytics au bas de la page.

1. Un service d’ID ou un Analytics ID n’est pas attribué à un utilisateur final dans la fenêtre de délai d’attente de 30 secondes en raison d’une connexion lente ou de la « rotation » du navigateur.

   Le service d’ID et l’Analytics ID ne sont pas définis et le visiteur reçoit un ID côté client. Même si cela permet de capturer des données Analytics, le profil du visiteur est interrompu lorsque, sur une page suivante, un Analytics ID est défini. L’ID côté client ne correspond pas non plus à un profil du visiteur existant stocké dans Audience Manager ou Analytics. Cet ID côté client apparaît également sous la forme de deux visiteurs différents dans Analytics si deux domaines distincts sont envoyés dans la même suite de rapports.

1. Un ID de service d’ID n’est pas affecté à un utilisateur final dans la fenêtre de délai d’attente de 30 secondes, mais un ID de suivi Analytics standard lui est affecté et la période de grâce n’est pas activée.

   Le scénario 3 produit le même résultat que le scénario 2 en ce sens qu’un ID côté client est utilisé.

>[!TIP]
>
>L&#39;utilisation des dernières mises à jour de visitorapi. js et d&#39;appmeasurement. js avec les paramètres par défaut évitera tout impact sérieux ou perceptible des trois scénarios improbables ci-dessus.

>[!MORE_ LIKE_ THIS]
>
>* [Assistance clientèle](https://helpx.adobe.com/marketing-cloud/contact-support.html)

