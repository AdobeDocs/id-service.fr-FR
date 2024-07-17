---
description: Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service d’identités d’Experience Cloud.
keywords: Service d’ID
title: Notes de mise à jour de 2021
exl-id: 56bffb6f-a4fc-40df-8bb2-17e43772fe60
source-git-commit: 52956b38c59f60507aaf236b152ce41fc1229d14
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 100%

---

# Notes de mise à jour du service d’identités d’Experience Cloud – 2021

Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service d’identités d’Experience Cloud.

## Visitor 5.3.0

Les mises à jour suivantes ont été incluses dans la version 5.3.0 de Visitor :

* Mise à jour de l’algorithme pour générer l’ECID local.
* Dernier accord préalable avec les indicateurs `Secure` et `SameSite` pour le cookie de confidentialité.
* Correctif d’un problème de navigateur Firefox lorsqu’une page est chargée dans un iFrame enfant.

## Visitor 5.2.0

Les mises à jour suivantes ont été incluses dans la version 5.2.0 de Visitor :

* Cette version introduit un événement `onReceiveEcid`, qui est appelé lorsqu’un ECID en provenance du service d’identités est reçu. Par exemple :

```js
visitorInstance.onReceiveEcid(callback(ecid){
 console.log(ecid)
})
```
