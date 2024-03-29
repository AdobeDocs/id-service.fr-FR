---
description: getMarketingCloudVisitorID renvoie l’identifiant visiteur Experience Cloud.
keywords: Service d’ID
title: getMarketingCloudVisitorID
exl-id: bd81cc0b-0511-492d-beb8-8ba2fe5d4323
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '117'
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
