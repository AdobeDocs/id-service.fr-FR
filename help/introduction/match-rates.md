---
description: Présentation des processus de synchronisation des identifiants et des taux de correspondance dans le service Experience Cloud ID, notamment Adobe Media Optimizer et le service d'ID.
keywords: Service d’identification
seo-description: Présentation des processus de synchronisation des identifiants et des taux de correspondance dans le service Experience Cloud ID, notamment Adobe Media Optimizer et le service d'ID.
seo-title: Comprendre la synchronisation des identifiants et les taux de correspondance
title: Comprendre la synchronisation des identifiants et les taux de correspondance
uuid: 31 bd 655 f -2 b 9 e -4 f 8 d -9 a 1 f-e 81 a 6110 eda 8
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Understanding ID synchronization and match rates{#understanding-id-synchronization-and-match-rates}

Présentation des processus de synchronisation des identifiants et des taux de correspondance dans le service Experience Cloud ID, notamment Adobe Media Optimizer et le service d&#39;ID.

## ID synchronization and match rates {#section-f652aae7234945e89d26dd833c5215fb}

La synchronisation des identifiants fait correspondre des identifiants attribués par le service d’ID à des ID attribués aux visiteurs du site par nos clients. Par exemple, imaginons que le service d’ID ait attribué un identifiant visiteur 1234. Une autre plate-forme connaît ce visiteur par son identifiant 4321. Le service d’ID cartographie ces identifiants et les relie lors du processus de synchronisation. Le résultat ajoute de nouveaux points de données à ce que notre client sait des visiteurs de son site. Par ailleurs, si le service d’ID ne peut pas faire correspondre un identifiant, il en crée un nouveau et l’utilise pour les futures synchronisations.

Les taux de correspondance mesurent et valident l’efficacité du processus de synchronisation des identifiants. Des taux de correspondance élevés suggèrent qu’un service particulier sera plus efficace et donnera accès à une plus large audience en ligne qu’un service avec des taux de correspondance faibles. La comparaison des taux de correspondance est une manière quantifiable d’évaluer les différentes plates-formes technologiques d’annonces intégrées.

![](assets/idsync2.png)

**Assurer des taux de correspondance élevés**

To generate high match rates, it is important to set up the ID service properly (see the [standard implementation guide](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445)). Une mise en œuvre adéquate permet d’obtenir des taux de correspondance élevés, parce que cela permet au service d’ID de définir le cookie dont il a besoin pour fonctionner et de synchroniser les identifiants avec les partenaires de données autorisés. Cependant, des facteurs tels qu’une faible connexion Internet, la collecte des données depuis des appareils mobiles ou les réseaux sans fil peuvent affecter l’efficacité de la collecte, synchronisation et mise en correspondance des identifiants du service d’ID. Ces variables côté client dépassent le champ d’action du service d’ID ou d’[!DNL Adobe].

## ID synchronization process described {#section-a541a85cbbc74f5682824b1a2ee2a657}

Le service d’ID synchronise les identifiants en temps réel. Ces processus fonctionnent dans le navigateur et non pas via un transfert de données de serveur à serveur. Le tableau suivant décrit les étapes du processus de synchronisation des identifiants.

**Étape 1 : Chargement de la page**

When a visitor comes to your site and loads a page, the `Visitor.getInstance` function makes a [CORS](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758) or JSON-P call to the ID service. Le service d’ID répond avec un cookie qui inclut l’[!DNL Experience Cloud] ID (MID) du visiteur. Les MID est un identifiant unique attribué à chaque visiteur du site. Voir également [Les cookies et le service Experience Cloud ID](../introduction/cookies.md).

**Étape 2 : Chargement de l’iFrame**

Pendant que le corps de la page se charge, le service d’ID charge une iFrame appelée *`Destination Publishing iFrame`*. [!DNL Destination Publishing iFrame] Les chargements dans un domaine sont séparés de la page parent. Cette conception aide à améliorer les performances de la page et la sécurité, parce que l’iFrame :

* Se charge de manière asynchrone par rapport à la page parente. This means the parent page can load independently from the [!DNL Destination Publishing iFrame]. Le chargement de l’iFrame et des pixels de synchronisation des identifiants au sein de l’iFrame n’affecte pas la page parente ni l’expérience utilisateur.
* Se charge aussi vite que possible. Si le rythme est trop rapide, vous pouvez charger l’iFrame après l’événement de chargement de la fenêtre (non recommandé). Voir [idSyncAttachIframeOnWindowLoad](../library/function-vars/idsyncattachiframeonwindowload.md#reference-b86b7112e0814a4c82c4e24c158508f4) pour plus de détails.
* Empêche le code de l’iFrame d’avoir accès à la page parente ou d’affecter cette dernière.

Voir également [Requête et définition d’ID par le service Experience Cloud ID...](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a).

**Étape 3 : Déclenchement des synchronisations d’identifiants**

La synchronisation des identifiants est une URL qui se déclenche dans l’iFrame de publication de destination. Comme l’exemple générique le montre, une URL de synchronisation des identifiants contient le point de terminaison de la synchronisation des identifiants d’un partenaire, ainsi qu’une URL de redirection, qui redirige vers [!DNL Adobe] avec leur identifiant.

```
http://abc.com?partner_id=abc&sync_id=123&redir=http://dpm.demdex.net/ibs:dpid=<
<varname>
  ADOBE_PARTNER_ID
</varname>>&dpuuid=<
<varname>
  PARTNER_UUID
</varname>>
```

Voir également [Synchronisation des identifiants pour les transferts de données entrants](https://marketing.adobe.com/resources/help/en_US/aam/c_id_sync_in.html).

**Étape 4 : Enregistrement des identifiants**

Les identifiants synchronisés sont enregistrés sur les [serveurs de données principaux et de périphérie](https://marketing.adobe.com/resources/help/en_US/aam/c_compedge.html).

## Sync services manages ID synchronization {#section-cd5784d7ad404a24aa28ad4816a0119a}

The term *`Sync Services`* refers to internal [!DNL Experience Cloud] technologies responsible for ID synchronization. Ce service est activé par défaut. Pour le désactiver, ajoutez une [variable optionnelle](../library/function-vars/disableidsync.md#reference-589d6b489ac64eddb5a7ff758945e414) à la fonction du service d’ID `Visitor.getInstance`. Sync Services matches different [!DNL Experience Cloud] IDs such as:

* Third-party [!DNL Experience Cloud] cookie IDs to first-party [!DNL Experience Cloud] IDs.

* First-party [!DNL Experience Cloud] cookie IDs to [!DNL Adobe Media Optimizer] (AMO) IDs.

* Les identifiants de cookie tiers [!DNL Experience Cloud] et les identifiants des fournisseurs de données et des plateformes de ciblage tiers. Cela comprend les services et plateformes tels que les fournisseurs de données, les plateformes de demande et/ou côté fournisseurs, les réseaux publicitaires, les échanges, etc.
* First-party [!DNL Experience Cloud] cookie IDs to cross-device partner IDs.

## ID synchronization with Adobe Media Optimizer {#section-642c885ea65d45ffb761f78838735016}

[!DNL Adobe Media Optimizer] est une exception au processus de synchronisation des identifiants basé sur l&#39;iframe. Because [!DNL Media Optimizer] is a trusted domain, ID syncs take place from the parent page rather than in the [!DNL Destination Publishing iFrame]. During synchronization, the ID service calls [!DNL Media Optimizer] at `cm.eversttech.net`, which is a legacy domain name used by [!DNL Media Optimizer] prior to its acquisition by Adobe. L’envoi de données à [!DNL Media Optimizer] permet d’améliorer les taux de correspondance et est automatique pour les clients du service d’ID utilisant la version 2.0 (ou ultérieure). Voir aussi [Cookies Media Optimizer](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_media_optimizer.html).

>[!MORE_ LIKE_ THIS]
>
>* [Signification des appels vers le domaine Demdex](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)

