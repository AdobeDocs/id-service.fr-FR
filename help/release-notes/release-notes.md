---
description: Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service Experience Cloud Identity.
keywords: ID Service
seo-description: Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service Experience Cloud Identity.
seo-title: Notes de mise à jour 2020
title: Notes de mise à jour 2020
translation-type: tm+mt
source-git-commit: 25a9af7a28462bc0bd26cf4a5a58203e76a83366

---


# Notes de mise à jour d’Experience Cloud - 2020 {#release-notes}

Versions, mises à jour ou modifications de fonctionnalités du service d’identité Experience Cloud (ECID).

## Version 4.5

* A partir de la version 4.5, ECID rejettera les identifiants vides envoyés à `setCustomerIDs` la méthode. (CORE-38828)
* Correction d’un problème survenant lorsque l’inclusion était mal configurée comme `doesOptInApply=false` et `isIabContext=true.` (CORE-38351)