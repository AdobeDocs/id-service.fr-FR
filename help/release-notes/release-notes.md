---
description: Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service Experience Cloud Identity.
keywords: Service d’ID
title: Notes de mise à jour 2020
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: ht
source-wordcount: '132'
ht-degree: 100%

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

Pour consulter les notes de mise à jour mensuelles de tous les produits, reportez-vous aux [Notes de mise à jour Experience Cloud](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=fr).
