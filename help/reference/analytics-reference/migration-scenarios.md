---
description: Comprend des exemples de configuration de serveur et les étapes de migration requises.
keywords: Service d’ID
title: Scénarios de migration du service Experience Cloud Identity
exl-id: 419532bf-399f-4646-a95f-31c35535d6fc
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '380'
ht-degree: 100%

---

# Scénarios de migration du service Experience Cloud Identity {#experience-cloud-id-service-migration-scenarios}

Comprend des exemples de configuration de serveur et les étapes de migration requises.

## Propriété web unique {#section-6ccfea84628d46c99507cb124e7f5445}

* **Client** : Exemple Entreprise Inc.
* **Activé pour Experience Cloud** : non
* **Propriétés web** : exemple.com
* **Serveurs de collecte de données** : mesures.exemple.com, smesures.exemple.com
* **Fichier JavaScript d’Analytics** : un seul fichier pour toutes les pages du site

Tout d’abord, ce client doit être pris en charge par Experience Cloud (voir les [conditions](../../reference/requirements.md)). De plus, puisqu’il dispose d’un fichier JavaScript unique, ce client n’a pas besoin d’une période de grâce. Il configure également la migration des visiteurs, puis migre hors de son CNAME de collecte de données, qui n’est pas nécessaire.

## Plusieurs fichiers JavaScript, balises d’image codées en dur {#section-a665f6ee202940449198e4e7a5dcac54}

* **Client** : Autre Exemple Entreprise Inc.
* **Activé pour Experience Cloud** : oui
* **Propriétés web** : autreexemple.com
* **Serveurs de collecte de données** : autreexempleco.112.2o7.net
* **Fichier JavaScript d’Analytics** : plusieurs fichiers JavaScript Un fichier pour leur site principal, un autre pour leur section d’assistance qui est conservé dans un CMS distinct.
* **Autres méthodes de collecte de données** : balises d’image codées en dur sur une section du site

Tout d’abord, ce client doit connaître son ID d’organisation Adobe Experience Cloud (voir les [conditions](../../reference/requirements.md)). Ensuite, puisqu’il utilise plusieurs fichiers JavaScript, il doit configurer une période de grâce pour la migration. Ce client devra aussi configurer la migration des visiteurs de `*.2o7.net` vers `*.sc.omtrdc.net`.

Si ce client effectue la mise à jour vers le code JavaScript Analytics le plus récent en préparation au déploiement du service [!DNL Experience Cloud] ID, il doit également mettre à jour toutes les balises d’image codées de manière irréversible afin d’utiliser JavaScript à la place.

## Plusieurs propriétés web, plusieurs fichiers JavaScript et un lecteur vidéo Flash {#section-34647995ff3740b999fdee22d885e515}

* **Client** : Un Bon Client LLC
* **Activé pour Experience Cloud** : oui
* **Propriétés web** : monsiteprincipal.com, monautresiteA.com, monautresiteB.com
* **Serveurs de collecte de données** : mesures.monsiteprincipal.com, smesures.monsiteprincipal.com
* **Fichier JavaScript d’Analytics** : plusieurs fichiers JavaScript Un fichier pour chaque propriété web.
* **Autres méthodes de collecte de données** : un lecteur vidéo Flash

Tout d’abord, ce client doit connaître son ID d’organisation Adobe Experience Cloud (voir les [conditions](../../reference/requirements.md)). Ensuite, puisqu’il utilise plusieurs fichiers JavaScript, il doit configurer une période de grâce pour la migration. Ce client effectue le suivi des visiteurs entre son domaine principal et ses sous-domaines. Il continue donc à utiliser son CNAME de collecte de données avec le service d’ID des visiteurs.

Lorsque ce client effectue la mise à jour vers le code JavaScript Analytics le plus récent en préparation au déploiement du service [!DNL Experience Cloud] ID, il doit également mettre à jour son lecteur vidéo Flash vers la version la plus récente d’AppMeasurement pour Flash.
