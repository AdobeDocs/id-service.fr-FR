---
description: Présentation des processus de synchronisation des identifiants et des taux de correspondance dans le service d'identité d'Experience Cloud, notamment Adobe Media Optimizer et le service d'ID.
keywords: Service d’identification
seo-description: Présentation des processus de synchronisation des identifiants et des taux de correspondance dans le service d'identité d'Experience Cloud, notamment Adobe Media Optimizer et le service d'ID.
seo-title: Comprendre la synchronisation des identifiants et les taux de correspondance
title: Comprendre la synchronisation des identifiants et les taux de correspondance
uuid: 31bd655f-2b9e-4f8d-9a1f-e81a6110eda8
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Comprendre la synchronisation des identifiants et les taux de correspondance{#understanding-id-synchronization-and-match-rates}

Présentation des processus de synchronisation des identifiants et des taux de correspondance dans le service d'identité d'Experience Cloud, notamment Adobe Media Optimizer et le service d'ID.

## Synchronisation des identifiants et taux de correspondance {#section-f652aae7234945e89d26dd833c5215fb}

La synchronisation des identifiants fait correspondre des identifiants attribués par le service d’ID à des ID attribués aux visiteurs du site par nos clients. Par exemple, imaginons que le service d’ID ait attribué un identifiant visiteur 1234. Une autre plate-forme connaît ce visiteur par son identifiant 4321. Le service d’ID cartographie ces identifiants et les relie lors du processus de synchronisation. Le résultat ajoute de nouveaux points de données à ce que notre client sait des visiteurs de son site. Par ailleurs, si le service d’ID ne peut pas faire correspondre un identifiant, il en crée un nouveau et l’utilise pour les futures synchronisations.

Les taux de correspondance mesurent et valident l’efficacité du processus de synchronisation des identifiants. Des taux de correspondance élevés suggèrent qu’un service particulier sera plus efficace et donnera accès à une plus large audience en ligne qu’un service avec des taux de correspondance faibles. La comparaison des taux de correspondance est une manière quantifiable d’évaluer les différentes plates-formes technologiques d’annonces intégrées.

![](assets/idsync2.png)

**Assurer des taux de correspondance élevés**

Pour générer des taux de correspondance élevés, il est important de bien configurer le service d’ID (voir le [guide de mise en œuvre standard](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445)). Une mise en œuvre adéquate permet d’obtenir des taux de correspondance élevés, parce que cela permet au service d’ID de définir le cookie dont il a besoin pour fonctionner et de synchroniser les identifiants avec les partenaires de données autorisés. Cependant, des facteurs tels qu’une faible connexion Internet, la collecte des données depuis des appareils mobiles ou les réseaux sans fil peuvent affecter l’efficacité de la collecte, synchronisation et mise en correspondance des identifiants du service d’ID. Ces variables côté client dépassent le champ d’action du service d’ID ou d’[!DNL Adobe].

## Description du processus de synchronisation des identifiants {#section-a541a85cbbc74f5682824b1a2ee2a657}

Le service d’ID synchronise les identifiants en temps réel. Ces processus fonctionnent dans le navigateur et non pas via un transfert de données de serveur à serveur. Le tableau suivant décrit les étapes du processus de synchronisation des identifiants.

**Étape 1 : Chargement de la page**

Lorsqu’un visiteur se rend sur votre site et charge une page, la fonction `Visitor.getInstance`lance un appel [CORS](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758) ou JSON-P au service d’ID. Le service d’ID répond avec un cookie qui inclut l’[!DNL Experience Cloud] ID (MID) du visiteur. Les MID est un identifiant unique attribué à chaque visiteur du site. Voir également [Cookies et service d'identité Experience Cloud](../introduction/cookies.md).

**Étape 2 : Chargement de l’iFrame**

Pendant que le corps de la page se charge, le service d’ID charge une iFrame appelée *`Destination Publishing iFrame`*. Le [!DNL Destination Publishing iFrame] se charge dans un domaine séparé de la page active. Cette conception aide à améliorer les performances de la page et la sécurité, parce que l’iFrame :

* Se charge de manière asynchrone par rapport à la page parente. Cela signifie que la page parente peut se charger indépendamment de [!DNL Destination Publishing iFrame]. Le chargement de l’iFrame et des pixels de synchronisation des identifiants au sein de l’iFrame n’affecte pas la page parente ni l’expérience utilisateur.
* Se charge aussi vite que possible. Si le rythme est trop rapide, vous pouvez charger l’iFrame après l’événement de chargement de la fenêtre (non recommandé). Voir [idSyncAttachIframeOnWindowLoad](../library/function-vars/idsyncattachiframeonwindowload.md#reference-b86b7112e0814a4c82c4e24c158508f4) pour plus de détails.
* Empêche le code de l’iFrame d’avoir accès à la page parente ou d’affecter cette dernière.

Voir également [Demande et définition d'identifiants par le service d'identité Experience Cloud](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a)

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

## Les services de synchronisation gèrent la synchronisation des identifiants {#section-cd5784d7ad404a24aa28ad4816a0119a}

Le terme *`Sync Services`* fait référence aux technologies internes [!DNL Experience Cloud] responsables de la synchronisation des identifiants. Ce service est activé par défaut. Pour le désactiver, ajoutez une [variable optionnelle](../library/function-vars/disableidsync.md#reference-589d6b489ac64eddb5a7ff758945e414) à la fonction du service d’ID `Visitor.getInstance`. Les services de synchronisation établissent des correspondances entre différents [!DNL Experience Cloud] ID, tels que :

* Les identifiants de [!DNL Experience Cloud] cookie tiers et les [!DNL Experience Cloud] identifiants propriétaires.

* Les identifiants de [!DNL Experience Cloud] cookie propriétaires et les identifiants [!DNL Adobe Media Optimizer] (AMO).

* Les identifiants de cookie tiers [!DNL Experience Cloud] et les identifiants des fournisseurs de données et des plateformes de ciblage tiers. Cela comprend les services et plateformes tels que les fournisseurs de données, les plateformes de demande et/ou côté fournisseurs, les réseaux publicitaires, les échanges, etc.
* Les identifiants de [!DNL Experience Cloud] cookie propriétaires et les identifiants des partenaires opérant sur plusieurs appareils.

## Synchronisation des identifiants avec Adobe Media Optimizer {#section-642c885ea65d45ffb761f78838735016}

[!DNL Adobe Media Optimizer] est une exception au processus de synchronisation des identifiants basé sur l’iFrame. Comme [!DNL Media Optimizer] est un domaine de confiance, les synchronisations des identifiants ont lieu à partir de la page parente plutôt que dans [!DNL Destination Publishing iFrame]. Pendant la synchronisation, le service d’ID appelle [!DNL Media Optimizer] à l’adresse `cm.eversttech.net`, qui est un nom de domaine hérité utilisé par [!DNL Media Optimizer] avant son acquisition par Adobe. L’envoi de données à [!DNL Media Optimizer] permet d’améliorer les taux de correspondance et est automatique pour les clients du service d’ID utilisant la version 2.0 (ou ultérieure). Voir aussi [Cookies Media Optimizer](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_media_optimizer.html).

>[!MORE_LIKE_THIS]
>
>* [Signification des appels vers le domaine Demdex](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)

