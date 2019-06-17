---
description: Un indicateur booléen facultatif qui empêche le service Experience Cloud ID de renvoyer le cookie tiers demdex.net.
keywords: Service d’identification
seo-description: Un indicateur booléen facultatif qui empêche le service Experience Cloud ID de renvoyer le cookie tiers demdex.net.
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7 ed 5 aa 16-44 ca -4702-878 a -1 a 208 ca 95270
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# disableThirdPartyCookies{#disablethirdpartycookies}

Un indicateur booléen facultatif qui empêche le service Experience Cloud ID de renvoyer le cookie tiers demdex.net.

>[!NOTE]
>
>Cette configuration a été `idSyncDisable3rdPartySyncing` renommée `disableThirdPartyCookies` dans la version v 3.0 du 18 janvier 2018.

**Syntax:** `disableThirdPartyCookies: true|false` (default is `false`.) Pour `VisitorAPI.js` la version 1.5.3 ou supérieure.

Lorsque `disableThirdPartyCookies: true`le service d&#39;ID ne renvoie pas le cookie tiers demdex. net (voir [Cookies et service](../../mcvid-introduction/mcvid-cookies.md) Experience Cloud ID). Si le navigateur d’un visiteur du site contient déjà ce cookie, le service d’ID ne l’utilise pas pour créer un Experience Cloud ID (MID) ou renvoyer un ID existant. Le service d’ID crée à la place un MID aléatoire dans le cookie propriétaire. Une fois qu’il est activé, vous pouvez collecter des données avec le service d’ID et les partager dans différentes solutions Experience Cloud.

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

