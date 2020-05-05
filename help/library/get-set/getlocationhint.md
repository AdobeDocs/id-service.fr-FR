---
description: Renvoie l’ID de zone géographique du service Experience Cloud Identity. Un identifiant de région (ou indicateur d’emplacement) est un identifiant numérique pour l’emplacement géographique d’un centre de données du service d’ID particulier. Vous avez besoin de l’identifiant de région pour effectuer des appels d’API côté serveur à Audience Manager.
keywords: ID Service
seo-description: Renvoie l’ID de zone géographique du service Experience Cloud Identity. Un identifiant de région (ou indicateur d’emplacement) est un identifiant numérique pour l’emplacement géographique d’un centre de données du service d’ID particulier. Vous avez besoin de l’identifiant de région pour effectuer des appels d’API côté serveur à Audience Manager.
seo-title: getLocationHint
title: getLocationHint
uuid: cdc312b7-d270-4a5c-a2bb-0fbb37f1e2f4
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# getLocationHint{#getlocationhint}

Renvoie l’ID de zone géographique du service Experience Cloud Identity. Un identifiant de région (ou indicateur d’emplacement) est un identifiant numérique pour l’emplacement géographique d’un centre de données du service d’ID particulier. Vous avez besoin de l’identifiant de région pour effectuer des appels d’API côté serveur à Audience Manager.

**Syntaxe :** ` var *`nom de variable`* = visitor.getLocationHint()`

For a list of region IDs and corresponding locations, see [DCS Region IDs, Locations, and Host Names](https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html).

**Exemple de code**

La fonction d’indicateur d’emplacement lit l’identifiant de région à partir du cookie AMCV. Si l’identifiant de région est déjà défini dans le cookie AMCV, le rappel se produit immédiatement. Si l’identifiant de région n’est pas défini, la fonction attend une réponse du serveur avant de transmettre l’identifiant de région au rappel. Voici à quoi pourrait ressembler votre code.

```js
//callback function 
var callback = function ( 
<i>region ID here</i>){ 
//do whatever your function does with the region ID 
}; 
 
//Get the region ID 
visitor.getLocationHint(callback, true); 
```

