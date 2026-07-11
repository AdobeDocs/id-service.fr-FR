---
description: Définit un intervalle de délai d’expiration en millisecondes. Utilisé pour indiquer à d’autres solutions (par exemple, Analytics, Audience Manager, Target, etc.) la durée d’attente d’une réponse du service d’identification des visiteurs.
keywords: Service d’identification des visiteurs
title: loadTimeout
exl-id: 485264f4-ee24-4042-8be3-259e70462110
TQID: https://experienceleague.adobe.com/w0-c0ROMsYRLqlHQuBfSAdardHnMfaJ8oTLf1xwL9QQ
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 147
ht-degree: 56%

---

# loadTimeout{#loadtimeout}

Définit un intervalle de délai d’expiration en millisecondes. Utilisé pour indiquer à d’autres solutions (par exemple, Analytics, Audience Manager, Target, etc.) la durée d’attente d’une réponse du service d’identification des visiteurs.

**Syntaxe :** `loadTimeout: *`intervalle en millisecondes`*`

La valeur par défaut est de 30 000 millisecondes (30 secondes). Nous vous recommandons vivement de *ne pas* modifier la valeur par défaut.

>[!NOTE]
>
>Les appels au service d’identification des visiteurs sont asynchrones par rapport aux autres codes non Adobe de la page. Par conséquent, l’augmentation ou la réduction du délai d’expiration n’a aucune incidence sur la vitesse du rendu du contenu par la page. Toutefois, les longs intervalles de délai d’expiration peuvent affecter les temps de chargement des pages, lesquels sont mesurés par des outils de surveillance réseau courants. Le temps de rendu n’est quant à lui pas affecté.

**Exemple de code**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example sets the timeout to 10,000 milliseconds (10 seconds). 
   loadTimeout:10000 
});
```

