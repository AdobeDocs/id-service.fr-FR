---
description: Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service d’identification des visiteurs.
keywords: Service d’identification des visiteurs
title: Notes de mise à jour de 2021
exl-id: 56bffb6f-a4fc-40df-8bb2-17e43772fe60
TQID: https://experienceleague.adobe.com/AB8VuYn9X41P9REJ8C215GzBRtH66lb35i-q1PNbZfU
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 110
ht-degree: 59%

---

# Notes de mise à jour du service d’identification des visiteurs Adobe - 2021

Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service d’identification des visiteurs.

## Visitor 5.3.0

Les mises à jour suivantes ont été incluses dans la version 5.3.0 de Visitor :

* Mise à jour de l’algorithme pour générer l’ECID local.
* Dernier accord préalable avec les indicateurs `Secure` et `SameSite` pour le cookie de confidentialité.
* Correctif d’un problème de navigateur Firefox lorsqu’une page est chargée dans un iFrame enfant.

## Visitor 5.2.0

Les mises à jour suivantes ont été incluses dans la version 5.2.0 de Visitor :

* Cette version introduit un `onReceiveEcid` d’événement, qui est appelé lorsqu’un ECID en provenance du service d’identification des visiteurs est reçu. Par exemple :

```js
visitorInstance.onReceiveEcid(callback(ecid){
 console.log(ecid)
})
```

