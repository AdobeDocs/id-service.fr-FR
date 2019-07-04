---
description: Un indicateur booléen optionnel qui désactive la synchronisation des identifiants.
keywords: Service d’identification
seo-description: Un indicateur booléen optionnel qui désactive la synchronisation des identifiants.
seo-title: disableIdSyncs
title: disableIdSyncs
uuid: 8bea1de8-53c8-4a15-bcf5-f0869763a32e
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

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

