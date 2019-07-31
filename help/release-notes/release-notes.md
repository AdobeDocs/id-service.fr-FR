---
description: Fonctionnalités, mises à jour ou modifications apportées au service d'identité d'Experience Cloud.
keywords: Service d’identification
seo-description: Fonctionnalités, mises à jour ou modifications apportées au service d'identité d'Experience Cloud.
seo-title: Notes de mise à jour 2019
title: Notes de mise à jour 2019
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: tm+mt
source-git-commit: 4532d09cc9b4d83fa62c13bd1adac7abdae222b1

---


# Notes de mise à jour 2019 {#release-notes}

Fonctionnalités, mises à jour ou modifications apportées au service d'identité d'Experience Cloud.

## Notes de mise à jour 2019 {#topic-1b9a1c3ec5044e1c987785950f697e25}

Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service [!DNL Experience Cloud] ID.

## Version 4.4 {#version-4point4}

**Nouvelle fonctionnalité**

[Prise en charge de hachage SHA 256 pour setcustomerids](/help/reference/hashing-support.md). Le service ECID (Experience Cloud ID Service) prend en charge l'algorithme de hachage SHA -256 qui permet de transmettre des ID de client ou des adresses électroniques, et transmet des identifiants hachés.

**Correctifs, améliorations, améliorations**

* We made a configuration update to `cookieDomain`. The ECID library now filters out the empty string `cookieDomain` in `initConfig` and uses the top level cookie domain, which is returned by the getDomain method. (CORE-29223)
* We fixed a bug related to `getVisitorValues` in `localVisitor`. (CORE-31287)
* We fixed a bug where there was an inconsistency for the MCOPTOUT value in the Safari browser, returned by the `getVisitorValue` method. (CORE-29719)
* We updated the Opt-in library by adding `optIn.off` to unsubscribe from events.
* We fixed a bug related to the setTimeout function, where `setTimeout` violated the Content Security Policy (CSP) on some customer sites. (CORE-30623)

## Version 4.3 {#version-4point3}

**Prise en charge ITP 2.1**. Si un serveur de suivi est défini dans un CNAME propriétaire, un nouveau cookie (s_ ecid) est placé avec la valeur ECID. La bibliothèque ECID référence la valeur pour conserver l'identifiant au-delà de 7 jours. See [ECID library methods in a Safari ITP world](/help/reference/ecid-library-methods.md).

**Correctif pour la configuration securecookie.**

## Version 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Service Opt-in**. La souscription est une extension de l'identifiant d'expérience (ECID) qui permet de contrôler si les bibliothèques Experience Cloud peuvent créer des cookies dans les pages Web pour les visiteurs. Using [Experience Platform Launch](https://docs.adobelaunch.com/), you can simplify gathering visitor opt-in consents for Experience Cloud solution by enabling Analytics, Target, Audience Manager, and other or all select Experience Cloud solutions to opt-in to your consent management system.

## Version 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Élément | Description |
|---|---|
| L’indicateur `disableIdSyncs` ne fonctionne pas après une certaine chaîne. | Corrigé. Les valeurs définies du `disableidSyncs` paramètre pour la `getInstance` fonction sont désormais honorées. |
| Les iFrames tiers n’obtiennent pas ECID. | Correction d’ECID sous Safari Mobile et dans plusieurs iFrames ne fonctionnant pas. |

