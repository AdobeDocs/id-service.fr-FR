---
description: Indique si le modèle de publication de destination doit utiliser Akamai pour les connexions HTTPS.
keywords: Service d’identification
seo-description: Indique si le modèle de publication de destination doit utiliser Akamai pour les connexions HTTPS.
seo-title: idSyncSSLUseAkamai
title: idSyncSSLUseAkamai
uuid: 501ccc37-c3ab-4454-bfcf-3e3c3e8b5ca3
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# idSyncSSLUseAkamai{#idsyncssluseakamai}

Indique si le modèle de publication de destination doit utiliser Akamai pour les connexions HTTPS.

La `idSyncSSLUseAkamai` configuration est activée selon le partenaire.

**Syntaxe: ** `idSyncSSLUseAkamai: true`

**Exemple de code**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
 
    //Set Akamai URL for ID sync container 
    idSyncSSLUseAkamai:true 
 
    ... 
});
```

