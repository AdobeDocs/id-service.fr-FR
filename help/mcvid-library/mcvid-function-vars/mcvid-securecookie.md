---
description: Un indicateur booléen facultatif qui ajoute un attribut « sécurisé » au cookie AMCV.
keywords: Service d’identification
seo-description: Un indicateur booléen facultatif qui ajoute un attribut « sécurisé » au cookie AMCV.
seo-title: secureCookie
title: secureCookie
uuid: 995d19f6-9c9d-4493-9c9c-545b0b5696b0
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# secureCookie{#securecookie}

Un indicateur booléen facultatif qui ajoute un attribut « sécurisé » au cookie AMCV.

Cet attribut de configuration est disponible dans la `visitorAPI`version 3.3.0 de.

>[!NOTE]
>
>La `SecureCookie` configuration de ne fonctionne pas sur les domaines non sécurisés. Il se pourrait donc que vous ne receviez pas les valeurs MID pour les visites avec un protocole non sécurisé. La `secureCookie` configuration doit être définie sur `true` uniquement lorsque vous avez la certitude que l’ensemble des pages et des sous-domaines utilisent un protocole sécurisé.

**Syntaxe :** `secureCookie: true | false` (par défaut)

**Exemple de code**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE",{ 
 
        //Set secure cookie property 
        secureCookie: true 
 });
```

