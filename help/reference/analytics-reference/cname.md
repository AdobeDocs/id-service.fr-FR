---
description: valeur nulle
keywords: order of operations;ID Service
seo-description: valeur nulle
seo-title: CNAME de collecte de données et suivi inter-domaines
title: CNAME de collecte de données et suivi inter-domaines
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: 588c4b29ebd3cccea4f2ab032f69a4b6c6e97f2a

---


# Collecte de données et identité{#data-collection-and-identity}

Dans les analyses, vous pouvez utiliser trois méthodes pour identifier les visiteurs.

- Utilisation du service d’identification des [visiteurs](https://docs.adobe.com/content/help/en/id-service/using/home.md)
- Utilisation de l’identifiant visiteur Analytics [hérité](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/unique-visitors/visid-overview.md)
- Fournir leur propre identité

## Using the Visitor ID Service{#using-the-visitor-id-service}

Le service d’identification des visiteurs est la méthode recommandée pour identifier les visiteurs. Il est basé sur deux composants

- Identifiant propriétaire - Identifiant propriétaire pouvant être utilisé pour mesurer les visiteurs de votre propre site Web. Cet ID est stocké dans le premier ID de partie et stocké dans un cookie côté client et un cookie côté serveur (avec un CNAME).
- Identifiant tiers (facultatif) : identifiant tiers distinct stocké sur demdex.net qui peut être utilisé pour mesurer les visiteurs sur plusieurs domaines (exemple.com et exemple.net)

Analytics utilisera toujours l’identifiant propriétaire et si l’identifiant tiers est activé et présent, l’identifiant propriétaire de chaque site sera le même. Toutefois, si l’ID tiers est désactivé, soit par vos paramètres, soit parce que le navigateur bloque les cookies tiers, il n’est pas possible de lier le trafic sur les deux sites.

## Domaines Analytics hérités

Avant le lancement du service d’identification des visiteurs, il y a plusieurs années, de nombreux clients utilisaient les domaines d’analyse natifs pour définir les cookies d’ID. Il s’agit notamment `omtrdc.net``2o7.net` d’un domaine CNAME. `omtrdc.net`, `2o7.net` et dans certains cas, un domaine CNAME est utilisé pour stocker des cookies tiers. Les cookies ainsi définis ont toujours été limités à un seul client afin que les clients ne puissent pas combiner leurs données entre les entreprises. Les domaines tiers CNAMED, parfois appelés domaines tiers conviviaux, ne sont utilisés que lorsque les clients veulent suivre les utilisateurs sur les sites qu’ils possèdent (par exemple, exemple.com, example.co.jp). Cette méthode est en cours de désapprobation afin de permettre un service d’identification des visiteurs plus robuste et respectueux de la vie privée. Les clients doivent accéder au service d’identification des visiteurs avec un CNAME par domaine dès que possible.

## Fournissez votre propre identité

Si un client choisit, il peut complètement contourner le système d’identification d’Adobe et mettre en oeuvre le sien en fournissant un identifiant [visiteur](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/unique-visitors/visid-custom.md)personnalisé. Il y a quelques choses à savoir si vous choisissez cette voie.

- Vous devez mettre en oeuvre des contrôles de confidentialité appropriés et d’exclusion
- Cet identifiant s’applique uniquement à Analytics.
- Vous êtes responsable de la persistance de cet ID

## CNAMES DE Collecte de données

Adobe recommande toujours l’utilisation d’un CNAME conjointement avec le service d’identification des visiteurs. Cela permet à l’identifiant visiteur propriétaire de persister à l’aide de cookies HTTP, ce qui rend les cookies plus durables.

## Exclusions

Adobe propose aux API de partager des signaux d’exclusion avec nos systèmes afin que vous puissiez fournir aux utilisateurs des moyens d’exclure le suivi. Vous trouverez des instructions détaillées sur l’ [exclusion](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/data-collection/opt-out.md) et l’ [inclusion](https://docs.adobe.com/content/help/en/id-service/using/implementation-guides/opt-in-service/optin-overview.md)

## Activation de la prise en charge de la collecte de données propriétaires (CNAME) avec le service Experience Cloud Identity {#section-25d4feb686d944e3a877d7aad8dbdf9a}

La prise en charge du CNAME du serveur de collecte de données est [activée lors de la configuration d’un CNAME](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-first-party.md) et en définissant la `visitor.marketingCloudServerSecure` variable dans le service d’identité d’Experience Cloud et `s.trackingServerSecure` dans AppMeasurement.
