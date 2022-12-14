---
description: Le rôle du service Experience Cloud Identity dans Adobe Experience Cloud.
title: Présentation d’Experience Cloud Identity Service
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
source-git-commit: f7c25f5ebd0690c56c081422949eb34f1f277ae1
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 36%

---

# Présentation d’Experience Cloud Identity Service

Le service Experience Cloud Identity active la structure d’identification courante pour les services d’application Experience Cloud. Vous pouvez utiliser le service Experience Cloud Identity pour définir la variable [Identifiant Experience Cloud (ECID)](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html).

L’ECID est un espace de noms d’identité partagé utilisé dans Adobe Experience Platform et les applications Experience Cloud pour effectuer le suivi du comportement des visiteurs et s’assurer que chaque appareil dispose d’un identifiant unique qui peut persister sur plusieurs sessions.

>[!TIP]
>
>Le service Experience Cloud Identity, le service Experience Platform Identity et l’ECID sont trois **différent** entités.

Le service Identity Experience Cloud peut remplacer différents identifiants spécifiques à l’application et utiliser la variable [ID de client et états d’authentification](/help/reference/authenticated-state.md) pour vous permettre de transmettre vos propres ID de client à l’Experience Cloud.

>[!NOTE]
>
>Le service Experience Cloud Identity ne fonctionne qu’avec les services d’application Experience Cloud auxquels vous êtes abonné et ne vous permet pas d’accéder à d’autres services d’application si vous ne vous y abonnez pas.

Experience Cloud Identity Service prend en charge les applications suivantes :

* [Adobe Analytics](https://business.adobe.com/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/products/target/adobe-target.html)

Par ailleurs, le service d’ID est un composant à part entière de plusieurs fonctionnalités, améliorations et services actuels et futurs d’Experience Cloud. Actuellement, le service d’ID prend en charge [Analytics](http://www.adobe.com/fr/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/fr/marketing-cloud/data-management-platform.html) et [Target](http://www.adobe.com/fr/marketing-cloud/testing-targeting.html). Si vous n’avez pas mis en œuvre le service d’ID, c’est le moment idéal d’envisager une stratégie de migration.

## Résumé des fonctionnalités

En résumé, le service Identity Experience Cloud vous aide à :

* Identifie de manière unique un visiteur sur un appareil dans plusieurs applications.
* Définit un cookie propriétaire dans le domaine du client afin d’assurer le tracking sur le domaine en question. Consultez le document sur les [cookies et le service Experience Cloud Identity](./cookies.md) pour plus d’informations.
* Reçoit les alias et les mappages d’ID des clients et partenaires d’Experience Cloud.
* Gère la synchronisation des identifiants dans Experience Cloud.
* Prend en charge la synchronisation des identifiants avec différents tiers dans l’écosystème de la technologie publicitaire.

## Conditions requises du service Identity Experience Cloud

Votre solution et d’autres bibliothèques de code d’Adobe doivent répondre à [certaines exigences](/help/reference/requirements.md) avant de pouvoir utiliser Identity Service.

* [Cookies et service Identity Experience Cloud](cookies.md): Experience Cloud Identity Service utilise l’ID d’organisation, le cookie AMCV Experience Cloud et un cookie demdex pour créer et stocker les identifiants uniques et persistants des visiteurs de votre site. Ces cookies permettent à Identity Service d’effectuer le suivi des visiteurs sur vos différents domaines et d’activer le partage de données entre différentes solutions Experience Cloud.
* [Requête et définition d’ID par le service Experience Cloud Identity](id-request.md) : cette section décrit le processus de demande d’ID et de réponse. Ces exemples illustrent l’affectation d’ID sur chaque site, entre différents sites et pour les sites gérés par différents clients Experience Cloud avec leurs ID d’organisation.
* [Comprendre la synchronisation des identifiants et les taux de correspondance](match-rates.md): Une vue d’ensemble des processus de synchronisation des identifiants et des taux de correspondance dans le service Experience Cloud Identity, y compris Adobe Media Optimizer et Identity Service.
