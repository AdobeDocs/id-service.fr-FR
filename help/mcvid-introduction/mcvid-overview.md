---
description: Le rôle du service Experience Cloud ID dans Adobe Experience Cloud.
seo-description: Le service Experience Cloud ID active la structure d’identification courante pour les services principaux, les solutions, les attributs du client et les audiences d’Experience Cloud dans le service principal aux personnes.
seo-title: Présentation du service d'ID
title: Aperçu
uuid: null
translation-type: tm+mt
source-git-commit: 1c6dc1871ee2e7b8d1f510576836519f7383b809

---


# Aperçu

Le service Experience Cloud ID active la structure d’identification courante pour les services principaux, les solutions, les attributs du client et les audiences d’Experience Cloud dans le service principal aux personnes. Pour ce faire, il attribue un identifiant persistant et unique à un visiteur du site. Lorsque votre organisation met en œuvre le service d’ID, cet identifiant permet d’identifier un même visiteur et ses données dans différentes solutions Experience Cloud.

![](assets/ecid.png)

Par ailleurs, le service d’ID peut remplacer les différents identifiants spécifiques aux solutions (par exemple, Analytics AID). Ainsi, au moyen de la fonctionnalité [ID de client et états d’authentification](/help/mcvid-reference/mcvid-authenticated-state.md), le service d’ID permet de transmettre vos propres ID de client à Experience Cloud. Souvenez-vous toutefois que le service d’ID ne fonctionne qu’avec les solutions auxquelles vous êtes déjà abonné. Il ne vous permettra pas d’accéder à d’autres produits si vous n’êtes pas inscrit à ces derniers.

Par ailleurs, le service d’ID est un composant à part entière de plusieurs fonctionnalités, améliorations et services actuels et futurs d’Experience Cloud. Actuellement, le service d’ID prend en charge [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html) et [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html). De plus, il est requis si vous souhaitez participer à la coopérative Adobe Experience Cloud Device Co-op. Si vous n’avez pas mis en œuvre le service d’ID, c’est le moment idéal d’envisager une stratégie de migration. Pour plus d’informations sur l’importance et le rôle du service d’ID, voir [Pourquoi le service Experience Cloud ID vous concerne](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/).

## Résumé des fonctionnalités

Pour résumer, le service d’ID :

* Crée une clé ou un ID commun qui peut être utilisé pour lier les profils et les identités.
* Identifie de manière unique un appareil sur plusieurs solutions.
* Définit un cookie propriétaire dans le domaine du client pour assurer le suivi sur le même domaine. Voir Experience Cloud.
* Reçoit les alias et les mappages d’ID des clients et partenaires d’Experience Cloud.
* Gère la synchronisation des identifiants dans Experience Cloud.
* Prend en charge la synchronisation des identifiants avec différents tiers dans l’écosystème de la technologie publicitaire.

## Conditions requises du service d’ID

Votre solution et les autres bibliothèques de code Adobe doivent répondre [certaines conditions](/help/mcvid-reference/mcvid-requirements.md) requises avant d&#39;utiliser le service d&#39;ID.

* [Cookies et service Experience Cloud ID](mcvid-cookies.md): Le service d&#39;ID utilise votre ID d&#39;organisation, le cookie AMCV Experience Cloud et un cookie demdex pour créer et stocker des identifiants uniques et persistants pour les visiteurs de votre site. Ces cookies permettent au service d’ID d’effectuer le suivi des visiteurs dans vos différents domaines et d’activer le partage de données entre différentes solutions Experience Cloud.
* [Demande et définition d&#39;identifiants](mcvid-id-request.md)par le service Experience Cloud ID Présentation du processus de demande et de réponse d&#39;ID. Ces exemples illustrent l’affectation d’ID sur chaque site, entre différents sites et pour les sites gérés par différents clients Experience Cloud avec leurs ID d’organisation.
* [Comprendre la synchronisation des identifiants et les taux de correspondance](mcvid-match-rates.md): Présentation des processus de synchronisation des identifiants et des taux de correspondance dans le service Experience Cloud ID, y compris Adobe Media Optimizer et le service d&#39;ID.