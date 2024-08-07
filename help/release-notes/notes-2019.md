---
description: Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service d’identités d’Experience Cloud.
keywords: Service d’ID
title: Notes de mise à jour 2019
exl-id: 11439e27-9740-4afc-a2b8-5e35d179f34f
source-git-commit: 503683b66b6022b7c1fecbfb197fe17e05ae9c64
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 100%

---

# Notes de mise à jour d’Experience Cloud - 2019 {#release-notes}

Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service d’identités d’Experience Cloud.

## Version 4.4.1

Ajout d’une case à cocher d’approbation de pré-inclusion pour les analyses des médias dans l’extension Launch ECID.

**Correctifs**

* Problème avec l’analyse de la chaîne d’entrée preOptInApprovals de l’extension Launch ECID.
* Baisse des performances lors de l’utilisation de trackingServer.

## Version 4.4 {#version-4point4}

**Nouvelle fonctionnalité**

[Prise en charge du hachage SHA-256 pour setCustomerIDs](/help/reference/hashing-support.md). Le service Experience Cloud ID (ECID) prend en charge l’algorithme de hachage SHA-256 qui vous permet de transmettre des ID de client ou des adresses électroniques, et transmet des identifiants hachés.

**Correctifs, améliorations, avancées**

* Nous avons fait une mise à jour de la configuration de `cookieDomain`. La bibliothèque ECID filtre désormais la chaîne vide `cookieDomain` dans `initConfig` et utilise le domaine de cookie de niveau supérieur, qui est renvoyé par la méthode getDomain.
* Nous avons corrigé un bogue lié à `getVisitorValues` dans `localVisitor`.
* Nous avons corrigé un bogue en raison duquel la valeur MCOPTOUT était incohérente dans le navigateur Safari, renvoyée par la méthode `getVisitorValue`.
* Nous avons mis à jour la bibliothèque Opt-in par l’ajout de `optIn.off` pour se désabonner des événements.
* Nous avons corrigé un bogue lié à la fonction setTimeout, en raison duquel `setTimeout` violait la politique de sécurité du contenu (CSP) sur certains sites clients.

## Version 4.3 {#version-4point3}

**Prise en charge d’ITP 2.1**. Si un serveur de suivi est défini dans un CNAME propriétaire, un nouveau cookie (s_ecid) est placé avec la valeur ECID. La bibliothèque ECID référence la valeur pour conserver l’identifiant au-delà de sept jours. Reportez-vous à la section [Méthodes de bibliothèque ECID dans un univers ITP Safari](/help/reference/ecid-library-methods.md).

**Correction d’un bogue pour la configuration de secureCookie.**

## Version 4.1

Mise à jour de `publishDestinations` par nouveau changement d’API. Avec cette mise à jour, les informations du référent de la page peuvent être exposées pendant la synchronisation ID, si nécessaire.

## Version 4.2

Prise en charge du module externe Audience Manager pour IAB TCF, disponible via l’objet d’abonnement ECID.

**Correctifs**

* IAB + OptIn ne parvient pas à obtenir le MID pour les clients qui reviennent.
* Correction d’un bogue sur la configuration de l’inclusion doesOptInApply dans la gestion dynamique des balises.
* L’exclusion ECID désactive les synchronisations d’ID.

## Version 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Service Opt-in**. Opt-in est une extension de l’Experience Cloud ID (ECID) qui vous permet de contrôler la création de cookies par les bibliothèques Experience Cloud sur les pages web pour les visiteurs (ainsi que de décider quelles sont les bibliothèques concernées). Avec [Experience Platform Launch](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=fr), vous pouvez simplifier la collecte des consentements d’inclusion des visiteurs pour la solution Experience Cloud en autorisant Analytics, Target, Audience Manager et d’autres solutions Experience Cloud, ou une partie de celles-ci, à souscrire à votre système de gestion du consentement.

## Version 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Élément | Description |
|---|---|
| L’indicateur `disableIdSyncs` ne fonctionne pas après une certaine chaîne. | Corrigé. Les valeurs définies du `disableidSyncs` paramètre pour la `getInstance` fonction sont désormais honorées. |
| Certains iFrames tiers ne disposent pas de l’ECID. | Correction de l’ECID sur Safari Mobile et des ECID dans divers iFrames qui ne fonctionnaient pas. |
