---
description: Cette variable vous permet de remplacer l’intervalle de durée de vie par défaut par le cookie AMCV.
keywords: Service d’ID
title: cookieLifetime
exl-id: bdbabdcd-a87b-412c-8c2f-3f39820f939a
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '50'
ht-degree: 100%

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
