---
description: Notes de mise à jour et mises à jour de 2015.
keywords: Service d’identification des visiteurs
title: Notes de mise à jour 2015
exl-id: 57c45726-f856-4af5-a30a-9a1bdcaa6411
TQID: https://experienceleague.adobe.com/WmeSY7aRbvnZJN0a-lNR-yYzWzF4dfJLPZqA--6lpYQ
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 457
ht-degree: 60%

---

# Notes de mise à jour 2015 {#release-notes}

Notes de mise à jour et mises à jour de 2015.

## Version 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

Novembre 2015

La loi COPPA (Children’s Online Privacy Protection Act) interdit la collecte en ligne d’informations personnelles sur les mineurs de moins de 13 ans sans le consentement vérifiable de l’un des parents. Les clients et clientes concernés par la loi COPPA peuvent ajouter une variable facultative à leur code de service d’identification des visiteurs qui les empêche de définir des cookies dans le domaine tiers d’un navigateur. Voir [&#x200B; Prise en charge de la loi COPPA dans le service d’identification des visiteurs](../reference/coppa.md#concept-d7ddf81bebd74f129661fcec1ca19413). Pour les versions 1.5.3 ou ultérieures.

## Version 1.5.2 {#section-e3c73e47539942a89b02d33061128148}

Septembre 2015

* Correction d’un bogue dans le navigateur Safari qui empêchait la synchronisation des services lorsque des utilisateurs bloquaient les cookies tiers. (AAM-20764)
* Les appels au service d’identification des visiteurs incluent désormais l’identifiant de version dans le paramètre `d_visid_ver=` . L’ID renvoyé est utile aux équipes internes pour le dépannage et les problèmes de prise en charge. (AAM-20824)

## Version 1.5.1 {#section-f4309d7917964a748fee4bdb45bffa44}

Août 2015

* Correction d’un bug pour empêcher le service d’identification des visiteurs de demander un iframe s’il n’existe aucune donnée à synchroniser ou à déclencher. (AAM-20164)
* Correction d’un bug qui empêchait le service d’identification des visiteurs de définir correctement un cookie de domaine de niveau supérieur en plusieurs parties. Par exemple, si vous disposez d’un domaine tel que `my_company.co.uk`, dans certaines circonstances, le service d’identification des visiteurs définit un cookie dans `co.uk` uniquement. (AN-104683)

  Cela n’a affecté que quelques clients qui remplissaient *tous* les critères suivants :

   * Utilisation du service d’identification des visiteurs.
   * L’activation d’une [&#x200B; période de grâce &#x200B;](https://experienceleague.adobe.com/fr/docs/analytics/implementation/id/migration) *ou* utilise des cookies propriétaires et les utilisateurs bloquent les cookies tiers.
   * possèdent des pages avec des domaines de niveau supérieur à parties multiples.

Les révisions de la documentation de cette mise à jour incluent :

* [Méthodes d’API et bibliothèque de code](../library/library.md#concept-ff27497375644a898d47984aefb21c97) : Réorganisation du contenu et du texte. Dans la plupart des cas, une page est dédiée à chaque méthode.
* [Conditions requises pour le service d’identification des visiteurs](../reference/requirements.md) : contenu révisé et texte réorganisé.

## Version 1.5 {#section-db5edfa11ae143ada07a96e0ab06dc57}

Juillet 2015

Le service d’identification des visiteurs prend en charge plusieurs identifiants et états d’authentification. Cette modification supprime également la prise en charge obsolète des mappages DPID Audience Manager aux ID utilisateur utilisés par la fonction `setCustomerIDs`. Voir [ID de client et états d’authentification](../reference/authenticated-state.md)

## Version 1.4 {#section-f5c596f355b14da28f45c798df513572}

Mai 2015

À compter de la version 1.4, la méthode préférée de configuration consiste à transférer un objet de configuration comme second paramètre à la fonction `Visitor.getInstance`.

```js
var visitor = Visitor.getInstance("016D5C175213CCA80A490D05@AdobeOrg",{ 
    "loadTimeout":1000, 
    "trackingServer":"myco.sc.omtrdc.net", 
    "idSyncContainerID":80 
});
```

## Version 1.3.5 {#section-eed4567f058f446d9a819e4682621aed}

Février 2015

Correction de la gestion des délais d’expiration des demandes pour les objets blob AAM et les conseils d’emplacement. Désormais, après temporisation, ces champs resteront correctement vierges pour les pages actives et tous les rappels seront appelés. Le délai d’expiration est traité comme une condition d’erreur. Par conséquent, l’opération réessaiera sur la page suivante. (AN-94473, AN-94474)

## Version 1.3.4 {#section-bca4a3e7c05546b7af1c9ec47fdb3331}

Janvier 2015

Reprise de la recherche des balises `<head>/<body>` pour le conteneur de balises `<script>` de la demande JSONP, ainsi que la création de la balise `<script>` afin de comptabiliser différentes mises en œuvre DOM (HTML/XHTML) avec éventuellement différents paramètres de respect de la casse. (AN-9355)

