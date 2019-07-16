---
description: Questions fréquentes sur les fonctionnalités, les fonctionnalités et les problèmes liés à l'utilisation d'Analytics avec le service d'identité d'Experience Platform.
keywords: Service d'identité de Platform Platform
seo-description: Questions fréquentes sur les fonctionnalités, les fonctionnalités et les problèmes liés à l'utilisation d'Analytics avec le service d'identité.
seo-title: FAQ sur le service d'analyse et d'identité
title: FAQ sur le service d'analyse et d'identité
uuid: 35ed79a9-eccc-4b54-8451-606f091c73b7
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# Analytics and Identity Service FAQs{#analytics-and-id-service-faqs}

Questions fréquentes sur les fonctionnalités, les fonctionnalités et les problèmes liés à l&#39;utilisation d&#39;Analytics avec le service d&#39;identité.

## Serveurs de suivi {#section-9a2ad7842e364c869e1650480d17f8ef}

**Comment puis-je trouver les informations relatives à mon serveur de suivi ?**

Chaque bloc de code AppMeasurement correctement configuré contient les informations relatives à votre serveur de suivi.

Toutefois, les clients peuvent parfois diviser leur fichier Analytics AppMeasurement en fichiers distincts. Par exemple, certains clients peuvent placer les variables de configuration dans un fichier, utiliser un deuxième fichier pour les modules externes, puis placer le code AppMeasurement dans un troisième fichier. Cette pratique n’est pas recommandée.

Si vous ne trouvez pas les informations relatives à votre serveur de suivi, votre instance Analytics n’est certainement pas configurée correctement. Si vous ne trouvez pas les informations relatives votre serveur de suivi, contactez l’[Assistance clientèle](https://helpx.adobe.com/marketing-cloud/contact-support.html).

**Que se passe-t-il si j&#39;utilise le service d&#39;identité et je change de serveur de suivi ?**

Aucun changement n&#39;est apporté aux utilisateurs qui ont déjà été identifiés par le service d&#39;identité. Les visiteurs hérités qui n&#39;ont pas été migrés vers le service d&#39;identité et qui sont toujours identifiés avec un cookie Analytics sont détachés. Le nombre d&#39;utilisateurs affectés dépend de la durée pendant laquelle le service d&#39;identité a été activé. Par exemple, une implémentation dans laquelle le service d&#39;identité a été actif pendant 1 semaine peut avoir plus d&#39;utilisateurs hérités qu&#39;une implémentation où le service d&#39;identité a été actif pendant 6 mois parce que les utilisateurs qui reviennent sur le site ont été migrés.

## Mise en œuvre et configuration {#section-6028f55d5b514ae6a631c6a79f42fb89}

**Dois-je configurer un CNAME pour effectuer un suivi des visiteurs dans tous les domaines ?**

Si vous disposez d’un site d’accès principal où les utilisateurs peuvent être identifiés avant de se rendre sur d’autres domaines, un CNAME peut activer le suivi interdomaines dans les navigateurs qui n’acceptent pas les cookies tiers (tels que Safari).

Dans les navigateurs qui acceptent les cookies tiers, un cookie est défini dans le [domaine demdex.net](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html) durant la requête de récupération d’un identifiant visiteur. Ce cookie permet au service d&#39;identité de renvoyer le même identifiant visiteur Experience Cloud sur tous les domaines configurés à l&#39;aide du même ID d&#39;organisation. Dans les navigateurs qui n’acceptent pas les cookies tiers, un nouvel identifiant visiteur Experience Cloud est attribué pour chaque domaine.

Même si un CNAME est configuré, si le site d’accès principal n’est pas le premier site visité, les visiteurs sont identifiés différemment sur le site secondaire et le site principal dans les navigateurs qui n’acceptent pas les cookies tiers.

**Pourquoi le paramètre Experience Cloud ID (MID) ne figure-t-il pas dans la requête Analytics ?**

If the Identity Service is returning information correctly but you do not see the `MID` parameter, make sure that you&#39;ve upgraded to a supported version of AppMeasurement.

**Mon site peut-il utiliser du code H et appmeasurement pour JavaScript avec le service d&#39;identité ?**

Oui. Tant que les deux fichiers renvoient au même fichier VisitorAPI.js, vous pouvez utiliser un mélange de code H et AppMeasurement pour JavaScript sur votre site.

Cependant, le code H n’est pas pris en charge par le code visitorAPI.js 1.6 ou version ultérieure. Si vous voulez passer à visitorAPI.js 1.6 (ou version ultérieure), vous ne pouvez pas continuer d’utiliser du code H.

**Qu’est-ce qu’une période de grâce et comment puis-je la configurer ?**

See [The Identity Service Grace Period](../reference/analytics-reference/grace-period.md) and contact [Customer Care](https://helpx.adobe.com/marketing-cloud/contact-support.html).

**Pourquoi dois-je migrer vers la collecte de données en temps réel pour utiliser le service d&#39;identité ?**

La migration RDC offre des avantages de performances générales et elle est requise pour vérifier que votre mise en œuvre sera compatible avec les fonctions à venir qui exploiteront le réseau global de notes de périmètre d’Adobe. Voir [Conditions requises pour Analytics : collecte des données régionale](../reference/requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f).

## Création de rapports {#section-123cd55a32e54a45a23beb140becfa8f}

**Quelles sont les causes possibles de différences lors de l&#39;utilisation d&#39;Analytics avec le service d&#39;identité ?**

Causes courantes de différences lors de l&#39;utilisation du service d&#39;identité :

* Utilisation permanente du cookie s_vi hérité. Ce type d’utilisation contribue aux écarts dans la collecte de données.
* Double comptabilisation des visiteurs lors de leur navigation d’une enquête vers un pop-up.

## Cookies {#section-b7d5384fbedd47b09e1030211c39a3d1}

**Que se passe-t-il dans Analytics lorsque le service d&#39;identité ne peut pas définir le cookie AMCV ?**

Il existe trois scénarios possibles selon lesquels les données Analytics sont, dans ce cas, affectées pour les nouveaux visiteurs :

1. Un utilisateur final quitte une page avant que les cookies AMCV ne soient correctement définis (dans une fenêtre de délai d’attente de 30 secondes).

   Si un visiteur quitte une page avant la fin de son chargement, l’accès Analytics n’est pas envoyé. Dans ce scénario, Analytics ne reçoit pas de données et considère que les données sont perdues en raison d’une fermeture anticipée de la page. Sur la base de nos tests, qui ont inclus les zones géographiques périphériques, nous avons constaté que ce scénario représente en moyenne moins de 1 % du trafic. Il est important de noter que ce scénario se produit parfois même sans présence du service d&#39;identité. Il s&#39;agit d&#39;un artefact de l&#39;inclusion du code de collecte de données Analytics au bas de la page.

1. Fin - l&#39;utilisateur n&#39;obtient pas de service d&#39;identité ou d&#39;Analytics ID dans la fenêtre de délai d&#39;attente de 30 secondes en raison d&#39;une connexion lente ou d&#39;une rotation de navigateur.  » »

   Le service d&#39;identité et l&#39;ID Analytics ne sont pas définis et le visiteur se verra attribuer un identifiant client. Même si cela permet de capturer des données Analytics, le profil du visiteur est interrompu lorsque, sur une page suivante, un Analytics ID est défini. L’ID côté client ne correspond pas non plus à un profil du visiteur existant stocké dans Audience Manager ou Analytics. Cet ID côté client apparaît également sous la forme de deux visiteurs différents dans Analytics si deux domaines distincts sont envoyés dans la même suite de rapports.

1. Fin - l&#39;identifiant de service d&#39;identité n&#39;est pas attribué à l&#39;utilisateur dans la fenêtre de délai d&#39;attente de 30 secondes, mais un identifiant de suivi Analytics standard est affecté et la période de grâce n&#39;est pas activée.

   Le scénario 3 produit le même résultat que le scénario 2 en ce sens qu’un ID côté client est utilisé.

>[!TIP]
>
>L’utilisation des dernières mises à jour de VisitorAPI.js et AppMeasurement.js avec les paramètres par défaut devrait éviter tout impact sérieux ou perceptible résultant des trois scénarios peu probables ci-dessus.

>[!MORE_LIKE_THIS]
>
>* [Assistance clientèle](https://helpx.adobe.com/marketing-cloud/contact-support.html)

