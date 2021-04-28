---
description: Un indicateur booléen facultatif qui empêche le service Experience Cloud Identity de renvoyer le cookie tiers demdex.net.
keywords: Service d’ID
seo-description: Un indicateur booléen facultatif qui empêche le service Experience Cloud Identity de renvoyer le cookie tiers demdex.net.
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7ed5aa16-44ca-4702-878a-1a208ca95270
exl-id: 19d12822-0e17-4a1c-8e9c-25a22e20a4a8
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '157'
ht-degree: 100%

---

# disableThirdPartyCookies {#disablethirdpartycookies}

Un indicateur booléen facultatif qui empêche le service Experience Cloud Identity de renvoyer le cookie tiers demdex.net.

>[!NOTE]
>
>Cette configuration était `idSyncDisable3rdPartySyncing` et a été renommée `disableThirdPartyCookies` dans la version 3.0 du 18 janvier 2018.

**Syntaxe :** `disableThirdPartyCookies: true|false` (la valeur par défaut est `false`). Pour `VisitorAPI.js` version 3.0.0 ou ultérieure.

Lorsque `disableThirdPartyCookies: true`, le service d’ID ne renvoie pas le cookie tiers demdex.net (voir [Cookies et service Experience Cloud Identity](../../introduction/cookies.md) ). Si le navigateur d’un visiteur du site contient déjà ce cookie, le service d’ID ne l’utilise pas pour créer un Experience Cloud ID (MID) ou renvoyer un ID existant. Le service d’ID crée à la place un MID aléatoire dans le cookie propriétaire. Une fois activé, vous pouvez collecter des données avec le service d’ID et les partager dans différentes solutions d’Experience Cloud.

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
