---
description: Rôle du service d’identité Experience Cloud dans Adobe Experience Cloud.
seo-description: Le service d’identité d’Experience Cloud (anciennement le service d’identification des visiteurs ou le service de Marketing Cloud ID) active le cadre d’identification commun pour les services d’Experience Cloud, tels que les attributs du client et les audiences.
seo-title: Présentation du service d’ID Experience Cloud
title: Présentation du service d’ID Experience Cloud
translation-type: tm+mt
source-git-commit: 98b72f87b188debd6a5f6b86822c3f714647de61

---


# Présentation du service d’ID Experience Cloud

The [!UICONTROL Experience Cloud Identity Service] enables the common identification framework for Experience Cloud Core Services (such as customer attributes and audiences) solutions in the Experience Platform Identity Service.

>[!NOTE]
>
> Vous pouvez voir les références au service d’ID sous forme d’acronymes ou d’anciens noms, tels que ECID, Marketing Cloud ID Service (MID) et Visitor ID Service. Elles se rapportent au service [!UICONTROL d’identité]Experience Cloud. Vous pouvez également voir [!UICONTROL Experience Platform Identity Service]. Pour clarifier :

* [!UICONTROL Experience Platform Identity Service]: Service qui lie les identités. Il s’agit du service de liaison de périphériques pour la gestion de l’expérience basée sur les personnes.
* [!UICONTROL Experience Cloud ID Service] (ECID) : Identifiant unique et persistant attribué à un visiteur du site. Il s’agit d’une entité spécifique qui peut être utilisée par Platform Identity Service.

Lorsque votre organisation met en œuvre le service d’ID, cet identifiant permet d’identifier un même visiteur et ses données dans différentes solutions Experience Cloud.

![](assets/ecid-new.png)

Par ailleurs, le service d’ID peut remplacer les différents identifiants spécifiques aux solutions (par exemple, Analytics AID). Ainsi, au moyen de la fonctionnalité [ID de client et états d’authentification](/help/reference/authenticated-state.md), le service d’ID permet de transmettre vos propres ID de client à Experience Cloud. Souvenez-vous toutefois que le service d’ID ne fonctionne qu’avec les solutions auxquelles vous êtes déjà abonné. Il ne vous permettra pas d’accéder à d’autres produits si vous n’êtes pas inscrit à ces derniers.

Par ailleurs, le service d’ID est un composant à part entière de plusieurs fonctionnalités, améliorations et services actuels et futurs d’Experience Cloud. Actuellement, le service d’ID prend en charge [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html) et [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html). De plus, il est requis si vous souhaitez participer à la coopérative Adobe Experience Cloud Device Co-op. Si vous n’avez pas mis en œuvre le service d’ID, c’est le moment idéal d’envisager une stratégie de migration. Pour plus d’informations sur l’importance et le rôle du service d’ID, voir [Pourquoi le service Experience Cloud Identity vous concerne](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/).

## Résumé des fonctionnalités

Pour résumer, le service d’ID :

* Crée une clé ou un ID commun qui peut être utilisé pour lier les profils et les identités.
* Identifie de manière unique un appareil sur plusieurs solutions.
* Définit un cookie propriétaire dans le domaine du client pour assurer le suivi sur le même domaine. Voir le document sur les [cookies et Experience Cloud Identity Service](https://docs.adobe.com/content/help/en/id-service/using/intro/cookies.html) pour plus d’informations.
* Reçoit les alias et les mappages d’ID des clients et partenaires d’Experience Cloud.
* Gère la synchronisation des identifiants dans Experience Cloud.
* Prend en charge la synchronisation des identifiants avec différents tiers dans l’écosystème de la technologie publicitaire.

## Conditions requises du service d’ID

Votre solution et les autres bibliothèques de code Adobe doivent répondre [à certaines conditions requises](/help/reference/requirements.md) avant que vous puissiez utiliser le service d’ID.

* [Cookies et service Experience Cloud Identity](cookies.md) : le service d’ID utilise l’ID d’organisation, le cookie AMCV d’Experience Cloud et un cookie demdex pour créer et stocker les identifiants uniques et persistants des visiteurs de votre site. Ces cookies permettent au service d’ID d’effectuer le suivi des visiteurs dans vos différents domaines et d’activer le partage de données entre différentes solutions Experience Cloud.
* [Requête et définition d’ID par le service Experience Cloud Identity](id-request.md) : cette section décrit le processus de demande d’ID et de réponse. Ces exemples illustrent l’affectation d’ID sur chaque site, entre différents sites et pour les sites gérés par différents clients Experience Cloud avec leurs ID d’organisation.
* [Comprendre la synchronisation des identifiants et les taux de correspondance](match-rates.md) : une vue d’ensemble des processus de synchronisation des identifiants et des taux de correspondance dans le service Experience Cloud Identity, y compris Adobe Media Optimizer et le service d’ID.
