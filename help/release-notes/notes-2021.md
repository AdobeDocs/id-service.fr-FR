---
description: Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service Experience Cloud Identity.
keywords: Service d’ID
title: Notes de mise à jour de 2021
exl-id: f0bbb100-49a9-4bba-8cee-5f40bec87984
source-git-commit: fcd3e8b65bb84e94eabac7ffec6a34f4cf75ec3d
workflow-type: ht
source-wordcount: '103'
ht-degree: 100%

---

# Notes de mise à jour d’Experience Cloud Identity Service - 2021

Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées à Experience Cloud Identity Service.

## Visitor 5.3.0

Les mises à jour suivantes ont été incluses dans la version 5.3.0 de Visitor :

* Mise à jour de l’algorithme pour générer l’ECID local.
* Dernier accord préalable avec les indicateurs `Secure` et `SameSite` pour le cookie de confidentialité.
* Correctif d’un problème de navigateur Firefox lorsqu’une page est chargée dans un iFrame enfant.

## Visitor 5.2.0

Les mises à jour suivantes ont été incluses dans la version 5.2.0 de Visitor :

* Cette version introduit un événement `onRecieveEcid`, qui est appelé lorsqu’un ECID en provenance d’Identity Service est reçu. Par exemple :

```js
visitorInstance.onRecieveEcid(callback(ecid){
 console.log(ecid)
})
```
