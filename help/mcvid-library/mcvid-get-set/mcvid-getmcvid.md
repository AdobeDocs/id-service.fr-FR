---
description: getMarketingCloudVisitorID renvoie l’identifiant visiteur Experience Cloud.
keywords: Service d’identification
seo-description: getMarketingCloudVisitorID renvoie l’identifiant visiteur Experience Cloud.
seo-title: getMarketingCloudVisitorID
title: getMarketingCloudVisitorID
uuid: 93 e 16220-b 5 b 3-4 d 81-9189-30031 bc 15129
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID renvoie l’identifiant visiteur Experience Cloud.

**Syntaxe :**` var *`nom de variable`* = visitor.getMarketingCloudVisitorID()`

Cette méthode est généralement utilisée par les solutions personnalisées qui impliquent la lecture de l’identifiant visiteur. Elle n’est pas utilisée par une mise en œuvre standard. `getMarketingCloudVisitorID` fonctionne également avec des fonctions de rappel pour lire les identifiants [!DNL Analytics] et les placer dans votre système ou application.

```js
//callback function 
var useMarketingCloudID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get the Experience Cloud ID and pass it to the function 
var mcID = visitor.getMarketingCloudVisitorID(useMarketingClouidID)
```

>[!TIP]
>
>Si vous [!DNL Analytics] êtes client, vérifiez également l&#39;identifiant et envoyez [!DNL Analytics] -le à votre fonction. Par exemple, vous souhaitez les deux identifiants lorsque vous transmettez l’identifiant visiteur dans un élément de formulaire masqué à une application côté serveur qui utilise l’API d’insertion de données. Dans ce cas, vous devez collecter et renvoyer les identifiants [!DNL Experience Cloud] et [!DNL Analytics] les identifiants visiteur. Voir [Obtention d&#39;un identifiant visiteur Analytics](../../mcvid-library/mcvid-get-set/mcvid-getanalyticsvisitorid.md).

