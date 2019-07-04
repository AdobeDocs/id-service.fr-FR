---
description: Renvoie l’ID de zone géographique du service Experience Cloud ID. Un ID de zone géographique (ou indicateur de location) est un identifiant numérique pour l’emplacement géographique d’un centre de données spécifique du service d’ID. Vous avez besoin de l’ID de zone géographique pour effectuer des appels d’API côté serveur à Audience Manager.
keywords: Service d’identification
seo-description: Renvoie l’ID de zone géographique du service Experience Cloud ID. Un ID de zone géographique (ou indicateur de location) est un identifiant numérique pour l’emplacement géographique d’un centre de données spécifique du service d’ID. Vous avez besoin de l’ID de zone géographique pour effectuer des appels d’API côté serveur à Audience Manager.
seo-title: getLocationHint
title: getLocationHint
uuid: cdc312b7-d270-4a5c-a2bb-0fbb37f1e2f4
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# getLocationHint{#getlocationhint}

Renvoie l’ID de zone géographique du service Experience Cloud ID. Un ID de zone géographique (ou indicateur de location) est un identifiant numérique pour l’emplacement géographique d’un centre de données spécifique du service d’ID. Vous avez besoin de l’ID de zone géographique pour effectuer des appels d’API côté serveur à Audience Manager.

**Syntaxe :** ` var *`nom de variable`* = visitor.getLocationHint()`

Pour obtenir la liste des ID de zone géographique et d’emplacements correspondants, voir [DCS Region IDs, Locations, and Host Names](https://marketing.adobe.com/resources/help/en_US/aam/dcs-regions.html).

**Exemple de code**

La fonction d’indicateur de location lit l’identifiant de région à partir du cookie AMCV. Si l’identifiant de région est déjà défini dans le cookie AMCV, le rappel a lieu immédiatement. Si l’identifiant de région n’est pas défini, la fonction attend une réponse du serveur avant de transmettre l’identifiant de région dans le rappel. Voici à quoi pourrait ressembler votre code.

```js
//callback function 
var callback = function ( 
<i>region ID here</i>){ 
//do whatever your function does with the region ID 
}; 
 
//Get the region ID 
visitor.getLocationHint(callback, true); 
```

