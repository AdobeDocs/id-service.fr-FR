---
description: Si plusieurs fichiers JavaScript envoient des données à la même suite de rapports ou si vous avez recours à d’autres technologies sur votre site, par exemple la mesure vidéo Flash, nous vous recommandons de configurer une période de grâce.
keywords: Service d’ID
title: Période de grâce du service d’ID
exl-id: 83b4898c-8358-458b-a798-1e3c9633afe9
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '417'
ht-degree: 100%

---

# Période de grâce du service d’ID {#the-id-service-grace-period}

Si plusieurs fichiers JavaScript envoient des données à la même suite de rapports ou si vous avez recours à d’autres technologies sur votre site, par exemple la mesure vidéo Flash, nous vous recommandons de configurer une période de grâce.

Une fois le service [!DNL Experience Cloud] ID déployé, les nouveaux visiteurs ne reçoivent plus d’identifiant visiteur Analytics du serveur de collecte de données. Si le service [!DNL Experience Cloud] ID n’a pas encore été mis en œuvre sur certaines sections de votre site, l’Experience Cloud ID n’est pas reconnu lorsque les visiteurs parcourent ces sections et un identifiant visiteur Analytics hérité est attribué aux visiteurs. Cela peut créer des comptes de visites dupliqués et une attribution incorrecte.

Si, par exemple, la section Assistance de votre site est gérée dans un système de gestion de contenu distinct, il se peut que vous ayez un fichier JavaScript Analytics différent pour cette section. Si vous déployez l’identifiant du visiteur sur votre site principal avant de déployer le service d’ID du visiteur sur le site d’assistance, les nouveaux visiteurs reçoivent un ID Analytics hérité lorsqu’ils se rendent dans la section d’assistance. Les visites qui portent sur les deux sections du site sont alors signalées comme deux visites distinctes.

Le déploiement du service [!DNL Experience Cloud] ID sur les sites qui utilisent plusieurs fichiers JavaScript ou d’autres technologies (telles que Flash) peut entraîner des problèmes de coordination puisque vous devez activer le service d’ID en même temps sur toutes les parties de votre site. Si vous configurez une période de grâce, les nouveaux visiteurs peuvent continuer à recevoir un identifiant visiteur Analytics du service [!DNL Experience Cloud] ID, de sorte que les visiteurs puissent être identifiés de manière cohérente sur les sections de votre site qui n’ont pas été mises à niveau pour utiliser le service d’ID.

>[!NOTE]
>
>La prise en charge de la période de grâce nécessite la version 1.3 ou ultérieure du service [!DNL Experience Cloud] ID.

## Ai-je besoin d’une période de grâce ? {#section-fd34c7ff697348a39f49258b7d39eb42}

Si vous disposez d’un seul fichier JavaScript Analytics et que vous n’utilisez aucune autre bibliothèque AppMeasurement, vous n’avez pas besoin d’une période de grâce. Vous pouvez simplement mettre à jour le fichier JavaScript unique ; les nouveaux visiteurs seront identifiés de manière cohérente à l’aide d’Experience Cloud ID durant leur visite.

Si plusieurs fichiers JavaScript envoient des données à la *même suite de rapports* ou si vous avez recours à d’autres technologies sur votre site, par exemple la mesure vidéo Flash, nous vous recommandons de configurer une période de grâce.

## Comment mettre en place une période de grâce ? {#section-512d5cd8570e483cbdd8b04457a16ced}

Contactez l’[Assistance clientèle](https://helpx.adobe.com/fr/marketing-cloud/contact-support.html).
