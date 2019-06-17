---
description: Un indicateur booléen optionnel qui désactive la synchronisation des identifiants.
keywords: Service d’identification
seo-description: Un indicateur booléen optionnel qui désactive la synchronisation des identifiants.
seo-title: disableIdSyncs
title: disableIdSyncs
uuid: 8 bea 1 de 8-53 c 8-4 a 15-bcf 5-f 0869763 a 32 e
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# disableIdSyncs{#disableidsyncs}

Un indicateur booléen optionnel qui désactive la synchronisation des identifiants.

>[!NOTE]
>
>Cette configuration a été `idSyncDisableSyncs` renommée `disableIdSyncs` dans la version v 3.0 du 18 janvier 2018.

**Syntax:** `disableIdSyncs: true|false` (default is `false`.)

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

