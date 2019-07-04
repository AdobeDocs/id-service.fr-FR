---
description: Cette variable vous permet de remplacer l’intervalle de durée de vie par défaut par le cookie AMCV.
keywords: Service d’identification
seo-description: Cette variable vous permet de remplacer l’intervalle de durée de vie par défaut par le cookie AMCV.
seo-title: cookieLifetime
title: cookieLifetime
uuid: cd945db3-429a-4625-ac3f-69ac259377a3
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# cookieLifetime{#cookielifetime}

Cette variable vous permet de remplacer l’intervalle de durée de vie par défaut par le cookie AMCV.

Par défaut, les cookies du service [!DNL Experience Cloud] ID expirent après 24 mois. Définissez l’intervalle en secondes.

**Syntaxe :** ` cookieLifetime: *`durée de vie en secondes`*`

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

