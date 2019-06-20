---
description: Comprend des exemples de configuration de serveur et les étapes de migration requises.
keywords: Service d’identification
seo-description: Comprend des exemples de configuration de serveur et les étapes de migration requises.
seo-title: Scénarios de migration du service Experience Cloud ID
title: Scénarios de migration du service Experience Cloud ID
uuid: 9 e 229045-6508-48 c 4-ae 39-9537 b 4941853
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Scénarios de migration du service Experience Cloud ID {#experience-cloud-id-service-migration-scenarios}

Comprend des exemples de configuration de serveur et les étapes de migration requises.

## Propriété Web unique {#section-6ccfea84628d46c99507cb124e7f5445}

* **Client** : Exemple Entreprise Inc.
* **Compatibilité Experience Cloud** : non
* **Propriétés Web** : exemple.com
* **Serveurs de collecte de données** : metrics.exemple.com, smetrics.exemple.com
* **Fichier JavaScript Analytics** : un seul fichier pour toutes les pages du site

Tout d’abord, ce client doit être pris en charge par Experience Cloud (voir les [conditions requises](../../reference/requirements.md)). Puisqu’il y a un seul fichier JavaScript, il n’est pas nécessaire de configurer une période de grâce pour ce client. Ce client devra aussi configurer la migration des visiteurs, puis migrer hors de son CNAME de collecte de données, car celui-ci n’est pas nécessaire.

## Plusieurs fichiers JavaScript, balises d’image codées de manière irréversible {#section-a665f6ee202940449198e4e7a5dcac54}

* **Client** : Autre Exemple Entreprise Inc.
* **Compatibilité Experience Cloud** : oui
* **Propriétés Web** : autreexemple.com
* **Serveurs de collecte de données** : autreexempleen.112.2o7.net
* **Fichier JavaScript Analytics** : plusieurs fichiers JavaScript (un fichier pour leur site principal, un autre fichier pour leur section de prise en charge préservée dans un CMS distinct)
* **Autres méthodes de collecte de données** : balises d’image codées de manière irréversible sur une section du site

Tout d’abord, ce client doit connaître son ID d’organisation Adobe Experience Cloud (voir les [conditions requises](../../reference/requirements.md)). Ensuite, puisqu’il utilise plusieurs fichiers JavaScript, il doit configurer une période de grâce pour la migration. This customer will also set up visitor migration and then migrate from `*.2o7.net` to `*.sc.omtrdc.net`.

Si ce client effectue la mise à jour vers le code JavaScript Analytics le plus récent en préparation au déploiement du service [!DNL Experience Cloud] ID, il doit également mettre à jour toutes les balises d’image codées de manière irréversible afin d’utiliser JavaScript à la place.

## Plusieurs propriétés Web, plusieurs fichiers JavaScript et un lecteur vidéo Flash {#section-34647995ff3740b999fdee22d885e515}

* **Client** : Un Bon Client LLC
* **Compatibilité Experience Cloud** : oui
* **Propriétés Web** : monsiteprincipal.com, monautresiteA.com, monautresiteB.com
* **Serveurs de collecte de données** : metrics.monsiteprincipal.com, smetrics.monsiteprincipal.com
* **Fichier JavaScript Analytics** : plusieurs fichiers JavaScript (un fichier pour chaque propriété Web)
* **Autres méthodes de collecte de données** : un lecteur vidéo Flash

Tout d’abord, ce client doit connaître son ID d’organisation Adobe Experience Cloud (voir les [conditions requises](../../reference/requirements.md)). Ensuite, puisqu’il utilise plusieurs fichiers JavaScript, il doit configurer une période de grâce pour la migration. Ce client effectue le suivi des visiteurs entre son domaine principal et ses sous-domaines, de sorte qu’il continuera à utiliser son CNAME de collecte de données avec le service d’identification des visiteurs.

Lorsque ce client effectue la mise à jour vers le code JavaScript Analytics le plus récent en préparation au déploiement du service [!DNL Experience Cloud] ID, il doit également mettre à jour son lecteur vidéo Flash vers la version la plus récente d’AppMeasurement pour Flash.
