---
description: Un indicateur booléen optionnel qui empêche le service d’ID de lancer des appels à d’autres domaines.
keywords: suivi inter-domaines ; service d’ID
title: disableThirdPartyCalls
exl-id: 1d5b4e80-1b2d-4401-9057-449a6abf5db5
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 100%

---

# disableThirdPartyCalls{#disablethirdpartycalls}

Un indicateur booléen optionnel qui empêche le service d’ID de lancer des appels à d’autres domaines.

**Syntaxe :** ` `disableThirdPartyCalls: true|false`` (la valeur par défaut est `false`).

Lorsque `disableThirdPartyCalls: true`, le service d’ID ne lancera pas d’appel vers d’autres domaines.

**Rôle**

Cette variable est conçue pour les clients qui ont besoin des éléments suivants :

* Empêcher le service dʼidentification dʼeffectuer des appels à partir de leurs pages sécurisées et authentifiées.
* Les visiteurs du site doivent posséder un Experience Cloud ID (MID).
* Leurs autres solutions Experience Cloud doivent fonctionner correctement.

**Stratégie de mise en œuvre**

Étant donné que dʼautres solutions Experience Cloud dépendent du MID, le service dʼidentification appelle Adobe pour renvoyer et définir cet identifiant. Si vous avez besoin d’empêcher le service d’ID de lancer des appels à partir des sections authentifiées de votre site Web, laissez-le lancer ces appels requis à partir des pages qui ne nécessitent pas d’authentification préalable. Une fois que le visiteur de votre site possède un MID, vous pouvez définir `disableThirdPartyCalls= true` dans le code du service d’ID sur les sections authentifiées de votre site. En principe, la plupart, voire la totalité, de vos clients accédera à une page dʼauthentification avant dʼaccéder aux parties sécurisées de votre site.

**Exemple de code**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCalls: true 
}); 
```
