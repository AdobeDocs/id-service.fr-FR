---
description: Indicateur booléen facultatif qui empêche le service d’identification des visiteurs d’effectuer des appels vers d’autres domaines.
keywords: suivi inter-domaines;Service d’identification des visiteurs
title: disableThirdPartyCalls
exl-id: 1d5b4e80-1b2d-4401-9057-449a6abf5db5
TQID: https://experienceleague.adobe.com/mv00QfToxSqeITADmY1LbihbtJNHf1zzQef9uKDu-dc
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 205
ht-degree: 24%

---

# disableThirdPartyCalls{#disablethirdpartycalls}

Indicateur booléen facultatif qui empêche le service d’identification des visiteurs d’effectuer des appels vers d’autres domaines.

**Syntaxe :** ` `disableThirdPartyCalls: true|false`` (la valeur par défaut est `false`).

Lorsqu’il est `disableThirdPartyCalls: true`, le service d’identification des visiteurs n’effectuera pas d’appels vers d’autres domaines.

**Rôle**

Cette variable est conçue pour les clients qui ont besoin des éléments suivants :

* Pour empêcher le service d’identification des visiteurs d’effectuer des appels à partir de leurs pages authentifiées et sécurisées
* Les visiteurs et visiteuses du site doivent disposer d’un ECID.
* Leurs autres solutions CX Enterprise fonctionnent correctement.

**Stratégie de mise en œuvre**

Comme d’autres solutions d’entreprise CX reposent sur le MID, le service d’identification des visiteurs appelle Adobe pour revenir et définir cet identifiant. Si vous devez empêcher le service d’identification des visiteurs d’effectuer des appels à partir de sections authentifiées de votre site web, laissez-le effectuer ces appels requis à partir de pages qui ne nécessitent pas d’authentification au préalable. Une fois que le visiteur de votre site dispose d’un MID, vous pouvez le `disableThirdPartyCalls= true` dans le code du service d’identification des visiteurs dans les sections authentifiées de votre site. En principe, la plupart, voire la totalité, de vos clients accédera à une page dʼauthentification avant dʼaccéder aux parties sécurisées de votre site.

**Exemple de code**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCalls: true 
}); 
```

