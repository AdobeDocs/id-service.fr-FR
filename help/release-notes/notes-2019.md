---
description: Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service Experience Cloud Identity.
keywords: ID Service
seo-description: Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service Experience Cloud Identity.
seo-title: Notes de mise à jour 2019
title: Notes de mise à jour 2019
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: tm+mt
source-git-commit: 25a9af7a28462bc0bd26cf4a5a58203e76a83366

---


# Experience Cloud release notes - 2019 {#release-notes}

Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service Experience Cloud Identity.

## Version 4.4.1

Ajout d’une case à cocher d’approbation de pré-inclusion pour les analyses des médias dans l’extension de lancement ECID (CORE-33185)

**Correctifs**

* Problème avec l’analyse de la chaîne d’entrée preOptInApprovals de l’extension de lancement ECID (CORE-34041)
* Abandon des performances lors de l’utilisation de trackingServer (CORE-32387)

## Version 4.4 {#version-4point4}

**Nouvelle fonctionnalité**

[Prise en charge du hachage SHA-256 pour setCustomerIDs](/help/reference/hashing-support.md). Le service Experience Cloud ID (ECID) prend en charge l’algorithme de hachage SHA-256 qui vous permet de transmettre des ID de client ou des adresses électroniques, et transmet des identifiants hachés.

**Correctifs, améliorations, avancées**

* Nous avons fait une mise à jour de la configuration de `cookieDomain`. La bibliothèque ECID filtre désormais la chaîne vide `cookieDomain` dans `initConfig` et utilise le domaine de cookie de niveau supérieur, qui est renvoyé par la méthode getDomain. (CORE-29223)
* Nous avons corrigé un bogue lié à `getVisitorValues` dans `localVisitor`. (CORE-31287)
* Nous avons corrigé un bogue en raison duquel la valeur MCOPTOUT était incohérente dans le navigateur Safari, renvoyée par la méthode `getVisitorValue`. (CORE-29719)
* Nous avons mis à jour la bibliothèque Opt-in par l’ajout de `optIn.off` pour se désabonner des événements.
* Nous avons corrigé un bogue lié à la fonction setTimeout, en raison duquel `setTimeout` violait la stratégie de sécurité du contenu (CSP) sur certains sites clients. (CORE-30623)

## Version 4.3 {#version-4point3}

**Prise en charge d’ITP 2.1**. Si un serveur de suivi est défini dans un CNAME propriétaire, un nouveau cookie (s_ecid) est placé avec la valeur ECID. La bibliothèque ECID référence la valeur pour conserver l’identifiant au-delà de sept jours. Reportez-vous à la section [Méthodes de bibliothèque ECID dans un univers ITP Safari](/help/reference/ecid-library-methods.md).

**Correction d’un bogue pour la configuration de secureCookie.**

## Version 4.1

Mise à jour `publishDestinations` par nouveau changement d’API. Avec cette mise à jour, les informations du référent de la page peuvent être exposées pendant la synchronisation ID, si nécessaire. (CORE-23693)

## Version 4.2

Prise en charge du module externe Audience Manager pour IAB TCF, disponible via l’objet d’inclusion ECID.

**Correctifs**

* IAB + OptIn ne parvient pas à obtenir le MID pour les clients qui reviennent (CORE-26022)
* Correction d’un bogue sur la configuration de l’inclusion doOptInApply dans la gestion dynamique des balises (DTM-12958).
* L’exclusion ECID désactive les synchronisations d’ID (CORE-23814)

## Version 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Service Opt-in**. Opt-in est une extension de l’Experience Cloud ID (ECID) qui vous permet de contrôler la création de cookies par les bibliothèques Experience Cloud sur les pages web pour les visiteurs (ainsi que de décider quelles sont les bibliothèques concernées). Using [Experience Platform Launch](https://docs.adobelaunch.com/), you can simplify gathering visitor opt-in consents for Experience Cloud solution by enabling Analytics, Target, Audience Manager, and other or all select Experience Cloud solutions to opt-in to your consent management system.

## Version 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Élément | Description |
|---|---|
| L’indicateur`disableIdSyncs` ne fonctionne pas après une certaine chaîne. | Corrigé. Les valeurs définies du `disableidSyncs` paramètre pour la `getInstance` fonction sont désormais honorées. |
| Les iFrames tiers n’obtiennent pas ECID. | Correction d’ECID sous Safari Mobile et dans plusieurs iFrames ne fonctionnant pas. |
