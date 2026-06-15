---
description: Un indicateur booléen optionnel qui désactive la synchronisation des identifiants.
keywords: Service d’ID
title: disableIdSyncs
exl-id: 96d42133-6040-4da3-9315-fd94318b33aa
TQID: https://experienceleague.adobe.com/ltW03vCXP9-8G7kJ8KwKOwAOgrsxkTxSoGzImR7dax0
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 39
ht-degree: 100%

---

# disableIdSyncs{#disableidsyncs}

Un indicateur booléen optionnel qui désactive la synchronisation des identifiants.

>[!NOTE]
>
>Cette configuration était `idSyncDisableSyncs` et a été renommée `disableIdSyncs` dans la version 3.0 du 18 janvier 2018.

**Syntaxe :** `disableIdSyncs: true|false` (la valeur par défaut est `false`).

**Exemple de code**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableIdSyncs: true 
});
```

