---
description: valeur nulle
keywords: order of operations;ID Service
seo-description: valeur nulle
seo-title: CNAME de collecte de données et suivi inter-domaines
title: CNAME de collecte de données et suivi inter-domaines
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: 989b5f537848a7506a96e2eac17409f8b0307217

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

Analytics utilisera l’identifiant propriétaire à moins que les identifiants tiers ne soient activés alors que nous utiliserons cet identifiant lorsque les navigateurs le permettent. L’ID tiers est un espace de noms par client afin qu’un client ne puisse pas combiner des données avec un autre client dans Analytics.

## Domaines Analytics hérités

Avant le lancement du service d’identification des visiteurs Adobe, de nombreux clients utilisaient les domaines d’analyse natifs pour définir les cookies d’ID. Il s’agit notamment `omtrdc.net``2o7.net` d’un domaine CNAME. `omtrdc.net`, `2o7.net`dans certains cas, un domaine CNAME a été utilisé pour stocker des cookies tiers. Les cookies ainsi définis étaient limités à un seul client afin que les clients ne puissent pas combiner leurs données avec celles d’autres clients. Les domaines tiers CNAMED, parfois appelés domaines tiers conviviaux, ont été utilisés lorsque les clients veulent suivre les utilisateurs sur les sites qu’ils possèdent (par exemple, exemple.com, example.co.jp). Cette méthode ou l’utilisation de CNAME pour la prise en charge de domaines tiers conviviaux est déconseillée afin de permettre un service d’identification des visiteurs plus robuste et respectueux de la vie privée. Les clients doivent accéder au service d’identification des visiteurs avec un CNAME par domaine dès que possible.

## Fournissez votre propre identité

Si un client choisit, il peut complètement contourner le système d’identification d’Adobe et mettre en oeuvre le sien en fournissant un identifiant [visiteur](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/unique-visitors/visid-custom.md)personnalisé. Il y a quelques choses à savoir si vous choisissez cette voie.

- Vous devez mettre en oeuvre des contrôles de confidentialité appropriés et d’exclusion
- Cet identifiant s’applique uniquement à Analytics.
- Vous êtes responsable de la persistance de cet ID

## CNAMES DE Collecte de données

Adobe recommande toujours l’utilisation d’un CNAME conjointement avec le service d’identification des visiteurs. Cela permet à l’identifiant visiteur propriétaire de persister à l’aide de cookies HTTP, ce qui rend les cookies plus durables.

## OPTOUT

Adobe fournit aux clients les API pour partager des signaux d’exclusion avec nos systèmes afin que les clients puissent à leur tour permettre aux utilisateurs de ne pas effectuer de suivi. Nous fournissons des instructions détaillées sur la manière dont le client peut mettre en oeuvre les contrôles appropriés pour prendre en charge le choix des utilisateurs ; soit l’API [d’](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/data-collection/opt-out.md) exclusion, soit les options permettant d’ [empêcher le déclenchement](https://docs.adobe.com/content/help/en/id-service/using/implementation-guides/opt-in-service/optin-overview.md) du cookie jusqu’à obtention du consentement

## Activation de la prise en charge de la collecte de données propriétaires (CNAME) avec le service Experience Cloud Identity {#section-25d4feb686d944e3a877d7aad8dbdf9a}

La prise en charge du CNAME du serveur de collecte de données est [activée lors de la configuration d’un CNAME](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-first-party.md) et en définissant la `visitor.marketingCloudServerSecure` variable dans le service d’identité d’Experience Cloud et `s.trackingServerSecure` dans AppMeasurement.
