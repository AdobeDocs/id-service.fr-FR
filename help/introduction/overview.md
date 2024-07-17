---
description: Le rôle du service d’identités Experience Cloud Identity dans Adobe Experience Cloud.
title: Vue d’ensemble du service d’identités d’Experience Cloud
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
source-git-commit: f7c25f5ebd0690c56c081422949eb34f1f277ae1
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 100%

---

# Vue d’ensemble du service d’identités d’Experience Cloud

Le service dʼidentités d’Experience Cloud active la structure d’identification courante pour les services d’application Experience Cloud. Vous pouvez utiliser le service d’identités d’Experience Cloud pour définir l’[Experience Cloud ID (ECID)](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html?lang=fr).

L’ECID est un espace de noms d’identité partagé utilisé dans Adobe Experience Platform et les applications Experience Cloud pour effectuer le suivi du comportement des visiteurs et des visiteuses et s’assurer que chaque appareil dispose d’un identifiant unique qui peut persister sur plusieurs sessions.

>[!TIP]
>
>Le service dʼidentités d’Experience Cloud, le service dʼidentités d’Experience Platform et l’ECID sont trois entités **différentes**.

Le service dʼidentités d’Experience Cloud peut remplacer différents identifiants spécifiques à l’application et utiliser la fonctionnalité d’[identifiants de client et d’états d’authentification](/help/reference/authenticated-state.md) pour vous permettre de transmettre vos propres identifiants de client à Experience Cloud.

>[!NOTE]
>
>Le service dʼidentités d’Experience Cloud ne fonctionne qu’avec les services d’application Experience Cloud auxquels vous avez souscrit un abonnement et ne vous permet pas d’accéder à d’autres services d’application dans le cas contraire.

Le service d’identités d’Experience Cloud prend en charge les applications suivantes :

* [Adobe Analytics](https://business.adobe.com/fr/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/fr/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/fr/products/target/adobe-target.html)

Par ailleurs, le service d’ID est un composant à part entière de plusieurs fonctionnalités, améliorations et services actuels et futurs d’Experience Cloud. Actuellement, le service d’ID prend en charge [Analytics](http://www.adobe.com/fr/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/fr/marketing-cloud/data-management-platform.html) et [Target](http://www.adobe.com/fr/marketing-cloud/testing-targeting.html). Si vous n’avez pas mis en œuvre le service d’ID, c’est le moment idéal d’envisager une stratégie de migration.

## Résumé des fonctionnalités

En résumé, le service d’identités d’Experience Cloud :

* Identifie de manière unique un visiteur ou une visiteuse sur un appareil dans plusieurs applications.
* Définit un cookie propriétaire dans le domaine du client afin d’assurer le tracking sur le domaine en question. Consultez le document sur les [cookies et le service d’identités d’Experience Cloud](./cookies.md) pour plus d’informations.
* Reçoit les alias et les mappages d’ID des clients et partenaires d’Experience Cloud.
* Gère la synchronisation des identifiants dans Experience Cloud.
* Prend en charge la synchronisation des identifiants avec différents tiers dans l’écosystème de la technologie publicitaire.

## Conditions requises pour le service d’identités d’Experience Cloud

Votre solution et d’autres bibliothèques de code d’Adobe doivent répondre à [certaines conditions requises](/help/reference/requirements.md) avant de pouvoir utiliser le service d’identités.

* [Cookies et Experience Cloud Identity Service](cookies.md) : le service d’identités Experience Cloud Identity Service utilise l’identifiant de votre organisation, le cookie AMCV d’Experience Cloud et un cookie demdex pour créer et stocker les identifiants uniques et persistants des visiteurs et visiteuses de votre site. Ces cookies permettent au service d’identités d’effectuer le suivi des visiteurs et des visiteuses dans vos différents domaines et d’activer le partage de données entre différentes solutions Experience Cloud.
* [Requête et définition d’ID par le service d’identités d’Experience Cloud](id-request.md) : cette section décrit le processus de demande d’ID et de réponse. Ces exemples illustrent l’affectation d’ID sur chaque site, entre différents sites et pour les sites gérés par différents clients Experience Cloud avec leurs ID d’organisation.
* [Comprendre la synchronisation des identifiants et les taux de correspondance](match-rates.md) : cette section décrit les processus de synchronisation des identifiants et les taux de correspondance dans Experience Cloud Identity Service, y compris Adobe Media Optimizer et le service d’identités.
