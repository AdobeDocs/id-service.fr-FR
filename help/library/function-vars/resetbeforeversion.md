---
description: Cette configuration vous permet d’effacer les ECID orphelins ou obsolètes en fonction de la version du service d’identification des visiteurs mise à jour.
keywords: Service d’identification des visiteurs
title: resetBeforeVersion
exl-id: 9fa40baa-433d-4f16-824b-521948a92a4b
TQID: https://experienceleague.adobe.com/5aqi7F5QkybjotjVMJgDWCchFw1XOYa6qPOSUzDyeqE
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 257
ht-degree: 41%

---

# resetBeforeVersion{#resetbeforeversion}

Cette configuration vous permet d’effacer les ECID orphelins ou obsolètes en fonction de la version du service d’identification des visiteurs mise à jour.

Fournir votre version du service d’identification des visiteurs comme valeur de la variable `resetBeforeVersion` entraîne l’effacement des ECID obsolètes des ID côté client.

Certaines conditions, telles que les délais d’expiration de session, peuvent parfois entraîner la génération d’un identifiant côté client sans que le service d’identification des visiteurs obtienne un identifiant côté serveur. Dans ce cas, un ID client orphelin est suivi par le service d’identification des visiteurs sans possibilité de suivi sur plusieurs domaines ou de synchronisation correcte avec d’autres solutions. Le comportement compare la version du cookie AMCV actuel avec la valeur de la variable `resetBeforeVersion`. Si le cookie n’existe pas ou si la version du cookie est inférieure (antérieure) à la dernière version publiée de `resetBeforeVersion`, le cookie AMCV est supprimé et le service d’identification des visiteurs demande un nouvel ECID.

Dans le cas de visiteurs avec des cookies Demdex tiers sur leur navigateur, l’ECID est vérifié pour voir s’il a bien été généré en utilisant l’UUID dans le cookie Demdex. Si cela est bien le cas, le nouvel ECID sera bien le même et le visiteur est considéré comme nouveau. Si, pour une raison quelconque, lʼECID effacé nʼa pas été généré à lʼaide du cookie Demdex ou sʼil nʼy a pas de cookie Demdex, le visiteur recevra un nouvel ECID et sera considéré comme nouveau.

**Syntaxe :** `resetBeforeVersion = "3.3"`

**Exemple de code**

```js
//Call the Visitor ID Service 
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE", { 
  
    //Same as s.trackingServer 
    trackingServer: "Insert tracking server here ", 
  
    //Same as s.trackingServerSecure 
    trackingServerSecure: "Insert secure tracking server here", 
  
    //For CNAME support only. Exclude these variables if you're not using CNAME 
    marketingCloudServer: "Insert tracking server here", 
    marketingCloudServerSecure: "Insert secure tracking server here", 
  
    //Changing the version 
    resetBeforeVersion: "3.3" 
});
```

