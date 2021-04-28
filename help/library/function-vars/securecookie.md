---
description: Un indicateur booléen facultatif qui ajoute un attribut « sécurisé » au cookie AMCV.
keywords: Service d’ID
seo-description: Un indicateur booléen facultatif qui ajoute un attribut « sécurisé » au cookie AMCV.
seo-title: secureCookie
title: secureCookie
uuid: 995d19f6-9c9d-4493-9c9c-545b0b5696b0
exl-id: ba281b1c-1112-4ed6-b4fd-b8f87cabc575
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '105'
ht-degree: 100%

---

# secureCookie {#securecookie}

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
