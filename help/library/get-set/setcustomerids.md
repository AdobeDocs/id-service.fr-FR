---
description: setCustomerIDs définit une ou plusieurs paires clé-valeur qui définissent les ID de client et leur état d’authentification.
keywords: Service d’ID
seo-description: setCustomerIDs définit une ou plusieurs paires clé-valeur qui définissent les ID de client et leur état d’authentification.
seo-title: setCustomerIDs
title: setCustomerIDs
uuid: 4f960f98-cec2-4db6-84ea-0259e2128ea2
exl-id: 8fc549d3-2a6f-4214-bb0d-3e0bc1501ce2
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '73'
ht-degree: 100%

---

# setCustomerIDs {#setcustomerids}

setCustomerIDs définit une ou plusieurs paires clé-valeur qui définissent les ID de client et leur état d’authentification.

**Syntaxe :** `visitor.setCustomerIDs()`

Vous pouvez définir un ou plusieurs ID comme l’illustre l’exemple de code ci-après. Voir  [ID de client et états d’authentification](../../reference/authenticated-state.md) pour obtenir des informations supplémentaires et des exemples.

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
    "dpuuid":"550e8400-e29b-41d4-a716-446655440000" 
});
```
