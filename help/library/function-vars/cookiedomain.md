---
description: Requise pour les domaines de niveau supérieur à parties multiples où chacune des deux dernières parties de l’URL comporte plus de deux caractères.
keywords: Service d’identification
seo-description: Requise pour les domaines de niveau supérieur à parties multiples où chacune des deux dernières parties de l’URL comporte plus de deux caractères.
seo-title: cookieDomain
title: cookieDomain
uuid: a 57 e 5477-c 07 b -4 d 54-8 aea -8 e 8 b 152 f 1423
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# cookieDomain{#cookiedomain}

Requise pour les domaines de niveau supérieur à parties multiples où chacune des deux dernières parties de l’URL comporte plus de deux caractères.

**Syntaxe :**` cookieDomain: " *`URL`*"` (le `www` préfixe n&#39;est pas requis.)

**Exemple d’utilisation**

* Obligatoire :`www.example.com.uk`
* Non requis : `www.example.co.uk`

**Exemple de code**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   cookieDomain:"example.com.uk" 
});
```

