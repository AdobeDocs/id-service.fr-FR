---
description: setCustomerIDs définit une ou plusieurs paires clé-valeur qui définissent les ID de client et leur état d’authentification.
keywords: Service d’ID
title: setCustomerIDs
exl-id: 8fc549d3-2a6f-4214-bb0d-3e0bc1501ce2
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '58'
ht-degree: 100%

---

# setCustomerIDs{#setcustomerids}

setCustomerIDs définit une ou plusieurs paires clé-valeur qui définissent les ID de client et leur état d’authentification.

**Syntaxe :** `visitor.setCustomerIDs()`

Vous pouvez définir un ou plusieurs ID comme l’illustre l’exemple de code ci-après. Voir [ID de client et états d’authentification](../../reference/authenticated-state.md) pour obtenir des informations supplémentaires et des exemples.

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
