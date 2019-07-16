---
description: Un indicateur booléen optionnel qui contrôle la manière dont le service d'identité de Platform Platform charge l'iframe de synchronisation des identifiants.
keywords: Service d’identification
seo-description: Un indicateur booléen optionnel qui contrôle la manière dont le service d'identité de Platform Platform charge l'iframe de synchronisation des identifiants.
seo-title: idSyncAttachIframeOnWindowLoad
title: idSyncAttachIframeOnWindowLoad
uuid: aa2c2fa4-2cab-4e08-8d35-729a6c3e459a
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

Un indicateur booléen optionnel qui contrôle la manière dont le service d&#39;identité de Platform Platform charge l&#39;iframe de synchronisation des identifiants.

**Syntaxe :** ` `idSyncAttachIframeOnWindowLoad= true|false`` (la valeur par défaut est `false`).

Si `idSyncAttachIframeOnWindowLoad: true`, le service d’identification charge l’iFrame de synchronisation des identifiants au chargement de la fenêtre. Par défaut, le service d’ID charge l’iFrame de synchronisation des identifiants aussi rapidement que possible au lieu d’un chargement par fenêtre.

**Exemple de code**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example loads ID sync iFrame on window load instad of ASAP. 
   idSyncAttachIframeOnWindowLoad: true 
});
```

