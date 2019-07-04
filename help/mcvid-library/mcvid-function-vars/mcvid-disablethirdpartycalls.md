---
description: Un indicateur booléen optionnel qui empêche le service d’ID de lancer des appels à d’autres domaines.
keywords: suivi inter-domaines ; service d’ID
seo-description: Un indicateur booléen optionnel qui empêche le service d’ID de lancer des appels à d’autres domaines.
seo-title: disableThirdPartyCalls
title: disableThirdPartyCalls
uuid: e92ce1f5-67a4-476c-9d04-41d4e96b1592
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# disableThirdPartyCalls{#disablethirdpartycalls}

Un indicateur booléen optionnel qui empêche le service d’ID de lancer des appels à d’autres domaines.

**Syntaxe :** ` `disableThirdPartyCalls: true|false`` (la valeur par défaut est `false`).

Lorsque `disableThirdPartyCalls: true`, le service d’identification ne lancera pas d’appel vers d’autres domaines.

**Rôle**

Cette variable est conçue pour les clients qui ont besoin d’effectuer les actions suivantes :

* Empêcher le service d’ID de lancer des appels à partir de leurs pages sécurisées et authentifiées.
* Faire en sorte que les visiteurs du site aient un Experience Cloud ID (MID).
* Faire en sorte que leurs autres solutions Experience Cloud fonctionnent correctement.

**Stratégie de mise en œuvre**

Comme d’autres solutions Experience Cloud reposent sur le MID, le service d’ID lance un appel à Adobe pour lui demander de renvoyer et de définir cet ID. Si vous avez besoin d’empêcher le service d’ID de lancer des appels à partir des sections authentifiées de votre site Web, laissez-le lancer ces appels requis à partir des pages qui ne nécessitent pas d’authentification préalable. Une fois que le visiteur de votre site possède un MID, vous pouvez définir `disableThirdPartyCalls= true` dans le code du service d’ID sur les sections authentifiées de votre site. Nous partons du principe que la plupart, voire tous vos clients, vont consulter une page d’authentification avant d’accéder aux parties sécurisées de votre site.

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

