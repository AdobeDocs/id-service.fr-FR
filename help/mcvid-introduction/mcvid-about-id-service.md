---
description: Le rôle du service Experience Cloud ID dans Adobe Experience Cloud.
keywords: Service d’identification
seo-description: Le rôle du service Experience Cloud ID dans Adobe Experience Cloud.
seo-title: A propos du service d'ID
title: Aperçu
uuid: c 52 d 6155-00 a 0-4 fc 5-9 d 8 e -5 ce 00 b 8 d 01 e 6
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# A propos du service d&#39;ID{#aboutidservice}

Le rôle du service Experience Cloud ID dans Adobe Experience Cloud.

<!--
mcvid-functionality.xml
-->

## Le service Experience Cloud ID : un élément fondamental des services principaux {#section-2de0eb1d65664e92a4d8bbb167b84bde}

Le service Experience Cloud ID active la structure d’identification courante pour les services principaux, les solutions, les attributs du client et les audiences d’Experience Cloud dans le service principal aux personnes. Pour ce faire, il attribue un identifiant persistant et unique à un visiteur du site. Lorsque votre organisation met en œuvre le service d’ID, cet identifiant permet d’identifier un même visiteur et ses données dans différentes solutions Experience Cloud.

![](assets/ecid.png)

Par ailleurs, le service d’ID peut remplacer les différents identifiants spécifiques aux solutions (par exemple, Analytics AID). Ainsi, au moyen de la fonctionnalité [ID de client et états d’authentification](../mcvid-reference/mcvid-authenticated-state.md), le service d’ID permet de transmettre vos propres ID de client à [!DNL Experience Cloud]. Souvenez-vous toutefois que le service d’ID ne fonctionne qu’avec les solutions auxquelles vous êtes déjà abonné. Il ne vous permettra pas d’accéder à d’autres produits si vous n’êtes pas inscrit à ces derniers.

Par ailleurs, le service d’ID est un composant à part entière de plusieurs fonctionnalités, améliorations et services actuels et futurs d’[!DNL Experience Cloud]. Actuellement, le service d’ID prend en charge [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html) et [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html). De plus, il est requis si vous souhaitez participer à la coopérative [!DNL Adobe Experience Cloud] Device Co-op. Si vous n’avez pas mis en œuvre le service d’ID, c’est le moment idéal d’envisager une stratégie de migration. Pour plus d’informations sur l’importance et le rôle du service d’ID, voir [Pourquoi le service Experience Cloud ID vous concerne](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/).

## Résumé des fonctionnalités {#section-96555473455c4bf8924c2d56ff4f3255}

Pour résumer, le service d’ID :

* Crée une clé ou un ID commun qui peut être utilisé pour lier les profils et les identités.
* Identifie de manière unique un appareil sur plusieurs solutions.
* Définit un cookie propriétaire dans le domaine du client pour assurer le suivi sur le même domaine. Voir [Experience Cloud](../mcvid-introduction/mcvid-cookies.md).
* Reçoit les alias et les mappages d’ID des clients et partenaires d’[!DNL Experience Cloud].
* Gère la synchronisation des identifiants dans [!DNL Experience Cloud]le champ.
* Prend en charge la synchronisation des identifiants avec différents tiers dans l’écosystème de la technologie publicitaire.