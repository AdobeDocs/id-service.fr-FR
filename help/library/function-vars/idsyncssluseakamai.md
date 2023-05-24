---
description: Indique si le modèle de publication de destination doit utiliser Akamai pour les connexions HTTPS.
keywords: Service d’ID
title: idSyncSSLUseAkamai
exl-id: 74c24eb5-bf3d-4e6b-ac7d-1a37d940d77f
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '39'
ht-degree: 100%

---

# idSyncSSLUseAkamai{#idsyncssluseakamai}

Indique si le modèle de publication de destination doit utiliser Akamai pour les connexions HTTPS.

La `idSyncSSLUseAkamai` configuration est activée selon le partenaire.

**Syntaxe :** `idSyncSSLUseAkamai: true`

**Exemple de code**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
 
    //Set Akamai URL for ID sync container 
    idSyncSSLUseAkamai:true 
 
    ... 
});
```
