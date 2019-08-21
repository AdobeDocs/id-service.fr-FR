---
description: Requise pour les domaines de niveau supérieur à parties multiples où chacune des deux dernières parties de l’URL comporte plus de deux caractères.
keywords: Service d’identification
seo-description: Requise pour les domaines de niveau supérieur à parties multiples où chacune des deux dernières parties de l’URL comporte plus de deux caractères.
seo-title: cookieDomain
title: cookieDomain
uuid: a57e5477-c07b-4d54-8aea-8e8b152f1423
translation-type: ht
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# cookieDomain{#cookiedomain}

Requise pour les domaines de niveau supérieur à parties multiples où chacune des deux dernières parties de l’URL comporte plus de deux caractères.

**Syntaxe :** ` cookieDomain: " *`URL`*"` (le préfixe `www` n’est pas requis).

**Exemple d’utilisation**

* Obligatoire :`www.example.com.uk`
* Facultatif : `www.example.co.uk`

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

