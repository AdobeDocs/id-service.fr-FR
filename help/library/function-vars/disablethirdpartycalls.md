---
description: Un indicateur booléen optionnel qui empêche le service d’ID de lancer des appels à d’autres domaines.
keywords: cross domain tracking;ID Service
seo-description: Un indicateur booléen optionnel qui empêche le service d’ID de lancer des appels à d’autres domaines.
seo-title: disableThirdPartyCalls
title: disableThirdPartyCalls
uuid: e92ce1f5-67a4-476c-9d04-41d4e96b1592
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 58%

---


# disableThirdPartyCalls{#disablethirdpartycalls}

Un indicateur booléen optionnel qui empêche le service d’ID de lancer des appels à d’autres domaines.

**Syntaxe :** ` `disableThirdPartyCalls: true|false`` (la valeur par défaut est `false`).

Lorsque `disableThirdPartyCalls: true`, le service d’identification ne lancera pas d’appel vers d’autres domaines.

**Rôle**

Cette variable est conçue pour les clients qui ont besoin des éléments suivants :

* Pour empêcher le service d’ID d’effectuer des appels à partir de leurs pages sécurisées et authentifiées.
* Les visiteurs du site doivent posséder un ID d’Experience Cloud (MID).
* Leurs autres solutions Experience Cloud pour fonctionner correctement.

**Stratégie de mise en œuvre**

D’autres solutions Experience Cloud reposant sur le MID, le service d’ID appelle l’Adobe pour renvoyer et définir cet identifiant. Si vous avez besoin d’empêcher le service d’ID de lancer des appels à partir des sections authentifiées de votre site Web, laissez-le lancer ces appels requis à partir des pages qui ne nécessitent pas d’authentification préalable. Une fois que le visiteur de votre site possède un MID, vous pouvez définir `disableThirdPartyCalls= true` dans le code du service d’ID sur les sections authentifiées de votre site. L&#39;hypothèse ici est que la plupart, sinon la totalité, de vos clients accéderont à une page d&#39;authentification avant d&#39;accéder aux parties sécurisées de votre site.

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

