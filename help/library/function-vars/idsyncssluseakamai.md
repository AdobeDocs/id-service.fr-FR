---
description: Indique si le modèle de publication de destination doit utiliser Akamai pour les connexions HTTPS.
keywords: Service d’ID
seo-description: Indique si le modèle de publication de destination doit utiliser Akamai pour les connexions HTTPS.
seo-title: idSyncSSLUseAkamai
title: idSyncSSLUseAkamai
uuid: 501ccc37-c3ab-4454-bfcf-3e3c3e8b5ca3
exl-id: 74c24eb5-bf3d-4e6b-ac7d-1a37d940d77f
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '52'
ht-degree: 100%

---

# idSyncSSLUseAkamai {#idsyncssluseakamai}

Indique si le modèle de publication de destination doit utiliser Akamai pour les connexions HTTPS.

La `idSyncSSLUseAkamai` configuration est activée selon le partenaire.

**Syntaxe :**`idSyncSSLUseAkamai: true`

**Exemple de code**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
 
    //Set Akamai URL for ID sync container 
    idSyncSSLUseAkamai:true 
 
    ... 
});
```
