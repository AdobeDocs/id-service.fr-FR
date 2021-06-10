---
description: Renvoie l’ID de zone géographique du service Experience Cloud Identity. Un ID de zone géographique (ou indicateur d’emplacement) est un identifiant numérique pour l’emplacement géographique d’un centre de données de service d’ID en particulier. Vous avez besoin de l’ID de zone géographique pour effectuer des appels d’API côté serveur vers Audience Manager.
keywords: Service d’ID
title: getLocationHint
exl-id: 0213f828-a985-4201-8a38-0a4b170ed057
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 100%

---

# getLocationHint{#getlocationhint}

Renvoie l’ID de zone géographique du service Experience Cloud Identity. Un ID de zone géographique (ou indicateur d’emplacement) est un identifiant numérique pour l’emplacement géographique d’un centre de données de service d’ID en particulier. Vous avez besoin de l’ID de zone géographique pour effectuer des appels d’API côté serveur vers Audience Manager.

**Syntaxe :** ` var *`nom de variable`* = visitor.getLocationHint()`

Pour obtenir la liste des ID de zone géographique et d’emplacements correspondants, voir [DCS Region IDs, Locations, and Host Names](https://docs.adobe.com/content/help/fr-FR/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html).

**Exemple de code**

La fonction d’indicateur d’emplacement lit l’ID de zone géographique à partir du cookie AMCV. Si l’identifiant de zone géographique est déjà défini dans le cookie AMCV, le rappel se produit immédiatement. Si l’identifiant de zone géographique n’est pas défini, la fonction attend une réponse du serveur avant de transmettre l’ID de zone géographique au rappel. Voici à quoi pourrait ressembler votre code.

```js
//callback function 
var callback = function ( 
<i>region ID here</i>){ 
//do whatever your function does with the region ID 
}; 
 
//Get the region ID 
visitor.getLocationHint(callback, true); 
```
