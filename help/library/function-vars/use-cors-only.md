---
description: Un indicateur booléen facultatif qui contrôle la manière dont le navigateur demande des ressources auprès du service Experience Cloud Identity.
keywords: Service d’ID
title: useCORSOnly
exl-id: 049a082a-8e6b-44cc-bd05-c12aaf3cbe4d
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 100%

---

# useCORSOnly{#usecorsonly}

Un indicateur booléen facultatif qui contrôle la manière dont le navigateur demande des ressources auprès du service Experience Cloud Identity.

**Syntaxe :** `useCORSOnly: true|false` (la valeur par défaut est `false`).

**Aperçu**

Lorsqu’il est défini sur `false`, le navigateur vérifie les ressources avec CORS ou JSONP. Cependant, le service d’ID essaie toujours de demander des ressources avec CORS en premier. Il revient à JSONP sur les navigateurs plus anciens qui ne prennent pas en charge CORS. Si vous avez besoin de forcer le navigateur à utiliser seulement CORS, définissez `useCORSOnly:true` dans l’appel de la fonction `Visitor.getInstance`.

>[!IMPORTANT]
>
>`Set useCORSOnly: true` si vous avez des exigences de sécurité strictes. Vous ne devez activer ce mode que si vous êtes certain que les visiteurs utilisent des navigateurs qui prennent en charge CORS. L’expérience client n’est pas affectée par les navigateurs ne prenant pas en charge CORS. Cependant, les navigateurs qui ne prennent pas en charge CORS ne peuvent pas demander de ressources ni échanger des données avec [!DNL Adobe Experience Cloud].

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
