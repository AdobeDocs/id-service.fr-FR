---
description: Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service Experience Cloud Identity.
keywords: ID Service
seo-description: Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service Experience Cloud Identity.
seo-title: Notes de mise à jour 2020
title: Notes de mise à jour 2020
translation-type: ht
source-git-commit: c4da0f3da99a96d2be7421f49e0e88286d0505e0

---


# Notes de mise à jour d’Experience Cloud - 2020 {#release-notes}

Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées à Experience Cloud Identity Service (ECID).

## Version 4.6

* L’indicateur `loadSSL` est activé par défaut. Tous les appels à Identity Service seront par défaut en `https`.  Les clients peuvent définir ce paramètre sur false s’ils souhaitent appeler Identity Services en HTTP à partir de leurs `non-ssl` pages.
* Mise à jour de la fonction utilisée pour détecter la version d’`Internet-Explorer (IE)`, afin de corriger un problème signalé par `ESLint`.
Correction d’un problème de performances sur `Internet-Explorer (IE) 11` lorsque l’inclusion `pre-approval` est accordée à ECID et que ce dernier est mis à jour ultérieurement.

## Version 4.5

* À partir de la version 4.5, ECID rejettera les identifiants vides envoyés à la méthode `setCustomerIDs`.
* Correction d’un problème survenant lorsque l’inclusion était configurée sur `doesOptInApply=false` et `isIabContext=true`.
