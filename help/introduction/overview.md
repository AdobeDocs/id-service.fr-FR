---
description: Le rôle du service d’identification des visiteurs dans Adobe CX Enterprise.
title: Présentation du service d’identification des visiteurs Adobe
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
TQID: https://experienceleague.adobe.com/fkT81V3iLEz2irg-3SDoyx733RNhqa2zWV1FgiXoYO4
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 497
ht-degree: 18%

---

# Présentation du service d’identification des visiteurs Adobe

Le service d’identification des visiteurs Adobe active le framework d’identification courant pour les services applicatifs d’entreprise CX. Vous pouvez utiliser le service d’identification des visiteurs pour définir l’[ECID](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html?lang=fr).

L’ECID est un espace de noms d’identité partagé utilisé dans les applications Adobe Experience Platform et CX Enterprise pour effectuer le suivi du comportement des visiteurs et des visiteuses et s’assurer que chaque appareil dispose d’un identifiant unique qui peut persister sur plusieurs sessions.

>[!TIP]
>
>Le service d’identification des visiteurs, le service d’identités Experience Platform et l’ECID sont trois entités **différentes**.

Le service d’identification des visiteurs peut remplacer différents identifiants spécifiques à l’application et utiliser la fonctionnalité [ID de client et états d’authentification](/help/reference/authenticated-state.md) pour vous permettre de transmettre vos propres identifiants de client à l’entreprise CX.

>[!NOTE]
>
>Le service d&#39;identification des visiteurs ne fonctionne qu&#39;avec les services d&#39;application d&#39;entreprise CX auxquels vous êtes abonné et ne vous donnera pas accès à d&#39;autres services d&#39;application si vous n&#39;y êtes pas abonné.

Le service d’identification des visiteurs prend en charge les applications suivantes :

* [Adobe Analytics](https://business.adobe.com/fr/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/fr/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/fr/products/target/adobe-target.html)

À l’avenir, le service d’identification des visiteurs fera partie intégrante de nombreuses fonctionnalités, améliorations et services actuels et futurs d’CX Enterprise. Actuellement, le service d’identification des visiteurs prend en charge [Analytics](http://www.adobe.com/fr/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/fr/marketing-cloud/data-management-platform.html) et [Target](http://www.adobe.com/fr/marketing-cloud/testing-targeting.html). Si vous n’avez pas mis en œuvre le service d’identification des visiteurs, c’est le moment idéal d’envisager une stratégie de migration.

## Résumé des fonctionnalités

En résumé, le service d’identification des visiteurs permet d’effectuer les opérations suivantes :

* Identifie de manière unique un visiteur ou une visiteuse sur un appareil dans plusieurs applications.
* Définit un cookie propriétaire dans le domaine du client afin d’assurer le tracking sur le domaine en question. Pour plus d’informations, consultez le document sur les [cookies et le service d’identification des visiteurs](./cookies.md).
* Reçoit les alias et les mappages d’ID des clients et partenaires CX Enterprise.
* Gère la synchronisation des identifiants dans CX Enterprise.
* Prend en charge la synchronisation des identifiants avec différents tiers dans l’écosystème de la technologie publicitaire.

## Exigences du service d’identification des visiteurs

Votre solution et d’autres bibliothèques de code Adobe doivent répondre à [certaines conditions requises](/help/reference/requirements.md) avant de pouvoir utiliser le service d’identification des visiteurs.

* [Cookies et service d’identification des visiteurs](cookies.md) : le service d’identification des visiteurs utilise votre identifiant d’organisation IMS, le cookie AMCV d’entreprise CX et un cookie demdex pour créer et stocker les identifiants uniques et persistants des visiteurs de votre site. Ces cookies permettent au service d’identification des visiteurs de suivre les visiteurs dans vos différents domaines et d’activer le partage de données entre différentes solutions d’entreprise CX.
* [Requête et définition d’ID par le service d’identification des visiteurs](id-request.md) : présentation du processus de demande d’ID et de réponse. Ces exemples illustrent l’affectation d’ID sur chaque site, entre différents sites et pour les sites gérés par différents clients CX Enterprise avec leurs propres ID d’organisation IMS.
* [Comprendre la synchronisation des identifiants et les taux de correspondance ](match-rates.md) : cette section décrit les processus de synchronisation des identifiants et les taux de correspondance dans le service d’identification des visiteurs, y compris Adobe Media Optimizer et le service d’identification des visiteurs.

