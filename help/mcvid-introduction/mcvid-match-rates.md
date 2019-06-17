---
description: Une vue d’ensemble des processus de synchronisation des identifiants et des taux de correspondance dans le service Experience Cloud ID, y compris Adobe Media Optimizer et le service d’ID.
keywords: Service d’identification
seo-description: Une vue d’ensemble des processus de synchronisation des identifiants et des taux de correspondance dans le service Experience Cloud ID, y compris Adobe Media Optimizer et le service d’ID.
seo-title: Comprendre la synchronisation des identifiants et les taux de correspondance
title: Comprendre la synchronisation des identifiants et les taux de correspondance
uuid: 31 bd 655 f -2 b 9 e -4 f 8 d -9 a 1 f-e 81 a 6110 eda 8
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Comprendre la synchronisation des identifiants et les taux de correspondance{#understanding-id-synchronization-and-match-rates}

Une vue d’ensemble des processus de synchronisation des identifiants et des taux de correspondance dans le service Experience Cloud ID, y compris Adobe Media Optimizer et le service d’ID.

## Synchronisation des identifiants et taux de correspondance {#section-f652aae7234945e89d26dd833c5215fb}

La synchronisation des identifiants fait correspondre des identifiants attribués par le service d’ID à des ID attribués aux visiteurs du site par nos clients. Par exemple, imaginons que le service d’ID ait attribué un identifiant visiteur 1234. Une autre plate-forme connaît ce visiteur par son identifiant 4321. Le service d’ID cartographie ces identifiants et les relie lors du processus de synchronisation. Le résultat ajoute de nouveaux points de données à ce que notre client sait des visiteurs de son site. Par ailleurs, si le service d’ID ne peut pas faire correspondre un identifiant, il en crée un nouveau et l’utilise pour les futures synchronisations.

Les taux de correspondance mesurent et valident l’efficacité du processus de synchronisation des identifiants. Des taux de correspondance élevés suggèrent qu’un service particulier sera plus efficace et donnera accès à une plus large audience en ligne qu’un service avec des taux de correspondance faibles. La comparaison des taux de correspondance est une manière quantifiable d’évaluer les différentes plates-formes technologiques d’annonces intégrées.

![](assets/idsync2.png)

**Assurer des taux de correspondance élevés**

Pour générer des taux de correspondance élevés, il est important de configurer le service d&#39;ID correctement (voir le guide de mise en œuvre [standard](../mcvid-implementation-guides/mcvid-standard.md#concept-89cd0199a9634fc48644f2d61e3d2445)). Une mise en œuvre adéquate permet d’obtenir des taux de correspondance élevés, parce que cela permet au service d’ID de définir le cookie dont il a besoin pour fonctionner et de synchroniser les identifiants avec les partenaires de données autorisés. Cependant, des facteurs tels qu’une faible connexion Internet, la collecte des données depuis des appareils mobiles ou les réseaux sans fil peuvent affecter l’efficacité de la collecte, synchronisation et mise en correspondance des identifiants du service d’ID. Ces variables côté client dépassent le champ d’action du service d’ID ou d’[!DNL Adobe].

## Processus de synchronisation des identifiants décrit {#section-a541a85cbbc74f5682824b1a2ee2a657}

Le service d’ID synchronise les identifiants en temps réel. Ces processus fonctionnent dans le navigateur et non pas via un transfert de données de serveur à serveur. Le tableau suivant décrit les étapes du processus de synchronisation des identifiants.

**Étape 1 : Chargement de la page**

Lorsqu&#39;un visiteur se rend sur votre site et charge une page, `Visitor.getInstance` la fonction effectue un appel [CORS](../mcvid-reference/mcvid-cors.md#concept-6c280446990d46d88ba9da15d2dcc758) ou JSON-P au service d&#39;ID. Le service d’ID répond avec un cookie qui inclut l’[!DNL Experience Cloud] ID (MID) du visiteur. Les MID est un identifiant unique attribué à chaque visiteur du site. Voir également [Les cookies et le service Experience Cloud ID](../mcvid-introduction/mcvid-cookies.md).

**Étape 2 : Chargement de l’iFrame**

Pendant que le corps de la page se charge, le service d’ID charge une iFrame appelée *`Destination Publishing iFrame`*. [!DNL Destination Publishing iFrame] Les chargements dans un domaine sont séparés de la page parent. Cette conception aide à améliorer les performances de la page et la sécurité, parce que l’iFrame :

* Se charge de manière asynchrone par rapport à la page parente. Cela signifie que la page parente peut se charger indépendamment de [!DNL Destination Publishing iFrame]la valeur. Le chargement de l’iFrame et des pixels de synchronisation des identifiants au sein de l’iFrame n’affecte pas la page parente ni l’expérience utilisateur.
* Se charge aussi vite que possible. Si le rythme est trop rapide, vous pouvez charger l’iFrame après l’événement de chargement de la fenêtre (non recommandé). Voir [idSyncAttachIframeOnWindowLoad](../mcvid-library/mcvid-function-vars/mcvid-idsyncattachiframeonwindowload.md#reference-b86b7112e0814a4c82c4e24c158508f4) pour plus de détails.
* Empêche le code de l’iFrame d’avoir accès à la page parente ou d’affecter cette dernière.

Voir également [Requête et définition d’ID par le service Experience Cloud ID...](../mcvid-introduction/mcvid-id-request.md#concept-2caacebb1d244402816760e9b8bcef6a).

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

Ce terme *`Sync Services`* fait référence [!DNL Experience Cloud] aux technologies internes responsables de la synchronisation des identifiants. Ce service est activé par défaut. Pour le désactiver, ajoutez une [variable optionnelle](../mcvid-library/mcvid-function-vars/mcvid-disableidsync.md#reference-589d6b489ac64eddb5a7ff758945e414) à la fonction du service d’ID `Visitor.getInstance`. Les services de synchronisation correspondent à différents [!DNL Experience Cloud] ID tels que :

* Identifiants [!DNL Experience Cloud] de cookie tiers aux [!DNL Experience Cloud] identifiants propriétaires.

* Identifiants [!DNL Experience Cloud] des cookies de premier niveau ( [!DNL Adobe Media Optimizer] AMO).

* Les identifiants de cookie tiers [!DNL Experience Cloud] et les identifiants des fournisseurs de données et des plateformes de ciblage tiers. Cela comprend les services et plateformes tels que les fournisseurs de données, les plateformes de demande et/ou côté fournisseurs, les réseaux publicitaires, les échanges, etc.
* Identifiants [!DNL Experience Cloud] de cookies propriétaires aux identifiants de partenaire sur plusieurs périphériques.

## Synchronisation des identifiants avec Adobe Media Optimizer {#section-642c885ea65d45ffb761f78838735016}

[!DNL Adobe Media Optimizer] est une exception au processus de synchronisation des identifiants basé sur l&#39;iframe. Comme [!DNL Media Optimizer] il s&#39;agit d&#39;un domaine de confiance, les synchronisations d&#39;ID ont lieu à partir de la page parente plutôt que dans [!DNL Destination Publishing iFrame]la page. Lors de la synchronisation, le service d&#39;ID appelle [!DNL Media Optimizer] un `cm.eversttech.net`nom de domaine hérité utilisé avant [!DNL Media Optimizer] son acquisition par Adobe. L’envoi de données à [!DNL Media Optimizer] permet d’améliorer les taux de correspondance et est automatique pour les clients du service d’ID utilisant la version 2.0 (ou ultérieure). Voir aussi [Cookies Media Optimizer](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_media_optimizer.html).

>[!MORE_ LIKE_ THIS]
>
>* [Signification des appels vers le domaine Demdex](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)
