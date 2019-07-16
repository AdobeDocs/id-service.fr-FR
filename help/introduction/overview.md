---
description: Rôle du service d'identité d'Experience Platform dans Adobe Experience Cloud.
seo-description: Le service d'identité Experience Platform active la structure d'identification commune pour les services principaux d'Experience Cloud, les solutions et les attributs et audiences du client dans le service principal People.
seo-title: Aperçu du service d’ID
title: Aperçu
uuid: null
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# Aperçu

Le service d&#39;identité Experience Platform active la structure d&#39;identification commune pour les services principaux d&#39;Experience Cloud, les solutions et les attributs et audiences du client dans le service principal People. Pour ce faire, il attribue un identifiant persistant et unique à un visiteur du site. Lorsque votre organisation met en œuvre le service d’ID, cet identifiant permet d’identifier un même visiteur et ses données dans différentes solutions Experience Cloud.

![](assets/ecid.png)

Par ailleurs, le service d’ID peut remplacer les différents identifiants spécifiques aux solutions (par exemple, Analytics AID). Ainsi, au moyen de la fonctionnalité [ID de client et états d’authentification](/help/reference/authenticated-state.md), le service d’ID permet de transmettre vos propres ID de client à Experience Cloud. Souvenez-vous toutefois que le service d’ID ne fonctionne qu’avec les solutions auxquelles vous êtes déjà abonné. Il ne vous permettra pas d’accéder à d’autres produits si vous n’êtes pas inscrit à ces derniers.

Par ailleurs, le service d’ID est un composant à part entière de plusieurs fonctionnalités, améliorations et services actuels et futurs d’Experience Cloud. Actuellement, le service d’ID prend en charge [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html) et [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html). De plus, il est requis si vous souhaitez participer à la coopérative Adobe Experience Cloud Device Co-op. Si vous n’avez pas mis en œuvre le service d’ID, c’est le moment idéal d’envisager une stratégie de migration. For more information about the importance and role of the ID service, see [Why the Experience Platform Identity Service Should be on Your Radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/).

## Résumé des fonctionnalités

Pour résumer, le service d’ID :

* Crée une clé ou un ID commun qui peut être utilisé pour lier les profils et les identités.
* Identifie de manière unique un appareil sur plusieurs solutions.
* Définit un cookie propriétaire dans le domaine du client pour assurer le suivi sur le même domaine. Voir Experience Cloud.
* Reçoit les alias et les mappages d’ID des clients et partenaires d’Experience Cloud.
* Gère la synchronisation des identifiants dans Experience Cloud.
* Prend en charge la synchronisation des identifiants avec différents tiers dans l’écosystème de la technologie publicitaire.

## Conditions requises du service d’ID

Votre solution et les autres bibliothèques de code Adobe doivent répondre [à certaines conditions requises](/help/reference/requirements.md) avant que vous puissiez utiliser le service d’ID.

* [Cookies et service d&#39;identité de Platform Platform](cookies.md): Le service d&#39;ID utilise votre ID d&#39;organisation, le cookie AMCV Experience Cloud et un cookie demdex pour créer et stocker des identifiants uniques et persistants pour les visiteurs de votre site. Ces cookies permettent au service d’ID d’effectuer le suivi des visiteurs dans vos différents domaines et d’activer le partage de données entre différentes solutions Experience Cloud.
* [Demande et définition d&#39;identifiants par le service d&#39;identité de Platform Platform](id-request.md): Présentation du processus de demande et de réponse d&#39;ID. Ces exemples illustrent l’affectation d’ID sur chaque site, entre différents sites et pour les sites gérés par différents clients Experience Cloud avec leurs ID d’organisation.
* [Comprendre la synchronisation des identifiants et les taux de correspondance](match-rates.md): Présentation des processus de synchronisation des identifiants et des taux de correspondance dans le service d&#39;identité d&#39;Experience Platform, y compris Adobe Media Optimizer et le service d&#39;ID.