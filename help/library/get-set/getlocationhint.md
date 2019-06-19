---
description: Renvoie l'identifiant de région du service d'identité de Platform Platform. Un ID de zone géographique (ou indicateur de location) est un identifiant numérique pour l’emplacement géographique d’un centre de données spécifique du service d’ID. Vous avez besoin de l’ID de zone géographique pour effectuer des appels d’API côté serveur à Audience Manager.
keywords: Service d’identification
seo-description: Renvoie l'identifiant de région du service d'identité de Platform Platform. Un ID de zone géographique (ou indicateur de location) est un identifiant numérique pour l’emplacement géographique d’un centre de données spécifique du service d’ID. Vous avez besoin de l’ID de zone géographique pour effectuer des appels d’API côté serveur à Audience Manager.
seo-title: getLocationHint
title: getLocationHint
uuid: cdc 312 b 7-d 270-4 a 5 c-a 2 bb -0 fbb 37 f 1 e 2 f 4
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# getLocationHint{#getlocationhint}

Renvoie l&#39;identifiant de région du service d&#39;identité de Platform Platform. Un ID de zone géographique (ou indicateur de location) est un identifiant numérique pour l’emplacement géographique d’un centre de données spécifique du service d’ID. Vous avez besoin de l’ID de zone géographique pour effectuer des appels d’API côté serveur à Audience Manager.

**Syntaxe :**` var *`nom de variable`* = visitor.getLocationHint()`

Pour obtenir la liste des ID de zone géographique et des emplacements correspondants, voir [ID de zone géographique, emplacements et noms d’hôte du serveur de collecte de données](https://marketing.adobe.com/resources/help/en_US/aam/dcs-regions.html).

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

