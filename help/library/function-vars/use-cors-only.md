---
description: Un indicateur booléen optionnel qui contrôle la manière dont le navigateur demande des ressources à partir du service d'identité Experience Cloud.
keywords: Service d’identification
seo-description: Un indicateur booléen optionnel qui contrôle la manière dont le navigateur demande des ressources à partir du service d'identité Experience Cloud.
seo-title: useCORSOnly
title: useCORSOnly
uuid: 607dc035-dffc-4f4d-be51-08ef6c0a8fad
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# useCORSOnly{#usecorsonly}

Un indicateur booléen optionnel qui contrôle la manière dont le navigateur demande des ressources à partir du service d'identité Experience Cloud.

**Syntaxe :** `useCORSOnly: true|false` (la valeur par défaut est `false`).

**Aperçu**

Lorsqu’il est défini sur `false`, le navigateur vérifie les ressources avec CORS ou JSONP. Cependant, le service d’ID essaie toujours de d’abord demander des ressources avec CORS. Il revient à JSONP sur les navigateurs plus anciens qui ne prennent pas en charge CORS. Si vous avez besoin de forcer le navigateur à utiliser seulement CORS, définissez `useCORSOnly:true` dans l’appel de la fonction `Visitor.getInstance`.

>[!IMPORTANT]
>
>`Set useCORSOnly: true` si vous avez des exigences de sécurité strictes. Il est recommandé de n’activer ce mode que si vous pensez que tous vos visiteurs utilisent des navigateurs qui prennent en charge CORS. L’expérience utilisateur n’est pas impactée par les navigateurs qui ne prennent pas en charge CORS. Cependant, les navigateurs qui ne prennent pas en charge CORS ne peuvent pas demander de ressources ni échanger des données avec [!DNL Adobe Experience Cloud].

**Exemple de code**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   useCORSOnly: true 
});
```

