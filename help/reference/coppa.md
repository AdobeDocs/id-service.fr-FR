---
description: La Loi sur la protection de la vie privée des enfants en ligne (COPPA) interdit la collecte en ligne de renseignements personnels d'enfants de moins de 13 ans sans le consentement vérifiable des parents. Les clients et clientes concernés par la loi COPPA peuvent ajouter une variable facultative à leur code de service d’identification des visiteurs qui les empêche de définir des cookies dans le domaine tiers d’un navigateur.
keywords: Service d’identification des visiteurs
title: Prise en charge de la loi COPPA dans le service d’identification des visiteurs Adobe
exl-id: c7579f90-3011-4e26-b908-08907bf12ba2
TQID: https://experienceleague.adobe.com/szz7syrA2KSDasXTox02PTbxBy60tfFc80hHmsjXwc0
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 363
ht-degree: 36%

---

# Prise en charge de la loi COPPA dans le service d’identification des visiteurs Adobe {#coppa-support-in-the-experience-cloud-id-service}

La Loi sur la protection de la vie privée des enfants en ligne (COPPA) interdit la collecte en ligne de renseignements personnels d&#39;enfants de moins de 13 ans sans le consentement vérifiable des parents. Les clients et clientes concernés par la loi COPPA peuvent ajouter une variable facultative à leur code de service d’identification des visiteurs qui les empêche de définir des cookies dans le domaine tiers d’un navigateur.

>[!NOTE]
>
>Pour les versions 3.0.0 ou ultérieures.

**Cookies et suivi**

Lorsqu’une page web se charge, le service d’identification des visiteurs appelle un serveur de collecte de données (DCS) Adobe. La réponse du serveur de collecte de données comprend un cookie CX Enterprise et un cookie demdex.net.

* Le cookie CX Enterprise est défini dans le domaine propriétaire. Il ne peut pas être utilisé pour effectuer le suivi des visiteurs sur différents domaines, sauf si ces domaines fonctionnent ensemble pour autoriser l’accès.
* Le cookie demdex.net est défini dans le domaine tiers. Il contient un identifiant unique qui peut être utilisé pour effectuer le suivi des visiteurs sur différents domaines.

**Cookies et conformité à la loi COPPA**

Les cookies tiers qui effectuent le suivi des visiteurs dans différents domaines sur des sites Web destinés aux enfants déclenchent des exigences de consentement des parents COPPA. Pour respecter plus facilement la loi COPPA dans le cadre des analyses internes du site Web, ajoutez la variable `disableThirdPartyCookies:true` à la `Visitor.getInstance` fonction, comme illustré ci-après.

```js
//Call the Visitor ID Service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

Lorsqu’il est défini sur la valeur `true`, `disableThirdPartyCookies` l’objet empêche le serveur de collecte de données de renvoyer le cookie tiers demdex.net. Si un visiteur du site dispose déjà de ce cookie dans son navigateur, le service d’identification des visiteurs ne l’utilisera pas pour créer un ECID ou renvoyer un identifiant existant. Au lieu de cela, le service d’identification des visiteurs crée un identifiant aléatoire dans le cookie propriétaire. Une fois activé, vous pouvez collecter des données avec le service d’identification des visiteurs et les partager dans différentes solutions d’entreprise CX, y compris d’autres opérations internes autorisées par la COPPA.

>[!MORELIKETHIS]
>
>* [Centre de traitement des données personnelles Adobe](http://www.adobe.com/fr/privacy.html)
>* [Définition de la loi COPPA](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

