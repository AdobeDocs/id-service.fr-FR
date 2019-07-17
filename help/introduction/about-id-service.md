---
description: Rôle du service d'identité Experience Cloud dans Adobe Experience Cloud.
keywords: Service d’identification
seo-description: Rôle du service d'identité Experience Cloud dans Adobe Experience Cloud.
seo-title: À propos du service d’ID
title: Aperçu
uuid: c52d6155-00a0-4fc5-9d8e-5ce00b8d01e6
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# À propos du service d’ID{#aboutidservice}

Rôle du service d'identité Experience Cloud dans Adobe Experience Cloud.

<!--
mcvid-functionality.xml
-->

## The Experience Cloud Identity Service: A Foundational Element of Core Services {#section-2de0eb1d65664e92a4d8bbb167b84bde}

Le service d'identité Experience Cloud active la structure d'identification commune pour les services principaux d'Experience Cloud, les solutions et les attributs et audiences du client dans le service principal People. Pour ce faire, il attribue un identifiant persistant et unique à un visiteur du site. Lorsque votre organisation met en œuvre le service d’ID, cet identifiant permet d’identifier un même visiteur et ses données dans différentes solutions Experience Cloud.

![](assets/ecid.png)

Par ailleurs, le service d’ID peut remplacer les différents identifiants spécifiques aux solutions (par exemple, Analytics AID). Ainsi, au moyen de la fonctionnalité [ID de client et états d’authentification](../reference/authenticated-state.md), le service d’ID permet de transmettre vos propres ID de client à [!DNL Experience Cloud]. Souvenez-vous toutefois que le service d’ID ne fonctionne qu’avec les solutions auxquelles vous êtes déjà abonné. Il ne vous permettra pas d’accéder à d’autres produits si vous n’êtes pas inscrit à ces derniers.

Par ailleurs, le service d’ID est un composant à part entière de plusieurs fonctionnalités, améliorations et services actuels et [!DNL Experience Cloud] futurs d’. Actuellement, le service d’ID prend en charge [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html) et [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html). De plus, il est requis si vous souhaitez participer à la coopérative [!DNL Adobe Experience Cloud] Device Co-op. Si vous n’avez pas mis en œuvre le service d’ID, c’est le moment idéal d’envisager une stratégie de migration. For more information about the importance and role of the ID service, see [Why the Experience Cloud Identity Service Should be on Your Radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/).

## Résumé des fonctionnalités {#section-96555473455c4bf8924c2d56ff4f3255}

Pour résumer, le service d’ID :

* Crée une clé ou un ID commun qui peut être utilisé pour lier les profils et les identités.
* Identifie de manière unique un appareil sur plusieurs solutions.
* Définit un cookie propriétaire dans le domaine du client pour assurer le suivi sur le même domaine. Voir [Experience Cloud](../introduction/cookies.md).
* Reçoit les alias et les mappages d’ID des [!DNL Experience Cloud] clients et partenaires d’.
* Gère la synchronisation des identifiants dans [!DNL Experience Cloud].
* Prend en charge la synchronisation des identifiants avec différents tiers dans l’écosystème de la technologie publicitaire.
