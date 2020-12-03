---
description: Un indicateur booléen optionnel qui désactive la synchronisation des identifiants.
keywords: ID Service
seo-description: Un indicateur booléen optionnel qui désactive la synchronisation des identifiants.
seo-title: disableIdSyncs
title: disableIdSyncs
uuid: 8bea1de8-53c8-4a15-bcf5-f0869763a32e
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '44'
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

