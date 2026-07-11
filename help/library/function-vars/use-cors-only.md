---
description: Indicateur booléen facultatif qui contrôle la manière dont le navigateur demande des ressources au service d’identification des visiteurs.
keywords: Service d’identification des visiteurs
title: useCORSOnly
exl-id: 049a082a-8e6b-44cc-bd05-c12aaf3cbe4d
TQID: https://experienceleague.adobe.com/QMYUbL2y8X5gSUcLmYnKZnp5mfEu7-uiogOx3rx2dkY
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 147
ht-degree: 46%

---

# useCORSOnly{#usecorsonly}

Indicateur booléen facultatif qui contrôle la manière dont le navigateur demande des ressources au service d’identification des visiteurs.

**Syntaxe :** `useCORSOnly: true|false` (la valeur par défaut est `false`).

**Vue d’ensemble**

Lorsqu’il est défini sur `false`, le navigateur vérifie les ressources avec CORS ou JSONP. Cependant, le service d’identification des visiteurs tente toujours de demander des ressources avec CORS en premier. Il revient à JSONP sur les navigateurs plus anciens qui ne prennent pas en charge CORS. Si vous avez besoin de forcer le navigateur à utiliser seulement CORS, définissez `useCORSOnly:true` dans l’appel de la fonction `Visitor.getInstance`.

>[!IMPORTANT]
>
>`Set useCORSOnly: true` si vous avez des exigences de sécurité strictes. Vous ne devez activer ce mode que si vous êtes certain que tous vos visiteurs utilisent des navigateurs qui prennent en charge CORS. L’expérience client n’est pas affectée par les navigateurs ne prenant pas en charge CORS. Cependant, les navigateurs sans prise en charge CORS ne peuvent pas demander de ressources ni échanger de données avec Adobe CX Enterprise.

**Exemple de code**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   useCORSOnly: true 
});
```

