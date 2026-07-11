---
description: Configuration dans ECID qui permet la prise en charge des cookies AMCV sur les pages Google AMP.
keywords: Service d’identification des visiteurs
title: Configurations Secure et SameSite
exl-id: c3bc44fc-5adc-4eae-8169-9d731d148458
TQID: https://experienceleague.adobe.com/qT9et54-InwTH7usPnjGN8mdBeMMrqK-qjxGOwqsXBA
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 151
ht-degree: 54%

---

# Configurations Secure et SameSite

Cette configuration vous permet de modifier les paramètres de vos cookies et de prendre en charge [les cookies AMCV](../../introduction/cookies.md) sur les pages Google AMP.

Le service d’identification des visiteurs Adobe définit les cookies ECID avec le paramètre par défaut du navigateur de `SameSite = Lax`, qui est inaccessible si la page est chargée dans un iframe comme une page Google AMP. Pour accéder aux cookies ECID, utilisez les configurations ci-dessous pour mettre à jour le paramètre SameSite sur `SameSite = None`.

>[!NOTE]
>
>Lors de lʼapplication du paramètre `SameSite = None`, les cookies doivent être définis sur `Secure`, afin que les données ne puissent être transmises que par des connexions HTTPS.

**Mise en œuvre** :

Si vous utilisez des balises, mettez à niveau votre extension de balise [!UICONTROL Experience Cloud ID Service] vers la version 5.1.0 et configurez `secureCookie: true` et `sameSiteCookie: none`.

Si vous n’utilisez pas de balises, mettez à jour vers la dernière bibliothèque Visitor 5.1.0 et suivez les configurations ci-dessous, lors de l’initialisation de l’instance Visiteur :

**Exemple de code**

```js
var visitor = Visitor.getInstance("IMSORG_ID", {

     secureCookie: true,

     sameSiteCookie: "None"

});
```

