---
description: Le rôle du service dʼidentités d’Experience Cloud dans Adobe Experience Cloud.
keywords: Service d’ID
title: Présentation
exl-id: d907e299-bde0-4b5f-8c16-867a4eaa8be1
source-git-commit: 2c87022baeb09a8767d0d9627bf2b607c51b2503
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 96%

---

# À propos du service d’ID{#aboutidservice}

Le rôle du service dʼidentités d’Experience Cloud dans Adobe Experience Cloud.

<!--
mcvid-functionality.xml
-->

## Le service dʼidentités d’Experience Cloud : un élément fondamental des services principaux {#section-2de0eb1d65664e92a4d8bbb167b84bde}

Le service dʼidentités d’Experience Cloud active le framework d’ID courant pour les services principaux, les solutions, les attributs du client et les audiences d’Experience Cloud. Il fonctionne en attribuant un identifiant persistant unique à un visiteur du site. Lorsque votre organisation met en œuvre le service d’ID, cet identifiant permet d’identifier un même visiteur et ses données dans différentes solutions Experience Cloud.

![](assets/ecid-new.png)

En outre, le service d’ID peut remplacer les différents ID spécifiques à une solution (par exemple, Analytics AID). Par ailleurs, via la fonctionnalité [ID de client et états d’authentification](../reference/authenticated-state.md), le service d’ID permet de transmettre vos propres ID de client à [!DNL Experience Cloud]. Sachez toutefois que le service d’ID ne fonctionne qu’avec les solutions auxquelles vous êtes déjà abonné. Il ne vous permettra pas d’accéder à des produits auxquels vous n’êtes pas inscrit.

Par ailleurs, le service d’ID est un composant à part entière de plusieurs fonctionnalités, améliorations et services actuels et [!DNL Experience Cloud] futurs d’. Actuellement, le service d’ID prend en charge [Analytics](http://www.adobe.com/fr/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/fr/marketing-cloud/data-management-platform.html) et [Target](http://www.adobe.com/fr/marketing-cloud/testing-targeting.html). De plus, il est requis si vous souhaitez participer à la coopérative [!DNL Adobe Experience Cloud] Device Co-op. Si vous n’avez pas mis en œuvre le service d’ID, c’est le moment idéal d’envisager une stratégie de migration.

## Résumé des fonctionnalités {#section-96555473455c4bf8924c2d56ff4f3255}

En résumé, le service d’ID :

* Crée une clé ou un ID commun pouvant être utilisé pour lier des profils et des identités.
* Identifie de manière unique un appareil sur plusieurs solutions.
* Définit un cookie propriétaire dans le domaine du client afin d’assurer le suivi sur le domaine en question. Voir [Experience Cloud](../introduction/cookies.md).
* Reçoit les alias et les mappages d’ID des clients et partenaires d’[!DNL Experience Cloud].
* Gère la synchronisation des identifiants dans [!DNL Experience Cloud].
* Prend en charge la synchronisation des identifiants avec différents tiers dans l’écosystème de la technologie publicitaire.
