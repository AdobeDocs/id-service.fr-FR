---
description: Questions fréquemment posées sur les fonctionnalités et les problèmes liés à l’utilisation d’autres solutions Experience Cloud avec le service d’ID.
keywords: Service d’identification
seo-description: Questions fréquemment posées sur les fonctionnalités et les problèmes liés à l’utilisation d’autres solutions Experience Cloud avec le service d’ID.
seo-title: Questions fréquentes pour d'autres solutions Experience Cloud
title: Questions fréquentes pour d'autres solutions Experience Cloud
uuid: 7 d 848663-6 cbb -4 d 80-ab 06-7 b 6 d 2 dc 20 e 2 b
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# FAQs for other Experience Cloud solutions{#faqs-for-other-experience-cloud-solutions}

Questions fréquemment posées sur les fonctionnalités et les problèmes liés à l’utilisation d’autres solutions Experience Cloud avec le service d’ID.

## Dynamic Tag Management (DTM) {#section-7ac4b9c1f1fd45a5a03eac3fb5968af7}

**Puis-je utiliser Dynamic Tag Management pour déployer le service d’identification des visiteurs ?**

Oui, il s’agit de l’option de déploiement préférée et recommandée.

Voir [Mise en œuvre standard avec la gestion dynamique des balises (DTM)](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445).

## Analytics et Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**L’historique des visites d’un utilisateur sera-t-il exporté d’[!DNL Adobe Analytics]vers[!DNL Audience Manager]une fois le service Experience Cloud ID mis en œuvre ?**

Il y a deux possibilités :

* Si un utilisateur effectue des visites une fois le service d’ID mis en œuvre, le visiteur et son historique sont alors inclus dans l’exportation des données vers [!DNL Audience Manager].
* Si un utilisateur n’effectue aucune visite une fois le service d’ID mis en œuvre, le visiteur et son historique ne sont alors pas inclus dans l’exportation des données vers Audience Manager. En l’absence de toute nouvelle activité, il est impossible d’associer les Analytics ID aux Experience Cloud ID.

