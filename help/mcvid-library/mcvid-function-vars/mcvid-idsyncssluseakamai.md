---
description: Indique si le modèle de publication de destination doit utiliser Akamai pour les connexions HTTPS.
keywords: Service d’identification
seo-description: Indique si le modèle de publication de destination doit utiliser Akamai pour les connexions HTTPS.
seo-title: idSyncSSLUseAkamai
title: idSyncSSLUseAkamai
uuid: 501 ccc 37-c 3 ab -4454-bfcf -3 e 3 c 3 e 8 b 5 ca 3
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# idSyncSSLUseAkamai{#idsyncssluseakamai}

Indique si le modèle de publication de destination doit utiliser Akamai pour les connexions HTTPS.

La configuration `idSyncSSLUseAkamai` est activée selon le partenaire.

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

