---
description: Définit un intervalle d’expiration en millisecondes. Utilisé pour indiquer à d’autres solutions (par exemple, Analytics, Audience Manager, Target, etc.) la durée d’attente d’une réponse du service d’ID.
keywords: Service d’ID
title: loadTimeout
exl-id: 485264f4-ee24-4042-8be3-259e70462110
source-git-commit: 7ef084bc1add5a4ea8c7be738055b0c21e247eea
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 69%

---

# loadTimeout{#loadtimeout}

Définit un intervalle d’expiration en millisecondes. Utilisé pour indiquer à d’autres solutions (par exemple, Analytics, Audience Manager, Target, etc.) la durée d’attente d’une réponse du service d’ID.

**Syntaxe :** `loadTimeout: *`intervalle en millisecondes`*`

La valeur par défaut est de 30 000 millisecondes (30 secondes). Nous vous recommandons vivement de *ne pas* modifier la valeur par défaut.

>[!NOTE]
>
>Les appels au service d’ID sont asynchrones par rapport aux autres codes hors Adobe sur la page. Par conséquent, l’augmentation ou la réduction du délai d’attente n’a aucune incidence sur la vitesse du rendu du contenu par la page. Toutefois, les longs intervalles d’expiration peuvent affecter les temps de chargement des pages, lesquels sont mesurés par des outils de surveillance réseau courants. Le temps de rendu n’est quant à lui pas affecté.

**Exemple de code**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example sets the timeout to 10,000 milliseconds (10 seconds). 
   loadTimeout:10000 
});
```
