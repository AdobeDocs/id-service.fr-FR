---
description: Renvoie l’ID de zone géographique du service Experience Cloud Identity. Un ID de zone géographique (ou indicateur d’emplacement) est un identifiant numérique pour l’emplacement géographique d’un centre de données de service d’ID en particulier. Vous avez besoin de l’ID de zone géographique pour effectuer des appels d’API côté serveur vers Audience Manager.
keywords: Service d’identification
seo-description: Renvoie l’ID de zone géographique du service Experience Cloud Identity. Un ID de zone géographique (ou indicateur d’emplacement) est un identifiant numérique pour l’emplacement géographique d’un centre de données de service d’ID en particulier. Vous avez besoin de l’ID de zone géographique pour effectuer des appels d’API côté serveur vers Audience Manager.
seo-title: getLocationHint
title: getLocationHint
uuid: cdc312b7-d270-4a5c-a2bb-0fbb37f1e2f4
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 100%

---


# getLocationHint {#getlocationhint}

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

