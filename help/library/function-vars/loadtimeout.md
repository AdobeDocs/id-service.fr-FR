---
description: Définit un intervalle d’expiration en millisecondes. Utilisé pour indiquer à d’autres solutions (par exemple, Analytics, Audience Manager, Target, etc.) le délai d’expiration d’une réponse du service d’ID.
keywords: Service d’identification
seo-description: Définit un intervalle d’expiration en millisecondes. Utilisé pour indiquer à d’autres solutions (par exemple, Analytics, Audience Manager, Target, etc.) le délai d’expiration d’une réponse du service d’ID.
seo-title: loadTimeout
title: loadTimeout
uuid: f627e044-bd73-49a4-8a90-6d19aa566751
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# loadTimeout{#loadtimeout}

Définit un intervalle d’expiration en millisecondes. Utilisé pour indiquer à d’autres solutions (par exemple, Analytics, Audience Manager, Target, etc.) le délai d’expiration d’une réponse du service d’ID.

**Syntaxe :** ` loadTimeout: *`intervalle en millisecondes`*`

La valeur par défaut est de 30 000 millisecondes (30 secondes). Il est vivement recommandé *de ne pas* modifier la valeur par défaut.

>[!NOTE]
>
>Les appels au service d’ID sont asynchrones par rapport aux autres codes hors Adobe sur la page. Par conséquent, l’augmentation ou la réduction du délai d’attente n’a aucune incidence sur la vitesse du rendu du contenu par la page. Toutefois, de longs délais peuvent avoir un impact sur les délais de chargement de la page tels qu’ils sont mesurés par des outils de surveillance réseau courants, mais pas sur le délai du rendu.

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

