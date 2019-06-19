---
description: Un indicateur booléen optionnel qui contrôle la manière dont le service d'identité de Platform Platform charge l'iframe de synchronisation des identifiants.
keywords: Service d’identification
seo-description: Un indicateur booléen optionnel qui contrôle la manière dont le service d'identité de Platform Platform charge l'iframe de synchronisation des identifiants.
seo-title: idSyncAttachIframeOnWindowLoad
title: idSyncAttachIframeOnWindowLoad
uuid: aa 2 c 2 fa 4-2 cab -4 e 08-8 d 35-729 a 6 c 3 e 459 a
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

Un indicateur booléen optionnel qui contrôle la manière dont le service d&#39;identité de Platform Platform charge l&#39;iframe de synchronisation des identifiants.

**Syntax:** ` `idSyncAttachIframeOnWindowLoad= true|false`` (default is `false`.)

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

