---
description: Configuration dans ECID qui peut être utilisée pour prendre en charge les cookies AMCV sur les pages AMP de Google.
keywords: Service d’identification
seo-description: Configuration dans ECID qui peut être utilisée pour prendre en charge les cookies AMCV sur les pages AMP de Google.
seo-title: Configurations Secure et SameSite
title: Configurations Secure et SameSite
translation-type: tm+mt
source-git-commit: 702d20f3989f7749fb173496765d94c3a5af46dc
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 2%

---


# Configurations Secure et SameSite

Cette configuration vous permet de modifier les paramètres de vos cookies et de prendre en charge [les cookies AMCV](../../introduction/cookies.md) sur les pages Google AMP.

Le service d’ID de visiteur d’Adobe définit les cookies ECID avec le paramètre par défaut du navigateur `SameSite = Lax`, qui est inaccessible si la page est chargée dans un iframe tel qu’une page Google AMP. Pour accéder aux cookies ECID, utilisez les configurations ci-dessous pour mettre à jour le paramètre Siteidentique sur `SameSite = None`.

>[!NOTE]
>
>Lors de l’application de `SameSite = None`, les cookies doivent être définis sur `Secure`, de sorte que les données ne puissent être transmises que par le biais de connexions HTTPS.

**Mise en œuvre**:

Si vous utilisez Adobe Experience Platform Launch, mettez à niveau votre extension d’ID d’Experience Cloud vers la version 5.1.0 et configurez `secureCookie: true` et `sameSiteCookie: none`.

Si vous n’utilisez pas Experience Platform Launch, mettez à jour la bibliothèque Visiteur 5.1.0 la plus récente et suivez les configurations ci-dessous, tout en initialisant l’instance de Visiteur :

**Exemple de code**

```js
var visitor = Visitor.getInstance("IMSORG_ID", {

     secureCookie: true,

     sameSiteCookie: "None"

});
```
