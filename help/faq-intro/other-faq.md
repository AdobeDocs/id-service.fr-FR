---
description: Questions fréquemment posées sur les fonctionnalités et problèmes liés à l’utilisation d’autres solutions Experience Cloud avec le service d’ID.
keywords: Service d’ID
title: Questions fréquentes sur d’autres solutions Experience Cloud
exl-id: d1164951-01c9-4375-981a-f87d8a280e4b
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '186'
ht-degree: 100%

---

# Questions fréquentes sur d’autres solutions Experience Cloud {#faqs-for-other-experience-cloud-solutions}

Questions fréquemment posées sur les fonctionnalités et problèmes liés à l’utilisation d’autres solutions Experience Cloud avec le service d’ID.

## Dynamic Tag Management (DTM) {#section-7ac4b9c1f1fd45a5a03eac3fb5968af7}

**Puis-je utiliser Dynamic Tag Management pour déployer le service d’ID des visiteurs ?**

Oui, il s’agit de l’option de déploiement préférée et recommandée.

Voir [Implémentation standard avec DTM](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445).

## Analytics et Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**L’historique des visites d’un utilisateur sera-t-il exporté d’[!DNL Adobe Analytics] vers [!DNL Audience Manager] une fois le service Experience Cloud Identity mis en œuvre ?**

Il y a deux possibilités :

* Si un utilisateur effectue des visites une fois le service d’ID mis en œuvre, le visiteur et son historique sont alors inclus dans l’exportation des données vers [!DNL Audience Manager].
* Si un utilisateur n’effectue aucune visite une fois le service d’ID mis en œuvre, le visiteur et son historique ne sont alors pas inclus dans l’exportation des données vers Audience Manager. Étant donné qu’il n’existe aucune nouvelle activité, nous n’avons aucun moyen d’associer Analytics ID à Experience Cloud ID.
