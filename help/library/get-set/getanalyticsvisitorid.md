---
description: Renvoie l'Analytics ID hérité (le cas échéant) stocké dans le cookie s_ vi avant la mise en œuvre du service Experience Cloud ID. Si un Analytics ID n’a pas été précédemment attribué à un visiteur, cette méthode renvoie une chaîne vide.
keywords: Service d’identification
seo-description: Renvoie l'Analytics ID hérité (le cas échéant) stocké dans le cookie s_ vi avant la mise en œuvre du service Experience Cloud ID. Si un Analytics ID n’a pas été précédemment attribué à un visiteur, cette méthode renvoie une chaîne vide.
seo-title: getAnalyticsVisitorID
title: getAnalyticsVisitorID
uuid: 6 bb 8 ddfc -9 fc 1-4105-b 377-d 9 b 4 d 247 a 0 f 8
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# getAnalyticsVisitorID{#getanalyticsvisitorid}

Renvoie l&#39;Analytics ID hérité (le cas échéant) stocké dans le cookie s_ vi avant la mise en œuvre du service Experience Cloud ID. Si un Analytics ID n’a pas été précédemment attribué à un visiteur, cette méthode renvoie une chaîne vide.

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
>If you&#39;re an [!DNL Analytics] customer, also check for and send the [!DNL Analytics] ID to your function. Par exemple, vous souhaitez les deux identifiants lorsque vous transmettez l’identifiant visiteur dans un élément de formulaire masqué à une application côté serveur qui utilise l’API d’insertion de données. In this case, you should collect and return the [!DNL Experience Cloud] and [!DNL Analytics] visitor IDs. See [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md).

**Le paramètre aid est une valeur héritée**

Le paramètre `aid` apparaît dans une chaîne de requête dans deux ensembles différents de conditions.

**Cas 1**

Le paramètre `aid` apparaît dans une chaîne de requête dans les cas suivants :

* The [!DNL Experience Cloud] ID service is deployed correctly.
* Le visiteur d’un site possède un [!DNL Analytics] ID préexistant qui est stocké dans le [cookie s_vi](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html).

**Cas 2**

You will see the `aid` parameter in a query string when your organization is using a [grace period](../../reference/analytics-reference/grace-period.md) before fully implementing the ID service. If the user visiting your site is new, and you&#39;re not using a grace period, the visitor will get the `mid` ( [!DNL Experience Cloud] ID) parameter.

>[!MORE_ LIKE_ THIS]
>
>* Cookies [Analytics](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_analytics.html)

