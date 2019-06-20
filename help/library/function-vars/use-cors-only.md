---
description: Un indicateur booléen optionnel qui contrôle la manière dont le navigateur demande des ressources à partir du service Experience Cloud ID.
keywords: Service d’identification
seo-description: Un indicateur booléen optionnel qui contrôle la manière dont le navigateur demande des ressources à partir du service Experience Cloud ID.
seo-title: useCORSOnly
title: useCORSOnly
uuid: 607 dc 035-dffc -4 f 4 d-be 51-08 ef 6 c 0 a 8 fad
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# useCORSOnly{#usecorsonly}

Un indicateur booléen optionnel qui contrôle la manière dont le navigateur demande des ressources à partir du service Experience Cloud ID.

**Syntaxe :**`useCORSOnly: true|false` (par défaut)`false`

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

