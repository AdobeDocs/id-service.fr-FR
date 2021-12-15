---
title: Utiliser l’Opt-in pour contrôler les activités Experience Cloud en fonction du consentement de l’utilisateur
description: L’objet Opt-in Adobe est une extension du service Adobe Experience Platform Identity, conçu pour vous aider à contrôler si et quelles solutions Experience Cloud peuvent créer des cookies sur les pages web ou lancer des balises, en fonction du consentement de l’utilisateur final.
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
source-git-commit: 0dca594c090095a01dfa2d02a98dfeba7ca02dca
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 47%

---

# Contrôler les activités Experience Cloud en fonction du consentement de l’utilisateur

L&#39;Adobe [!UICONTROL Opt-in] L’objet est une extension de l’Adobe. [!UICONTROL Service Experience Platform Identity], conçu pour vous aider à contrôler si et quelles solutions Experience Cloud peuvent créer des cookies sur les pages web ou lancer des balises, en fonction du consentement de l’utilisateur final.

## Principes de base de l’[!UICONTROL Opt-in]

Un aspect important de la réglementation sur la protection des renseignements personnels est l’acquisition et la transmission du consentement des utilisateurs quant à la façon dont leurs données personnelles peuvent être utilisées et par qui. La dernière version de la variable [!UICONTROL Identity Service] inclut une fonctionnalité qui fournit un déclenchement conditionnel (tel que le consentement préalable et postérieur) des balises de solution Experience Cloud, selon que l’utilisateur final a donné ou non son consentement. Ce processus est illustré dans l’image suivante :

![ Diagramme de fonctionnement de l’[!UICONTROL  Opt-in] ](assets/opt-in.png)

[!UICONTROL Opt-in] fonctionne comme suit :

**Si l’[!UICONTROL Opt-in] est activé dans Identity Service (par le biais d’une variable booléenne), les bibliothèques de solutions Experience Cloud ne déclenchent pas les balises ou ne définissent pas de cookies tant que le consentement n’a pas été donné pour cette solution.**

[!UICONTROL Opt-in] vous permet également de décider si les balises se déclenchent avant le consentement de l’utilisateur, puis ces informations de consentement (ainsi que le consentement donné par l’utilisateur final) sont stockées afin qu’elles puissent être utilisées lors des accès suivants. L’enregistrement du consentement est disponible dans les options d’[!UICONTROL Opt-in], ou vous pouvez l’intégrer à un CMP pour stocker les consentements sélectionnés.

## Activation et configuration de l’[!UICONTROL Opt-in]

[!UICONTROL Opt-in] est plus facile à configurer avec les balises Adobe Experience Platform (anciennement Launch). Consultez la courte vidéo suivante pour découvrir comment procéder.

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Si vous n’utilisez pas de balises Experience Platform, vous pouvez définir [!UICONTROL Opt-in]Configuration de dans l’initialisation de l’objet Visiteur global, comme indiqué dans la section [documentation](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/getting-started.html?lang=en).

## Implémentation de l’[!UICONTROL Opt-in] dans la page

Toutes ces configurations et ces tâches d’arrière-plan ne servent qu’à préparer une interface permettant de présenter des options de consentement aux visiteurs du site. Vous pouvez créer cette interface utilisateur ou vous pouvez utiliser un partenaire CMP (Plateforme de gestion du consentement) pour la créer.

Lors de la configuration d’une interface utilisateur afin qu’elle utilise l’[!UICONTROL Opt-in] pour recueillir le consentement, elle doit être configurée pour appeler des API qui se connecteront à l’[!UICONTROL Opt-in] et lui indiqueront de donner son consentement à certaines ou à toutes les solutions Adobe Experience Cloud. Vous trouverez des informations détaillées sur ces API dans la [documentation de référence d’Opt-in](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/api.html?lang=en). Des informations supplémentaires sur l’Opt-in se trouvent également dans les pages de documentation environnantes.

## Démonstration de l’[!UICONTROL Opt-in]

Dans la vidéo suivante, visionnez une démonstration rapide de [!UICONTROL Opt-in] sur la page et comment elle peut affecter si les solutions Experience Cloud peuvent définir des cookies, lancer des balises, etc.

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**REMARQUE :** Il est important de noter qu&#39;au moment de la rédaction du présent article, [!UICONTROL Opt-in] n’a pas été intégré aux bibliothèques pour toutes les applications Experience Cloud. Les bibliothèques actuellement prises en charge pour l’[!UICONTROL Opt-in] sont les suivantes :

* Identity Service
* Analytics
* Audience Manager
* [!DNL Target]
