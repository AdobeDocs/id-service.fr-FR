---
description: Indicateur booléen optionnel qui empêche le service Experience Cloud Identity Service de renvoyer le cookie tiers demdex. net.
keywords: Service d’identification
seo-description: Indicateur booléen optionnel qui empêche le service Experience Cloud Identity Service de renvoyer le cookie tiers demdex. net.
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7ed5aa16-44ca-4702-878a-1a208ca95270
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# disableThirdPartyCookies{#disablethirdpartycookies}

Indicateur booléen optionnel qui empêche le service Experience Cloud Identity Service de renvoyer le cookie tiers demdex. net.

>[!NOTE]
>
>Cette configuration était `idSyncDisable3rdPartySyncing` et a été renommée `disableThirdPartyCookies` dans la version 3.0 du 18 janvier 2018.

**Syntaxe :** `disableThirdPartyCookies: true|false` (la valeur par défaut est `false`). Pour `VisitorAPI.js` 1.5.3 ou version ultérieure.

When `disableThirdPartyCookies: true`, the ID service does not return the third-party, demdex.net cookie (see [Cookies and the Experience Cloud Identity Service](../../introduction/cookies.md) ). Si le navigateur d’un visiteur du site contient déjà ce cookie, le service d’ID ne l’utilise pas pour créer un Experience Cloud ID (MID) ou renvoyer un ID existant. Le service d’ID crée à la place un MID aléatoire dans le cookie propriétaire. Une fois qu’il est activé, vous pouvez collecter des données avec le service d’ID et les partager dans différentes solutions Experience Cloud.

**Exemple de code**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCookies: true 
});
```

