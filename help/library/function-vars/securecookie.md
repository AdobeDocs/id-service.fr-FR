---
description: Un indicateur booléen facultatif qui ajoute un attribut « sécurisé » au cookie AMCV.
keywords: Service d’identification des visiteurs
title: secureCookie
exl-id: ba281b1c-1112-4ed6-b4fd-b8f87cabc575
TQID: https://experienceleague.adobe.com/UBhpXY4BvJiEDp6Adje--6ng-4W12RCWun2CpMFD3kU
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 94
ht-degree: 100%

---

# secureCookie{#securecookie}

Un indicateur booléen facultatif qui ajoute un attribut « sécurisé » au cookie AMCV.

Cet attribut de configuration est disponible dans la `visitorAPI` version 3.3.0 de.

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

