---
description: Questions fréquemment posées sur les fonctionnalités et les problèmes liés à l’utilisation d’autres solutions Experience Cloud avec le service d’ID.
keywords: Service d’identification
seo-description: Questions fréquemment posées sur les fonctionnalités et les problèmes liés à l’utilisation d’autres solutions Experience Cloud avec le service d’ID.
seo-title: Questions fréquentes pour d'autres solutions Experience Cloud
title: Questions fréquentes pour d'autres solutions Experience Cloud
uuid: 7 d 848663-6 cbb -4 d 80-ab 06-7 b 6 d 2 dc 20 e 2 b
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Questions fréquentes pour d&#39;autres solutions Experience Cloud{#faqs-for-other-experience-cloud-solutions}

Questions fréquemment posées sur les fonctionnalités et les problèmes liés à l’utilisation d’autres solutions Experience Cloud avec le service d’ID.

## Dynamic Tag Management (DTM) {#section-7ac4b9c1f1fd45a5a03eac3fb5968af7}

**Puis-je utiliser Dynamic Tag Management pour déployer le service d’identification des visiteurs ?**

Oui, il s’agit de l’option de déploiement préférée et recommandée.

Voir [Mise en œuvre standard avec la gestion dynamique des balises (DTM)](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445).

## Analytics et Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**L&#39;historique des visites d&#39;un utilisateur sera-t-il exporté[!DNL Adobe Analytics][!DNL Audience Manager]après la mise en œuvre du service d&#39;identité d&#39;Experience Platform ?**

Il y a deux possibilités :

* Si un utilisateur effectue des visites une fois le service d’ID mis en œuvre, le visiteur et son historique sont alors inclus dans l’exportation des données vers [!DNL Audience Manager].
* Si un utilisateur n’effectue aucune visite une fois le service d’ID mis en œuvre, le visiteur et son historique ne sont alors pas inclus dans l’exportation des données vers Audience Manager. En l’absence de toute nouvelle activité, il est impossible d’associer les Analytics ID aux Experience Cloud ID.
