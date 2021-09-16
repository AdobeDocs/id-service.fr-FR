---
description: Le rôle du service Experience Cloud Identity dans Adobe Experience Cloud.
title: Présentation du service Experience Cloud ID
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
source-git-commit: 2c87022baeb09a8767d0d9627bf2b607c51b2503
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 100%

---

# Présentation du service Experience Cloud ID

Le [!UICONTROL service Experience Cloud Identity] offre un framework d’identification commun aux services principaux d’Experience Cloud (comme les attributs de client et les audiences) au sein du service d’ID Experience Platform.

>[!NOTE]
>
> Il est possible de voir des références au service d’ID sous forme d’acronymes ou d’anciens noms, tels que ECID, service d’Experience Cloud ID (MID) et Visitor ID Service (service identifiant visiteur). Tous ces termes font référence au [!UICONTROL service Experience Cloud Identity]. Vous pouvez également voir [!UICONTROL service Experience Platform Identity]. Pour résumer :

* [!UICONTROL Service Experience Platform Identity] : service qui fait le lien entre les identités. Il s’agit du service de liaison de périphériques pour la gestion de l’expérience basée sur les personnes.
* [!UICONTROL Service Experience Cloud ID] (ECID) : identifiant unique et persistant attribué à un visiteur du site. Il s’agit d’une entité spécifique qui peut être utilisée par le service Platform Identity.

Lorsque votre organisation met en œuvre le service d’ID, cet identifiant permet d’identifier un même visiteur et ses données dans différentes solutions Experience Cloud.

![](assets/ecid-new.png)

En outre, le service d’ID peut remplacer les différents ID spécifiques à une solution (par exemple, Analytics AID). En outre, via la fonctionnalité [ID de client et états d’authentification](/help/reference/authenticated-state.md), le service d’ID vous permet de transmettre vos propres ID de client à Experience Cloud. Sachez toutefois que le service d’ID ne fonctionne qu’avec les solutions auxquelles vous êtes déjà abonné. Il ne vous permettra pas d’accéder à des produits auxquels vous n’êtes pas inscrit.

Par ailleurs, le service d’ID est un composant à part entière de plusieurs fonctionnalités, améliorations et services actuels et futurs d’Experience Cloud. Actuellement, le service d’ID prend en charge [Analytics](http://www.adobe.com/fr/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/fr/marketing-cloud/data-management-platform.html) et [Target](http://www.adobe.com/fr/marketing-cloud/testing-targeting.html). De plus, il est requis si vous souhaitez participer à la coopérative Adobe Experience Cloud Device Co-op. Si vous n’avez pas mis en œuvre le service d’ID, c’est le moment idéal d’envisager une stratégie de migration.

## Résumé des fonctionnalités

En résumé, le service d’ID :

* Crée une clé ou un ID commun pouvant être utilisé pour lier des profils et des identités.
* Identifie de manière unique un appareil sur plusieurs solutions.
* Définit un cookie propriétaire dans le domaine du client afin d’assurer le suivi sur le domaine en question. Consultez le document sur les [cookies et le service Experience Cloud Identity](./cookies.md) pour plus d’informations.
* Reçoit les alias et les mappages d’ID des clients et partenaires d’Experience Cloud.
* Gère la synchronisation des identifiants dans Experience Cloud.
* Prend en charge la synchronisation des identifiants avec différents tiers dans l’écosystème de la technologie publicitaire.

## Conditions requises du service d’ID

Votre solution et les autres bibliothèques de code Adobe doivent répondre [à certaines conditions requises](/help/reference/requirements.md) avant que vous puissiez utiliser le service d’ID.

* [Cookies et service Experience Cloud Identity](cookies.md) : le service d’ID utilise l’ID d’organisation, le cookie AMCV d’Experience Cloud et un cookie demdex pour créer et stocker les identifiants uniques et persistants des visiteurs de votre site. Ces cookies permettent au service d’ID d’effectuer le suivi des visiteurs dans vos différents domaines et d’activer le partage de données entre différentes solutions Experience Cloud.
* [Requête et définition d’ID par le service Experience Cloud Identity](id-request.md) : cette section décrit le processus de demande d’ID et de réponse. Ces exemples illustrent l’affectation d’ID sur chaque site, entre différents sites et pour les sites gérés par différents clients Experience Cloud avec leurs ID d’organisation.
* [Comprendre la synchronisation des identifiants et les taux de correspondance](match-rates.md) : une vue d’ensemble des processus de synchronisation des identifiants et des taux de correspondance dans le service Experience Cloud Identity, y compris Adobe Media Optimizer et le service d’ID.
