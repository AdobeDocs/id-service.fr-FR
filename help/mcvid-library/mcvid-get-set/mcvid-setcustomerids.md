---
description: setCustomerIDs définit une ou plusieurs paires clé-valeur qui définissent les ID de client et leur état d’authentification.
keywords: Service d’identification
seo-description: setCustomerIDs définit une ou plusieurs paires clé-valeur qui définissent les ID de client et leur état d’authentification.
seo-title: setCustomerIDs
title: setCustomerIDs
uuid: 4 f 960 f 98-cec 2-4 db 6-84 ea -0259 e 2128 ea 2
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# setCustomerIDs{#setcustomerids}

setCustomerIDs définit une ou plusieurs paires clé-valeur qui définissent les ID de client et leur état d’authentification.

**Syntaxe :**`visitor.setCustomerIDs()`

Vous pouvez définir un ou plusieurs ID comme l’illustre l’exemple de code ci-après. Voir [ID de client et états d’authentification](../../mcvid-reference/mcvid-authenticated-state.md) pour obtenir des informations supplémentaires et des exemples.

```js
// Single ID with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
//Multiple IDs with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "puuid":"550e8400-e29b-41d4-a716-446655440000" 
});
```

