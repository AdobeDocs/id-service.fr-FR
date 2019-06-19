---
description: Renvoie l'Analytics ID hérité (le cas échéant) stocké dans le cookie s_ vi avant la mise en œuvre du service d'identité de Platform Platform. Si un Analytics ID n’a pas été précédemment attribué à un visiteur, cette méthode renvoie une chaîne vide.
keywords: Service d’identification
seo-description: Renvoie l'Analytics ID hérité (le cas échéant) stocké dans le cookie s_ vi avant la mise en œuvre du service d'identité de Platform Platform. Si un Analytics ID n’a pas été précédemment attribué à un visiteur, cette méthode renvoie une chaîne vide.
seo-title: getAnalyticsVisitorID
title: getAnalyticsVisitorID
uuid: 6 bb 8 ddfc -9 fc 1-4105-b 377-d 9 b 4 d 247 a 0 f 8
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# getAnalyticsVisitorID{#getanalyticsvisitorid}

Renvoie l&#39;Analytics ID hérité (le cas échéant) stocké dans le cookie s_ vi avant la mise en œuvre du service d&#39;identité de Platform Platform. Si un Analytics ID n’a pas été précédemment attribué à un visiteur, cette méthode renvoie une chaîne vide.

**Syntaxe** `var analyticsID = visitor.getAnalyticsVisitorID()`

Cette fonction est généralement utilisée avec les solutions personnalisées qui impliquent la lecture de l’identifiant visiteur. Elle n’est pas utilisée par une mise en œuvre standard. `getAnalyticsVisitorID` fonctionne également avec des fonctions de rappel pour lire les identifiants [!DNL Analytics] et les placer dans votre système ou application.

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
>Si vous [!DNL Analytics] êtes client, vérifiez également l&#39;identifiant et envoyez [!DNL Analytics] -le à votre fonction. Par exemple, vous souhaitez les deux identifiants lorsque vous transmettez l’identifiant visiteur dans un élément de formulaire masqué à une application côté serveur qui utilise l’API d’insertion de données. Dans ce cas, vous devez collecter et renvoyer les identifiants [!DNL Experience Cloud] et [!DNL Analytics] les identifiants visiteur. Voir [getmarketingcloudvisitorid](../../library/get-set/getmcvid.md).

**Le paramètre aid est une valeur héritée**

Le paramètre `aid` apparaît dans une chaîne de requête dans deux ensembles différents de conditions.

**Cas 1**

Le paramètre `aid` apparaît dans une chaîne de requête dans les cas suivants :

* Le service [!DNL Experience Cloud] d&#39;ID est déployé correctement.
* Le visiteur d’un site possède un [!DNL Analytics] ID préexistant qui est stocké dans le [cookie s_vi](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html).

**Cas 2**

Vous verrez le `aid` paramètre dans une chaîne de requête lorsque votre organisation utilise une période [de grâce](../../reference/analytics-reference/grace-period.md) avant de mettre entièrement en œuvre le service d&#39;ID. Si l&#39;utilisateur qui visite votre site est nouveau et que vous n&#39;utilisez pas de période de grâce, le visiteur obtient le paramètre `mid` ( [!DNL Experience Cloud] ID).

>[!MORE_ LIKE_ THIS]
>
>* Cookies [Analytics](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_analytics.html)

