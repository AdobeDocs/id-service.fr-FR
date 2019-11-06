---
description: Questions fréquemment posées sur les fonctionnalités et problèmes liés à l’utilisation d’Analytics avec le service Experience Cloud Identity.
keywords: Service Experience Cloud Identity
seo-description: Questions fréquemment posées sur les fonctionnalités et problèmes liés à l’utilisation d’Analytics avec le service Identity.
seo-title: Questions fréquentes sur Analytics et le service Identity
title: Questions fréquentes sur Analytics et le service Identity
uuid: 35ed79a9-eccc-4b54-8451-606f091c73b7
translation-type: ht
source-git-commit: c4c0b791230422f17292b72fd45ba5689a60adae

---


# Questions fréquentes sur Analytics et le service Identity{#analytics-and-id-service-faqs}

Questions fréquemment posées sur les fonctionnalités et problèmes liés à l’utilisation d’Analytics avec le service Identity.

## Serveurs de suivi {#section-9a2ad7842e364c869e1650480d17f8ef}

**Comment puis-je trouver les informations relatives à mon serveur de suivi ?**

Chaque bloc de code AppMeasurement correctement configuré contient les informations relatives à votre serveur de suivi.

Toutefois, les clients peuvent parfois diviser leur fichier Analytics AppMeasurement en fichiers distincts. Par exemple, certains clients peuvent placer les variables de configuration dans un fichier, utiliser un deuxième fichier pour les modules externes, puis placer le code AppMeasurement dans un troisième fichier. Cette pratique n’est pas recommandée.

Si vous ne trouvez pas les informations relatives à votre serveur de suivi, votre instance Analytics n’est certainement pas configurée correctement. Si vous ne trouvez pas les informations relatives votre serveur de suivi, contactez l’[Assistance clientèle](https://helpx.adobe.com/fr/marketing-cloud/contact-support.html).

**Que se passe-t-il si j’utilise le service Identity et que je change de serveur de suivi ?**

Aucun changement pour les utilisateurs qui ont déjà été authentifiés par le service Identity. Les visiteurs historiques qui ne sont pas passés au service Identity et qui sont toujours identifiés avec un cookie Analytics seront détachés du service. Le nombre d’utilisateurs affectés dépend de la durée d’activité du service Identity. Par exemple, une mise en œuvre où le service Identity a été actif depuis une semaine aura plus d’utilisateurs historiques qu’une mise en œuvre où le service Identity a été actif depuis six mois, puisque les utilisateurs qui sont revenus sur le site ont effectué la migration.

## Mise en œuvre et configuration {#section-6028f55d5b514ae6a631c6a79f42fb89}

**Dois-je configurer un CNAME pour effectuer un suivi des visiteurs dans tous les domaines ?**

Si vous disposez d’un site d’accès principal où les utilisateurs peuvent être identifiés avant de se rendre sur d’autres domaines, un CNAME peut activer le suivi interdomaines dans les navigateurs qui n’acceptent pas les cookies tiers (tels que Safari).

Dans les navigateurs qui acceptent les cookies tiers, un cookie est défini dans le [domaine demdex.net](https://docs.adobe.com/content/help/fr-FR/audience-manager/user-guide/reference/demdex-calls.translate.html) durant la requête de récupération d’un identifiant visiteur. Ce cookie permet au service Identity de renvoyer le même identifiant visiteur Experience Cloud sur tous les domaines configurés à l’aide du même ID d’organisation. Dans les navigateurs qui n’acceptent pas les cookies tiers, un nouvel identifiant visiteur Experience Cloud est attribué pour chaque domaine.

Même si un CNAME est configuré, si le site d’accès principal n’est pas le premier site visité, les visiteurs sont identifiés différemment sur le site secondaire et le site principal dans les navigateurs qui n’acceptent pas les cookies tiers.

**Pourquoi le paramètre Experience Cloud ID (MID) ne figure-t-il pas dans la requête Analytics ?**

Si le service Identity renvoie correctement les informations, mais que le paramètre `MID` n’apparaît pas, vérifiez que vous avez effectué la mise à niveau vers une version prise en charge d’AppMeasurement.

**Mon site peut-il utiliser du code H et AppMeasurement pour JavaScript avec le service Identity ?**

Oui. Tant que les deux fichiers renvoient au même fichier VisitorAPI.js, vous pouvez utiliser un mélange de code H et AppMeasurement pour JavaScript sur votre site.

Cependant, le code H n’est pas pris en charge par le code visitorAPI.js 1.6 ou version ultérieure. Si vous voulez passer à visitorAPI.js 1.6 (ou version ultérieure), vous ne pouvez pas continuer d’utiliser du code H.

**Qu’est-ce qu’une période de grâce et comment puis-je la configurer ?**

Voir [La Période de grâce du service d’identité](../reference/analytics-reference/grace-period.md) et contacter le service [d’assistance clientèle](https://helpx.adobe.com/fr/marketing-cloud/contact-support.html).

**Pourquoi dois-je migrer vers la collecte de données en temps réel (RDC) pour utiliser le service Identity ?**

La migration RDC offre des avantages de performances générales et elle est requise pour vérifier que votre mise en œuvre sera compatible avec les fonctions à venir qui exploiteront le réseau global de notes de périmètre d’Adobe. Voir [Conditions requises pour Analytics : collecte des données régionale](../reference/requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f).

## Création de rapports {#section-123cd55a32e54a45a23beb140becfa8f}

**Quelles sont les causes possibles d’écarts lors de l’utilisation d’Analytics avec le service Identity ?**

Causes possibles d’écarts lors de l’utilisation du service Identity :

* Utilisation permanente du cookie s_vi hérité. Ce type d’utilisation contribue aux écarts dans la collecte de données.
* Double comptabilisation des visiteurs lors de leur navigation d’une enquête vers un pop-up.

## Cookies {#section-b7d5384fbedd47b09e1030211c39a3d1}

**Que se passe-t-il dans Analytics lorsque le service Identity ne peut pas définir le cookie AMCV ?**

Il existe trois scénarios possibles selon lesquels les données Analytics sont, dans ce cas, affectées pour les nouveaux visiteurs :

1. Un utilisateur final quitte une page avant que les cookies AMCV ne soient correctement définis (dans une fenêtre de délai d’attente de 30 secondes).

   Si un visiteur quitte une page avant la fin de son chargement, l’accès Analytics n’est pas envoyé. Dans ce scénario, Analytics ne reçoit pas de données et considère que les données sont perdues en raison d’une fermeture anticipée de la page. Sur la base de nos tests, qui ont inclus les zones géographiques périphériques, nous avons constaté que ce scénario représente en moyenne moins de 1 % du trafic. Il est important de noter que ce scénario se produit parfois même sans la présence du service Identity. C’est une conséquence de l’inclusion du code de la collecte de données Analytics au bas de la page.

1. Un service Identity ou un Analytics ID n’est pas attribué à un utilisateur final dans la fenêtre de délai d’attente de 30 secondes en raison d’une connexion lente ou de la « rotation » du navigateur.

   Le service Identity et l’Analytics ID ne sont pas définis et le visiteur reçoit un ID côté client. Même si cela permet de capturer des données Analytics, le profil du visiteur est interrompu lorsque, sur une page suivante, un Analytics ID est défini. L’ID côté client ne correspond pas non plus à un profil du visiteur existant stocké dans Audience Manager ou Analytics. Cet ID côté client apparaît également sous la forme de deux visiteurs différents dans Analytics si deux domaines distincts sont envoyés dans la même suite de rapports.

1. Un ID de service Identity n’est pas affecté à un utilisateur final dans la fenêtre de délai d’attente de 30 secondes, mais un ID de suivi Analytics standard lui est affecté et la période de grâce n’est pas activée.

   Le scénario 3 produit le même résultat que le scénario 2 en ce sens qu’un ID côté client est utilisé.

>[!TIP]
>
>L’utilisation des dernières mises à jour de VisitorAPI.js et AppMeasurement.js avec les paramètres par défaut devrait éviter tout impact sérieux ou perceptible résultant des trois scénarios peu probables ci-dessus.

>[!MORELIKETHIS]
>
>* [Assistance clientèle](https://helpx.adobe.com/fr/marketing-cloud/contact-support.html)

