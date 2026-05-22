---
description: Cette configuration vous permet d’effacer les Experience Cloud ID (ECID) orphelins ou bloqués, en s’appuyant sur la version mise à jour du service d’ID.
keywords: Service d’ID
title: resetBeforeVersion
exl-id: 9fa40baa-433d-4f16-824b-521948a92a4b
TQID: https://experienceleague.adobe.com/5aqi7F5QkybjotjVMJgDWCchFw1XOYa6qPOSUzDyeqE
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 254
ht-degree: 87%

---

# resetBeforeVersion{#resetbeforeversion}

Cette configuration vous permet d’effacer les Experience Cloud ID (ECID) orphelins ou bloqués, en s’appuyant sur la version mise à jour du service d’ID.

Le fait de fournir votre version du service d’ID comme valeur pour la variable `resetBeforeVersion` entraîne la suppression des ECID obsolètes de la liste des ID côté client.

Certaines conditions, comme les expirations de sessions, peuvent parfois entraîner la création d’un ID côté client sans que le service d’ID reçoive un ID côté serveur. Lorsque cela se produit, le service d’ID trace l’ID côté client orphelin, sans toutefois pouvoir le suivre sur plusieurs domaines. Celui-ci ne peut pas non plus être synchronisé correctement avec les autres solutions. Le comportement compare la version du cookie AMCV actuel avec la valeur de la variable `resetBeforeVersion`. Si le cookie n’existe pas ou si la version du cookie est inférieure (antérieure) à la dernière version publiée de `resetBeforeVersion`, le cookie AMCV est supprimé et le service d’ID demande un nouvel ECID.

Dans le cas de visiteurs avec des cookies Demdex tiers sur leur navigateur, l’ECID est vérifié pour voir s’il a bien été généré en utilisant l’UUID dans le cookie Demdex. Si cela est bien le cas, le nouvel ECID sera bien le même et le visiteur est considéré comme nouveau. Si, pour une raison quelconque, lʼECID effacé nʼa pas été généré à lʼaide du cookie Demdex ou sʼil nʼy a pas de cookie Demdex, le visiteur recevra un nouvel ECID et sera considéré comme nouveau.

**Syntaxe :** `resetBeforeVersion = "3.3"`

**Exemple de code**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Marketing Cloud organization ID here", { 
  
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

