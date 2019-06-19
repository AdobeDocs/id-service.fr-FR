---
description: Un indicateur booléen facultatif qui ajoute un attribut « sécurisé » au cookie AMCV.
keywords: Service d’identification
seo-description: Un indicateur booléen facultatif qui ajoute un attribut « sécurisé » au cookie AMCV.
seo-title: secureCookie
title: secureCookie
uuid: 995 d 19 f 6-9 c 9 d -4493-9 c 9 c -545 b 0 b 5696 b 0
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# secureCookie{#securecookie}

Un indicateur booléen facultatif qui ajoute un attribut « sécurisé » au cookie AMCV.

Cet attribut de configuration est disponible dans la version 3.3.0 de `visitorAPI`.

>[!NOTE]
>
>`SecureCookie` La configuration ne fonctionnera pas sur les domaines non sécurisés et risque de ne pas recevoir les valeurs MID pour les visites utilisant un protocole non sécurisé. La configuration `secureCookie` doit être définie sur `true` uniquement lorsque vous avez la certitude que l’ensemble des pages et des sous-domaines utilisent un protocole sécurisé.

**Syntaxe :**`secureCookie: true | false` (par défaut)

**Exemple de code**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE",{ 
 
        //Set secure cookie property 
        secureCookie: true 
 });
```

