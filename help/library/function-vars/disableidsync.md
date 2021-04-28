---
description: Un indicateur booléen optionnel qui désactive la synchronisation des identifiants.
keywords: Service d’ID
seo-description: Un indicateur booléen optionnel qui désactive la synchronisation des identifiants.
seo-title: disableIdSyncs
title: disableIdSyncs
uuid: 8bea1de8-53c8-4a15-bcf5-f0869763a32e
exl-id: 96d42133-6040-4da3-9315-fd94318b33aa
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '46'
ht-degree: 100%

---

# disableIdSyncs {#disableidsyncs}

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
