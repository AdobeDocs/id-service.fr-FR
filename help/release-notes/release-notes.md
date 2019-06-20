---
description: Cette section contient des mises à jour, des mises à jour ou des modifications apportées au service Experience Cloud ID.
keywords: Service d’identification
seo-description: Cette section contient des mises à jour, des mises à jour ou des modifications apportées au service Experience Cloud ID.
seo-title: Notes de mise à jour 2019
title: Notes de mise à jour 2019
uuid: a 5 a 59410-7 f 85-48 f 9-a 30 a-fef 1 c 2 e 2 b 558
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Notes de mise à jour 2019 {#release-notes}

Cette section contient des mises à jour, des mises à jour ou des modifications apportées au service Experience Cloud ID.

## Notes de mise à jour 2019 {#topic-1b9a1c3ec5044e1c987785950f697e25}

Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service [!DNL Experience Cloud] ID.

## Version 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Service Opt-in**. La souscription est une extension de l&#39;identifiant d&#39;expérience (ECID) qui permet de contrôler si les bibliothèques Experience Cloud peuvent créer des cookies dans les pages Web pour les visiteurs. Using [Experience Platform Launch](https://docs.adobelaunch.com/), you can simplify gathering visitor opt-in consents for Experience Cloud solution by enabling Analytics, Target, Audience Manager, and other or all select Experience Cloud solutions to opt-in to your consent management system.

## Version 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Élément | Description |
|---|---|
| L’indicateur `disableIdSyncs` ne fonctionne pas après une certaine chaîne. | Fixe. Values set on `disableidSyncs` parameter for `getInstance` function are now being honored. |
| Les iFrames tiers n’obtiennent pas ECID. | Correction d’ECID sous Safari Mobile et dans plusieurs iFrames ne fonctionnant pas. |

