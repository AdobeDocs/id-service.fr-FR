---
description: Le rôle du service Experience Cloud Identity dans Adobe Experience Cloud.
keywords: Service d’identification
seo-description: Le rôle du service Experience Cloud Identity dans Adobe Experience Cloud.
seo-title: À propos du service d’ID
title: Aperçu
uuid: c52d6155-00a0-4fc5-9d8e-5ce00b8d01e6
translation-type: tm+mt
source-git-commit: ec67177fc6491e4c8cea835d198574c9fdb4b01f
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 69%

---


# À propos du service d’ID {#aboutidservice}

Le rôle du service Experience Cloud Identity dans Adobe Experience Cloud.

<!--
mcvid-functionality.xml
-->

## Le service Experience Cloud Identity : un élément fondamental des services principaux {#section-2de0eb1d65664e92a4d8bbb167b84bde}

Le service Experience Cloud Identity active le framework d’identification courant pour les services principaux, les solutions, les attributs du client et les audiences d’Experience Cloud. Pour ce faire, le service attribue un identifiant persistant et unique à un visiteur du site. Lorsque votre organisation met en œuvre le service d’ID, cet identifiant permet d’identifier un même visiteur et ses données dans différentes solutions Experience Cloud.

![](assets/ecid-new.png)

En outre, le service d’ID peut remplacer les différents identifiants spécifiques à la solution (par exemple, Analytics AID). Par le biais de la fonctionnalité [ID de client et états d’authentification](../reference/authenticated-state.md), le service d’ID vous permet de transmettre vos propres ID de client à [!DNL Experience Cloud]. Sachez toutefois que le service d’ID ne fonctionne qu’avec les solutions auxquelles vous êtes déjà abonné. Il ne vous permettra pas d&#39;accéder à d&#39;autres produits si vous n&#39;êtes pas inscrit pour ces derniers.

Par ailleurs, le service d’ID est un composant à part entière de plusieurs fonctionnalités, améliorations et services actuels et [!DNL Experience Cloud] futurs d’. Actuellement, le service d’ID prend en charge [Analytics](http://www.adobe.com/fr/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/fr/marketing-cloud/data-management-platform.html) et [Target](http://www.adobe.com/fr/marketing-cloud/testing-targeting.html). De plus, il est requis si vous souhaitez participer à la coopérative [!DNL Adobe Experience Cloud] Device Co-op. Si vous n’avez pas mis en œuvre le service d’ID, c’est le moment idéal d’envisager une stratégie de migration. Pour plus d’informations sur l’importance et le rôle du service d’ID, voir [Pourquoi le service Experience Cloud Identity vous concerne](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/).

## Résumé des fonctionnalités {#section-96555473455c4bf8924c2d56ff4f3255}

En résumé, le service d’ID :

* Crée une clé ou un identifiant commun qui peut être utilisé pour lier des profils et des identités.
* Identifie de manière unique un périphérique sur plusieurs solutions.
* Définit un cookie propriétaire dans le domaine du client afin d’assurer le suivi sur le même domaine. Voir [Experience Cloud](../introduction/cookies.md).
* Reçoit les alias et les mappages d’ID des clients et partenaires d’[!DNL Experience Cloud].
* Gère la synchronisation des identifiants dans [!DNL Experience Cloud].
* Prend en charge la synchronisation des identifiants avec différents tiers dans l’écosystème de la technologie publicitaire.
