---
description: Configuration dans ECID qui permet la prise en charge des cookies AMCV sur les pages Google AMP.
keywords: Service d’ID
title: Configurations Secure et SameSite
exl-id: c3bc44fc-5adc-4eae-8169-9d731d148458
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '154'
ht-degree: 100%

---

# Configurations Secure et SameSite

Cette configuration vous permet de modifier les paramètres de vos cookies et de prendre en charge [les cookies AMCV](../../introduction/cookies.md) sur les pages Google AMP.

Le service Adobe Visitor ID définit les cookies ECID selon le paramètre par défaut du navigateur `SameSite = Lax`, qui est inaccessible si la page est chargée dans une balise iframe telle quʼune page Google AMP. Pour accéder aux cookies ECID, utilisez les configurations ci-dessous pour mettre à jour le paramètre SameSite sur `SameSite = None`.

>[!NOTE]
>
>Lors de lʼapplication du paramètre `SameSite = None`, les cookies doivent être définis sur `Secure`, afin que les données ne puissent être transmises que par des connexions HTTPS.

**Mise en œuvre** :

Si vous utilisez Adobe Experience Platform Launch, mettez à niveau votre extension Experience Cloud ID vers la version 5.1.0 et configurez `secureCookie: true` et `sameSiteCookie: none`.

Si vous nʼutilisez pas Experience Platform Launch, mettez à jour la bibliothèque Visitor vers la dernière version (5.1.0) et suivez les configurations ci-dessous, tout en initialisant lʼinstance Visitor :

**Exemple de code**

```js
var visitor = Visitor.getInstance("IMSORG_ID", {

     secureCookie: true,

     sameSiteCookie: "None"

});
```
