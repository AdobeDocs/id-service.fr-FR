---
description: getMarketingCloudVisitorID renvoie l’identifiant visiteur Experience Cloud.
keywords: Service d’identification
seo-description: getMarketingCloudVisitorID renvoie l’identifiant visiteur Experience Cloud.
seo-title: getMarketingCloudVisitorID
title: getMarketingCloudVisitorID
uuid: 93e16220-b5b3-4d81-9189-30031bc15129
translation-type: tm+mt
source-git-commit: 4a5fbc971dc950c65e5c8f92dffdfe5dde528b54
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 100%

---


# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID renvoie l’identifiant visiteur Experience Cloud.

**Syntaxe :** ` var *`nom de variable`* = visitor.getMarketingCloudVisitorID()`

Cette méthode est généralement utilisée par les solutions personnalisées qui impliquent la lecture de l’identifiant visiteur. Elle n’est pas utilisée par une mise en œuvre standard. `getMarketingCloudVisitorID` fonctionne également avec des fonctions de rappel pour lire les [!DNL Analytics] identifiants et les placer dans votre système ou application.

```js
//callback function 
var useMarketingCloudID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get the Experience Cloud ID and pass it to the function 
var mcID = visitor.getMarketingCloudVisitorID(useMarketingCloudID)
```

>[!TIP]
>
>Si vous êtes un [!DNL Analytics] client, recherchez également [!DNL Analytics] l’identifiant et envoyez-le à votre fonction. Par exemple, vous souhaitez les deux identifiants lorsque vous transmettez l’identifiant visiteur dans un élément de formulaire masqué à une application côté serveur qui utilise l’API d’insertion de données. Dans ce cas, vous devez collecter et renvoyer les identifiants visiteur [!DNL Experience Cloud] et [!DNL Analytics]. Voir [Obtention de l’identifiant visiteur Analytics](../../library/get-set/getanalyticsvisitorid.md).

