---
description: Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service Experience Cloud Identity.
keywords: Service d’ID
title: Notes de mise à jour de 2021
source-git-commit: dce2c0036f697507381d0763c2f6a9538155681c
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 27%

---

# Notes de mise à jour d’Experience Cloud Identity Service - 2021

Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service Experience Cloud Identity.

## Visiteur 5.3.0

Les mises à jour suivantes ont été incluses dans la version 5.3.0 de Visitor :

* Mise à jour de l’algorithme pour générer l’ECID local.
* Dernier accord préalable avec `Secure` et `SameSite` indicateurs pour le cookie de confidentialité.
* Correctif d’un problème de navigateur Firefox lorsqu’une page est chargée dans un iFrame enfant.

## Visiteur 5.2.0

Les mises à jour suivantes ont été incluses dans la version 5.2.0 de Visitor :

* Cette version introduit un événement `onRecieveEcid`, qui est appelé lorsqu’un ECID est reçu d’Identity Service. Par exemple :

```js
visitorInstance.onRecieveEcid(callback(ecid){
 console.log(ecid)
})
```
