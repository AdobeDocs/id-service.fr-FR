---
description: Renvoie l’Analytics ID hérité (s’il existe) qui était stocké dans le cookie s_vi avant la mise en œuvre du service Experience Cloud Identity. Si un Analytics ID n’a pas été précédemment attribué à un visiteur, cette méthode renvoie une chaîne vide.
keywords: Service d’ID
title: getAnalyticsVisitorID
exl-id: 82973de4-4257-4aab-9268-4ab124a01ee2
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 91%

---

# getAnalyticsVisitorID{#getanalyticsvisitorid}

Renvoie l’Analytics ID hérité (s’il existe) qui était stocké dans le cookie s_vi avant la mise en œuvre du service Experience Cloud Identity. Si un Analytics ID n’a pas été précédemment attribué à un visiteur, cette méthode renvoie une chaîne vide.

**Syntaxe** `var analyticsID = visitor.getAnalyticsVisitorID()`

Cette fonction est généralement utilisée avec les solutions personnalisées qui impliquent la lecture de l’identifiant visiteur. Elle n’est pas utilisée par une mise en œuvre standard. `getAnalyticsVisitorID` fonctionne également avec des fonctions de rappel pour lire les [!DNL Analytics] identifiants et les placer dans votre système ou application.

**Exemple de code**

```js
//callback function 
var useAnalyticsVisitorID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get Analytics ID and pass it to the function 
var analyticsID = visitor.getAnalyticsVisitorID(useAnalyticsVisitorID)
```

>[!TIP]
>
>Si vous êtes un [!DNL Analytics] client, recherchez également [!DNL Analytics] l’identifiant et envoyez-le à votre fonction. Par exemple, vous souhaitez les deux identifiants lorsque vous transmettez l’identifiant visiteur dans un élément de formulaire masqué à une application côté serveur qui utilise l’API d’insertion de données. Dans ce cas, vous devez collecter et renvoyer les identifiants visiteur [!DNL Experience Cloud] et [!DNL Analytics]. Voir [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md).

**Le paramètre aid est une valeur héritée**

Le `aid` paramètre apparaît dans une chaîne de requête dans deux ensembles différents de conditions.

**Cas 1**

Le paramètre `aid` apparaît dans une chaîne de requête dans les cas suivants :

* Le service [!DNL Experience Cloud] ID est déployé correctement.
* Le visiteur d’un site possède un [!DNL Analytics] ID préexistant qui est stocké dans le [cookie s_vi](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html#section-5d50a078de444d12b7d927d68ff3b679).

**Cas 2**

Le `aid` paramètre apparaît dans une chaîne de requête lorsque votre organisation utilise une [période de grâce](../../reference/analytics-reference/grace-period.md) avant de mettre entièrement en œuvre le service d’ID. Si le visiteur de votre site est nouveau et que vous n’utilisez pas de période de grâce, le visiteur obtient le paramètre `mid` ( [!DNL Experience Cloud] ID).

>[!MORELIKETHIS]
>
>* [Cookies Analytics](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-privacy.html)

