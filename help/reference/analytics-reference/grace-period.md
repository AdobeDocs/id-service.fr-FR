---
description: Si plusieurs fichiers JavaScript envoient des données à la même suite de rapports ou si vous avez recours à d’autres technologies sur votre site, par exemple la mesure vidéo Flash, nous vous recommandons de configurer une période de grâce.
keywords: Service d’identification
seo-description: Si plusieurs fichiers JavaScript envoient des données à la même suite de rapports ou si vous avez recours à d’autres technologies sur votre site, par exemple la mesure vidéo Flash, nous vous recommandons de configurer une période de grâce.
seo-title: Période de grâce du service d’ID
title: Période de grâce du service d’ID
uuid: 10a7db7d-de32-4379-914f-edaf929efa32
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 79%

---


# Période de grâce du service d’ID{#the-id-service-grace-period}

Si plusieurs fichiers JavaScript envoient des données à la même suite de rapports ou si vous avez recours à d’autres technologies sur votre site, par exemple la mesure vidéo Flash, nous vous recommandons de configurer une période de grâce.

Une fois le service [!DNL Experience Cloud] ID déployé, les nouveaux visiteurs ne reçoivent plus d’identifiant visiteur Analytics du serveur de collecte de données. Si le service [!DNL Experience Cloud] ID n’a pas encore été mis en œuvre sur certaines sections de votre site, l’Experience Cloud ID n’est pas reconnu lorsque les visiteurs parcourent ces sections et un identifiant visiteur Analytics hérité est attribué aux visiteurs. Cela peut créer des comptes de visites dupliqués et une attribution incorrecte.

Si, par exemple, la section Assistance de votre site est gérée dans un système de gestion de contenu distinct, il se peut que vous ayez un fichier JavaScript Analytics différent pour cette section. Si vous déployez l’identifiant de visiteur sur votre site principal avant de déployer le service d’identification des visiteurs sur le site d’assistance, les nouveaux visiteurs recevront un identifiant Analytics hérité lorsqu’ils visiteront la section d’assistance et les visites qui s’étendent sur les deux sections du site seront signalées comme des visites différentes.

Le déploiement du service [!DNL Experience Cloud] ID sur les sites qui utilisent plusieurs fichiers JavaScript ou d’autres technologies (telles que Flash) peut entraîner des problèmes de coordination puisque vous devez activer le service d’ID en même temps sur toutes les parties de votre site. Si vous configurez une période de grâce, les nouveaux visiteurs peuvent continuer à recevoir un identifiant visiteur Analytics du service [!DNL Experience Cloud] ID, de sorte que les visiteurs puissent être identifiés de manière cohérente sur les sections de votre site qui n’ont pas été mises à niveau pour utiliser le service d’ID.

>[!NOTE]
>
>La prise en charge de la période de grâce nécessite la version 1.3 ou ultérieure du service [!DNL Experience Cloud] ID.

## Ai-je besoin d’une période de grâce ?{#section-fd34c7ff697348a39f49258b7d39eb42}

Si vous disposez d’un seul fichier JavaScript Analytics et que vous n’utilisez aucune autre bibliothèque AppMeasurement, vous n’avez pas besoin d’une période de grâce. Vous pouvez simplement mettre à jour le fichier JavaScript unique ; les nouveaux visiteurs seront identifiés de manière cohérente à l’aide de Experience Cloud ID durant leur visite.

Si vous avez plusieurs fichiers JavaScript qui envoient des données à la *même suite de rapports* ou si vous utilisez d’autres technologies sur votre site, telles que la mesure vidéo par Flash, nous vous recommandons de configurer une période de grâce.

## Comment mettre en place une période de grâce ?  {#section-512d5cd8570e483cbdd8b04457a16ced}

Contactez le [service à la clientèle](https://helpx.adobe.com/fr/marketing-cloud/contact-support.html).
