---
description: Cette configuration vous permet d’effacer les Experience Cloud ID (ECID) orphelins ou bloqués, en s’appuyant sur la version mise à jour du service d’ID.
keywords: Service d’identification
seo-description: Cette configuration vous permet d’effacer les Experience Cloud ID (ECID) orphelins ou bloqués, en s’appuyant sur la version mise à jour du service d’ID.
seo-title: resetBeforeVersion
title: resetBeforeVersion
uuid: b00d18b8-6720-42f9-9c83-bd306184cc0c
translation-type: ht
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# resetBeforeVersion{#resetbeforeversion}

Cette configuration vous permet d’effacer les Experience Cloud ID (ECID) orphelins ou bloqués, en s’appuyant sur la version mise à jour du service d’ID.

Le fait de fournir votre version du service d’ID comme valeur pour la variable `resetBeforeVersion` entraîne la suppression des ECID obsolètes de la liste des ID côté client.

Certaines conditions, comme les expirations de sessions, peuvent parfois entraîner la création d’un ID côté client sans que le service d’ID reçoive un ID côté serveur. Lorsque cela se produit, le service d’ID trace l’ID côté client orphelin, sans toutefois pouvoir le suivre sur plusieurs domaines. Celui-ci ne peut pas non plus être synchronisé correctement avec les autres solutions. Le comportement compare la version du cookie AMCV actuel avec la valeur de la variable `resetBeforeVersion`. Si le cookie n’existe pas ou que la version du cookie est inférieure (antérieure) à la dernière version de la variable `resetBeforeVersion`, alors le cookie AMCV est supprimé et le service d’ID demande un nouvel ECID.

Dans le cas de visiteurs avec des cookies Demdex tiers sur leur navigateur, l’ECID est vérifié pour voir s’il a bien été généré en utilisant l’UUID dans le cookie Demdex. Si cela est bien le cas, le nouvel ECID sera bien le même et le visiteur est considéré comme nouveau. S’il s’avérait que l’ECID effacé n’a pas été généré grâce à l’utilisation du cookie Demdex ou en l’absence de cookie Demdex, le visiteur reçoit alors un nouvel ECID et il est considéré comme nouveau.

**Syntaxe :**`resetBeforeVersion = "3.3"`

**Exemple de code**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Marketing Cloud organization ID here", { 
  
    //Same as s.trackingServer 
    trackingServer: "Insert tracking server here ", 
  
    //Same as s.trackingServerSecure 
    trackingServerSecure: "Insert secure tracking server here", 
  
    //For CNAME support only. Exclude these variables if you're not using CNAME 
    marketingCloudServer: "Insert tracking server here", 
    marketingCloudServerSecure: "Insert secure tracking server here", 
  
    //Changing the version 
    resetBeforeVersion: "3.3" 
});
```

