---
description: Le rôle du service Experience Platform Identity dans Adobe Experience Cloud.
seo-description: Le service Experience Platform Identity active le framework d’identification courant pour les services principaux, les solutions, les attributs du client et les audiences d’Experience Cloud.
seo-title: Aperçu du service d’ID
title: Aperçu
uuid: null
translation-type: ht
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# Aperçu

Le service Experience Platform Identity active le framework d’identification courant pour les services principaux, les solutions, les attributs du client et les audiences d’Experience Cloud dans le service Platform Identity. (Vous pouvez voir des références à d’anciens noms ou acronymes, tels que le service Experience Cloud ID, ECID, le service Marketing Cloud ID, MID, et le service d’identification des visiteurs). Pour ce faire, le service Identity attribue un identifiant persistant et unique à un visiteur du site. Lorsque votre organisation met en œuvre le service d’ID, cet identifiant permet d’identifier un même visiteur et ses données dans différentes solutions Experience Cloud.

![](assets/ecid.png)

Par ailleurs, le service d’ID peut remplacer les différents identifiants spécifiques aux solutions (par exemple, Analytics AID). Ainsi, au moyen de la fonctionnalité [ID de client et états d’authentification](/help/reference/authenticated-state.md), le service d’ID permet de transmettre vos propres ID de client à Experience Cloud. Souvenez-vous toutefois que le service d’ID ne fonctionne qu’avec les solutions auxquelles vous êtes déjà abonné. Il ne vous permettra pas d’accéder à d’autres produits si vous n’êtes pas inscrit à ces derniers.

Par ailleurs, le service d’ID est un composant à part entière de plusieurs fonctionnalités, améliorations et services actuels et futurs d’Experience Cloud. Actuellement, le service d’ID prend en charge [Analytics](https://www.adobe.com/fr/analytics/web-analytics.html), [Audience Manager](https://www.adobe.com/fr/analytics/audience-manager.html) et [Target](https://www.adobe.com/fr/marketing/target.html). De plus, il est requis si vous souhaitez participer à la coopérative Adobe Experience Cloud Device Co-op. Si vous n’avez pas mis en œuvre le service d’ID, c’est le moment idéal d’envisager une stratégie de migration. Pour plus d’informations sur l’importance et le rôle du service d’ID, voir [Pourquoi le service Experience Cloud Identity vous concerne](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/).

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

* [Cookies et service Experience Cloud Identity](cookies.md) : le service d’ID utilise l’ID d’organisation, le cookie AMCV d’Experience Cloud et un cookie demdex pour créer et stocker les identifiants uniques et persistants des visiteurs de votre site. Ces cookies permettent au service d’ID d’effectuer le suivi des visiteurs dans vos différents domaines et d’activer le partage de données entre différentes solutions Experience Cloud.
* [Requête et définition d’ID par le service Experience Cloud Identity](id-request.md) : cette section décrit le processus de demande d’ID et de réponse. Ces exemples illustrent l’affectation d’ID sur chaque site, entre différents sites et pour les sites gérés par différents clients Experience Cloud avec leurs ID d’organisation.
* [Comprendre la synchronisation des identifiants et les taux de correspondance](match-rates.md) : une vue d’ensemble des processus de synchronisation des identifiants et des taux de correspondance dans le service Experience Cloud Identity, y compris Adobe Media Optimizer et le service d’ID.