---
description: Cette variable vous permet de remplacer l’intervalle de durée de vie par défaut par le cookie AMCV.
keywords: Service d’identification
seo-description: Cette variable vous permet de remplacer l’intervalle de durée de vie par défaut par le cookie AMCV.
seo-title: cookieLifetime
title: cookieLifetime
uuid: cd 945 db 3-429 a -4625-ac 3 f -69 ac 259377 a 3
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# cookieLifetime{#cookielifetime}

Cette variable vous permet de remplacer l’intervalle de durée de vie par défaut par le cookie AMCV.

Par défaut, [!DNL Experience Cloud] les cookies du service d&#39;ID expirent après 24 mois. Définissez l’intervalle en secondes.

**Syntaxe :**` cookieLifetime: *`durée de vie en secondes`*`

**Exemple de code**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example changes expiration period to 12-months. 
   cookieLifetime:31536000 
});
```

