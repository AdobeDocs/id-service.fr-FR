---
description: Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service Experience Cloud Identity.
keywords: ID Service
seo-description: Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service Experience Cloud Identity.
seo-title: Notes de mise à jour 2020
title: Notes de mise à jour 2020
translation-type: tm+mt
source-git-commit: c4da0f3da99a96d2be7421f49e0e88286d0505e0

---


# Notes de mise à jour d’Experience Cloud - 2020 {#release-notes}

Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service Experience Cloud Identity (ECID).

## Version 4.6

* Indicateur `loadSSL` activé par défaut. Tous les appels au service d’identité seront activés `https` par défaut.  Les clients peuvent définir cette variable sur false s’ils souhaitent appeler Identity Services sur http à partir de leurs `non-ssl` pages.
* Mise à jour de la fonction utilisée pour détecter la `Internet-Explorer (IE)` version, afin de corriger un problème signalé par `ESLint`.
Correction d’un problème de performances `Internet-Explorer (IE) 11` lorsque l’option d’inclusion d’ECID est activéeIn `pre-approval` et mise à jour ultérieurement.

## Version 4.5

* A partir de la version 4.5, ECID rejettera les identifiants vides envoyés à la méthode `setCustomerIDs`. 
* Correction d’un problème survenant lorsque l’inclusion était configurée sur `doesOptInApply=false` et `isIabContext=true`.
