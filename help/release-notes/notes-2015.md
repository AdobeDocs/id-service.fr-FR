---
description: Notes de mise à jour et mises à jour de 2015.
keywords: Service d’ID
title: Notes de mise à jour 2015
exl-id: 57c45726-f856-4af5-a30a-9a1bdcaa6411
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '408'
ht-degree: 100%

---

# Notes de mise à jour 2015 {#release-notes}

Notes de mise à jour et mises à jour de 2015.

## Version 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

Novembre 2015

La loi COPPA (Children’s Online Privacy Protection Act) interdit la collecte en ligne d’informations personnelles sur les mineurs de moins de 13 ans sans le consentement vérifiable de l’un des parents. Les clients qui le souhaitent peuvent ajouter une variable en option au code de leur service de [!DNL Experience Cloud] ID afin de l’empêcher de définir des cookies dans le domaine tiers d’un navigateur. Voir [Prise en charge de la loi COPPA dans le service Experience Cloud Identity](../reference/coppa.md#concept-d7ddf81bebd74f129661fcec1ca19413). Pour les versions 1.5.3 ou ultérieures.

## Version 1.5.2 {#section-e3c73e47539942a89b02d33061128148}

Septembre 2015

* Correction d’un bogue dans le navigateur Safari qui empêchait la synchronisation des services lorsque des utilisateurs bloquaient les cookies tiers. (AAM-20764)
* Les appels au service d’ID incluent désormais l’ID de version dans le paramètre `d_visid_ver=`. L’ID renvoyé est utile aux équipes internes pour le dépannage et les problèmes de prise en charge. (AAM-20824)

## Version 1.5.1 {#section-f4309d7917964a748fee4bdb45bffa44}

Août 2015

* Correction d’un bug pour empêcher le service d’ID de demander un iframe s’il n’y a aucune donnée à synchroniser ou à déclencher. (AAM-20164)
* Correction d’un bogue qui empêchait le service d’ID de définir correctement un cookie de domaine de niveau supérieur à parties multiples. Si, par exemple, vous avez un domaine du type `my_company.co.uk`, dans certains cas, le service d’ID définirait un cookie dans `co.uk` seulement. (AN-104683)

   Cela n’a affecté que quelques clients qui remplissaient *tous* les critères suivants :

   * Utilisation du service d’ID.
   * activation d’une [période de grâce ](../reference/analytics-reference/grace-period.md)*ou* utilisation de cookies propriétaires et de cookies tiers de blocage des utilisateurs ;

   * possèdent des pages avec des domaines de niveau supérieur à parties multiples.

Les révisions de la documentation de cette mise à jour incluent :

* [Méthodes d’API et bibliothèque de code](../library/library.md#concept-ff27497375644a898d47984aefb21c97) : Réorganisation du contenu et du texte. Dans la plupart des cas, une page est dédiée à chaque méthode.
* [Conditions requises du service Experience Cloud Identity](../reference/requirements.md) : Contenu révisé et texte réorganisé.

## Version 1.5 {#section-db5edfa11ae143ada07a96e0ab06dc57}

Juillet 2015

Le service [!DNL Experience Cloud] ID prend en charge plusieurs ID et états d’authentification. Cette modification arrête la prise en charge des mises en correspondance des [!DNL Audience Manager] DPID avec les ID utilisés par la `setCustomerIDs`fonction. Voir [ID de client et états d’authentification](../reference/authenticated-state.md)

## Version 1.4 {#section-f5c596f355b14da28f45c798df513572}

Mai 2015

À compter de la version 1.4, la méthode préférée de configuration consiste à transférer un objet de configuration comme second paramètre à la fonction `Visitor.getInstance`.

```js
var visitor = Visitor.getInstance("016D5C175213CCA80A490D05@AdobeOrg",{ 
    "loadTimeout":1000, 
    "trackingServer":"myco.sc.omtrdc.net", 
    "idSyncContainerID":80 
});
```

Voir [Experience Cloud](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd).

## Version 1.3.5 {#section-eed4567f058f446d9a819e4682621aed}

Février 2015

Correction de la gestion des délais d’attente des demandes pour les objets blob AAM et les conseils d’emplacement. Désormais, après temporisation, ces champs resteront correctement vierges pour les pages actives et tous les rappels seront appelés. Le délai d’expiration est traité comme une condition d’erreur. Par conséquent, l’opération réessaiera sur la page suivante. (AN-94473, AN-94474)

## Version 1.3.4 {#section-bca4a3e7c05546b7af1c9ec47fdb3331}

Janvier 2015

Reprise de la recherche des balises `<head>/<body>` pour le conteneur de balises `<script>` de la demande JSONP, ainsi que la création de la balise `<script>` afin de comptabiliser différentes mises en œuvre DOM (HTML/XHTML) avec éventuellement différents paramètres de respect de la casse. (AN-9355)
