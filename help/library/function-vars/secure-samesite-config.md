---
description: Configuration dans ECID qui permet la prise en charge des cookies AMCV sur les pages Google AMP.
keywords: Service d’identification
seo-description: Configuration dans ECID qui permet la prise en charge des cookies AMCV sur les pages Google AMP.
seo-title: Configurations Secure et SameSite
title: Configurations Secure et SameSite
translation-type: ht
source-git-commit: 702d20f3989f7749fb173496765d94c3a5af46dc
workflow-type: ht
source-wordcount: '174'
ht-degree: 100%

---


# Configurations Secure et SameSite

Cette configuration vous permet de modifier les paramètres de vos cookies et de prendre en charge [les cookies AMCV](../../introduction/cookies.md) sur les pages Google AMP.

Le service Adobe Visitor ID définit les cookies ECID selon le paramètre par défaut du navigateur `SameSite = Lax`, qui est inaccessible si la page est chargée dans une balise iframe telle quʼune page Google AMP. Pour accéder aux cookies ECID, utilisez les configurations ci-dessous pour mettre à jour le paramètre SameSite sur `SameSite = None`.

>[!NOTE]
>
>Lors de lʼapplication du paramètre `SameSite = None`, les cookies doivent être définis sur `Secure`, afin que les données ne puissent être transmises que par des connexions HTTPS.

**Mise en œuvre** :

Si vous utilisez Adobe Experience Platform Launch, mettez à niveau votre extension Experience Cloud ID vers la version 5.1.0 et configurez `secureCookie: true` et `sameSiteCookie: none`.

Si vous nʼutilisez pas Experience Platform Launch, mettez à jour la bibliothèque Visitor vers la dernière version (5.1.0) et suivez les configurations ci-dessous, tout en initialisant lʼinstance Visitor :

**Exemple de code**

```js
var visitor = Visitor.getInstance("IMSORG_ID", {

     secureCookie: true,

     sameSiteCookie: "None"

});
```
