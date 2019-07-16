---
description: Fonctionnalités, mises à jour ou modifications apportées au service d'identité d'Experience Platform.
keywords: Service d’identification
seo-description: Fonctionnalités, mises à jour ou modifications apportées au service d'identité d'Experience Platform.
seo-title: Notes de mise à jour 2019
title: Notes de mise à jour 2019
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# Notes de mise à jour 2019 {#release-notes}

Fonctionnalités, mises à jour ou modifications apportées au service d&#39;identité d&#39;Experience Platform.

## Notes de mise à jour 2019 {#topic-1b9a1c3ec5044e1c987785950f697e25}

Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service [!DNL Experience Cloud] ID.

## Version 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Service Opt-in**. La souscription est une extension de l&#39;identifiant d&#39;expérience (ECID) qui permet de contrôler si les bibliothèques Experience Cloud peuvent créer des cookies dans les pages Web pour les visiteurs. Using [Experience Platform Launch](https://docs.adobelaunch.com/), you can simplify gathering visitor opt-in consents for Experience Cloud solution by enabling Analytics, Target, Audience Manager, and other or all select Experience Cloud solutions to opt-in to your consent management system.

## Version 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Élément | Description |
|---|---|
| L’indicateur `disableIdSyncs` ne fonctionne pas après une certaine chaîne. | Corrigé. Les valeurs définies du `disableidSyncs` paramètre pour la `getInstance` fonction sont désormais honorées. |
| Les iFrames tiers n’obtiennent pas ECID. | Correction d’ECID sous Safari Mobile et dans plusieurs iFrames ne fonctionnant pas. |

