---
description: Indicateur booléen facultatif qui empêche le service d’identification des visiteurs de renvoyer le cookie tiers demdex.net.
keywords: Service d’identification des visiteurs
title: disableThirdPartyCookies
exl-id: 19d12822-0e17-4a1c-8e9c-25a22e20a4a8
TQID: https://experienceleague.adobe.com/vx9q-Q1X0fraWPUmaBlx-bBFX-gvnAox03mpENTizHw
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 144
ht-degree: 16%

---

# disableThirdPartyCookies{#disablethirdpartycookies}

Indicateur booléen facultatif qui empêche le service d’identification des visiteurs de renvoyer le cookie tiers demdex.net.

>[!NOTE]
>
>Cette configuration était `idSyncDisable3rdPartySyncing` et a été renommée `disableThirdPartyCookies` dans la version 3.0 du 18 janvier 2018.

**Syntaxe :** `disableThirdPartyCookies: true|false` (la valeur par défaut est `false`). Pour `VisitorAPI.js` v3.0.0 ou une version ultérieure.

Lorsqu’il est `disableThirdPartyCookies: true`, le service d’identification des visiteurs ne renvoie pas le cookie tiers demdex.net (voir [Cookies et service d’identification des visiteurs](../../introduction/cookies.md) ). Si un visiteur du site dispose déjà de ce cookie dans son navigateur, le service d’identification des visiteurs ne l’utilisera pas pour créer un ECID ou renvoyer un identifiant existant. Au lieu de cela, le service d’identification des visiteurs crée un MID aléatoire dans le cookie propriétaire. Une fois activé, vous pouvez collecter des données avec le service d’identification des visiteurs et les partager dans différentes solutions d’entreprise CX.

**Exemple de code**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCookies: true 
});
```

