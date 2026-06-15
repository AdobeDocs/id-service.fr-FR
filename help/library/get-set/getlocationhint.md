---
description: Renvoie l’ID de zone géographique du service d’identités d’Experience Cloud. Un ID de zone géographique (ou indicateur d’emplacement) est un identifiant numérique pour l’emplacement géographique d’un centre de données de service d’ID en particulier. Vous avez besoin de l’ID de zone géographique pour effectuer des appels d’API côté serveur vers Audience Manager.
keywords: Service d’ID
title: getLocationHint
exl-id: 0213f828-a985-4201-8a38-0a4b170ed057
TQID: https://experienceleague.adobe.com/Q58a-bmHINs-3mhlUarH8Ipo85tNhjTjMDSlZLFcHsw
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 195
ht-degree: 100%

---

# getLocationHint{#getlocationhint}

Renvoie l’ID de zone géographique du service d’identités d’Experience Cloud. Un ID de zone géographique (ou indicateur d’emplacement) est un identifiant numérique pour l’emplacement géographique d’un centre de données de service d’ID en particulier. Vous avez besoin de l’ID de zone géographique pour effectuer des appels d’API côté serveur vers Audience Manager.

**Syntaxe :** `var *`nom de variable`* = visitor.getLocationHint()`

Pour obtenir la liste des ID de zone géographique et d’emplacements correspondants, voir [DCS Region IDs, Locations, and Host Names](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html?lang=fr).

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

