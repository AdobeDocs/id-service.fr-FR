---
description: Comprend des exemples de configuration de serveur et les étapes de migration requises.
keywords: ID Service
seo-description: Comprend des exemples de configuration de serveur et les étapes de migration requises.
seo-title: Scénarios de migration du service Experience Cloud Identity
title: Scénarios de migration du service Experience Cloud Identity
uuid: 9e229045-6508-48c4-ae39-9537b4941853
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 62%

---


# Scénarios de migration du service Experience Cloud Identity {#experience-cloud-id-service-migration-scenarios}

Comprend des exemples de configuration de serveur et les étapes de migration requises.

## Propriété Web unique {#section-6ccfea84628d46c99507cb124e7f5445}

* **Client** : Exemple Entreprise Inc.
* **Experience Cloud activé**: Non
* **Propriétés** Web : example.com
* **Serveurs** de collecte de données : metrics.example.com, smetrics.example.com
* **Fichier** JavaScript Analytics : Un seul fichier pour toutes les pages du site

Tout d’abord, ce client doit être pris en charge par Experience Cloud (voir les [conditions](../../reference/requirements.md)). De plus, puisqu’ils disposent d’un seul fichier JavaScript, ce client n’a pas besoin d’une période de grâce. Ce client va également configurer la migration des visiteurs, puis migrer hors de son CNAME de collecte de données, ce qui n’est pas nécessaire.

## Plusieurs fichiers JavaScript, balises d’image codées de manière irréversible {#section-a665f6ee202940449198e4e7a5dcac54}

* **Client** : Autre Exemple Entreprise Inc.
* **Experience Cloud activé**: Oui
* **Propriétés** Web : anotherexample.com
* **Serveurs** de collecte de données : anotherexampleco.112.2o7.net
* **Fichier JavaScript Analytics** : plusieurs fichiers JavaScript Un fichier pour leur site principal, un autre fichier pour leur section d&#39;assistance qui est conservé dans un CMS distinct.
* **Autres méthodes** de collecte de données : Balises d’image codées en dur sur une section du site

Tout d’abord, ce client doit connaître son ID d’organisation Adobe Experience Cloud (voir les [conditions](../../reference/requirements.md)). Ensuite, puisqu’il utilise plusieurs fichiers JavaScript, il doit configurer une période de grâce pour la migration. Ce client devra aussi configurer la migration des visiteurs de `*.2o7.net` vers `*.sc.omtrdc.net`.

Si ce client effectue la mise à jour vers le code JavaScript Analytics le plus récent en préparation au déploiement du service [!DNL Experience Cloud] ID, il doit également mettre à jour toutes les balises d’image codées de manière irréversible afin d’utiliser JavaScript à la place.

## Plusieurs propriétés Web, plusieurs fichiers JavaScript et un lecteur vidéo Flash {#section-34647995ff3740b999fdee22d885e515}

* **Client** : Un Bon Client LLC
* **Experience Cloud activé**: Oui
* **Propriétés** Web : mymainsite.com, myothersiteA.com, myothersiteB.com
* **Serveurs** de collecte de données : metrics.monsiteprincipal.com, smetrics.monsiteprincipal.com
* **Fichier JavaScript Analytics** : plusieurs fichiers JavaScript Un fichier pour chaque propriété Web.
* **Autres méthodes de collecte de données** : un lecteur vidéo Flash

Tout d’abord, ce client doit connaître son ID d’organisation Adobe Experience Cloud (voir les [conditions](../../reference/requirements.md)). Ensuite, puisqu’il utilise plusieurs fichiers JavaScript, il doit configurer une période de grâce pour la migration. Ce client effectue le suivi des visiteurs entre son Principal domaine et ses sous-domaines, de sorte qu’il continuera à utiliser son CNAME de collecte de données avec le service d’identification des visiteurs.

Lorsque ce client effectue la mise à jour vers le code JavaScript Analytics le plus récent en préparation au déploiement du service [!DNL Experience Cloud] ID, il doit également mettre à jour son lecteur vidéo Flash vers la version la plus récente d’AppMeasurement pour Flash.
