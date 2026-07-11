---
description: getMarketingCloudVisitorID renvoie l’ECID.
keywords: Service d’identification des visiteurs
title: getMarketingCloudVisitorID
exl-id: bd81cc0b-0511-492d-beb8-8ba2fe5d4323
TQID: https://experienceleague.adobe.com/Ltpdq4dlGbJ8h0vAZBD52Pq7gLaurxSDYqETkLqQfDw
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 118
ht-degree: 52%

---

# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID renvoie l’ECID.

**Syntaxe :** `var *`nom de variable`* = visitor.getMarketingCloudVisitorID()`

Cette méthode est généralement utilisée par les solutions personnalisées qui impliquent la lecture de l’identifiant visiteur. Elle n’est pas utilisée par une mise en œuvre standard. `getMarketingCloudVisitorID` fonctionne également avec les fonctions de rappel pour lire les Analytics ID et les importer dans votre système ou application.

```js
//callback function 
var useMarketingCloudID = function(id){ 
     //whatever your function does with the ECID 
}; 
 
//get the ECID and pass it to the function 
var mcID = visitor.getMarketingCloudVisitorID(useMarketingCloudID)
```

>[!TIP]
>
>Si vous êtes un client Analytics, recherchez également et envoyez l’Analytics ID à votre fonction. Par exemple, vous souhaitez les deux identifiants lorsque vous transmettez l’identifiant visiteur dans un élément de formulaire masqué à une application côté serveur qui utilise l’API d’insertion de données. Dans ce cas, vous devez collecter et renvoyer les identifiants visiteur ECID et Analytics. Voir [Obtention de l’identifiant visiteur Analytics](../../library/get-set/getanalyticsvisitorid.md).

