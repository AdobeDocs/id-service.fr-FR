---
title: Utiliser l’Opt-in pour contrôler les activités Experience Cloud en fonction du consentement de l’utilisateur
description: L’objet Opt-in d’Adobe est une extension d’Adobe Experience Platform Identity Service, conçu pour vous aider à contrôler si et quelles solutions Experience Cloud peuvent créer des cookies sur les pages web ou lancer des balises, en fonction du consentement de l’utilisateur final.
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '554'
ht-degree: 100%

---

# Contrôler les activités Experience Cloud en fonction du consentement de l’utilisateur

L’objet [!UICONTROL Opt-in] d’Adobe est une extension d’Adobe [!UICONTROL Experience Platform Identity Service], conçu pour vous aider à contrôler si et quelles solutions Experience Cloud peuvent créer des cookies sur les pages web ou déclencher des balises, en fonction du consentement de l’utilisateur final.

## Principes de base de l’[!UICONTROL Opt-in]

Un aspect important de la réglementation sur la protection des renseignements personnels est l’acquisition et la transmission du consentement des utilisateurs quant à la façon dont leurs données personnelles peuvent être utilisées et par qui. La dernière version d’[!UICONTROL Identity Service] comprend des fonctionnalités, qui se situent entre l’utilisateur (l’interface utilisateur) et les solutions Adobe et fournit un déclenchement conditionnel (par exemple, pré-et post-consentement) des balises de solution Adobe Experience Cloud selon si l’utilisateur final a donné son consentement ou pas. L’image suivante illustre cette situation :

![ Diagramme de fonctionnement de l’[!UICONTROL  Opt-in] ](assets/opt-in.png)

Pour résumer, l’[!UICONTROL Opt-in] est le gardien de la porte... ou est-ce plutôt le maître des clés ? Vous décidez.

Ça se résume à ceci :

**Si l’[!UICONTROL Opt-in] est activé dans Identity Service (par le biais d’une variable booléenne), les bibliothèques de solutions Experience Cloud ne déclenchent pas les balises ou ne définissent pas de cookies tant que le consentement n’a pas été donné pour cette solution.**

L’[!UICONTROL Opt-in] vous permet également de décider si des balises se déclenchent *avant* le consentement de l’utilisateur, puis ces informations de consentement (ainsi que le consentement donné par l’utilisateur final) sont stockées, afin qu’elles puissent être utilisées lors des accès suivants. L’enregistrement du consentement est disponible dans les options d’[!UICONTROL Opt-in], ou vous pouvez l’intégrer à un CMP pour stocker les consentements sélectionnés.

## Activation et configuration de l’[!UICONTROL Opt-in]

L’[!UICONTROL Opt-in] est également plus facile à configurer avec Adobe Experience Platform Launch. Consultez la courte vidéo suivante pour découvrir comment procéder.

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Si vous n’utilisez pas Experience Platform Launch, vous pouvez définir la configuration de l’[!UICONTROL Opt-in] dans l’initialisation de l’objet Visiteur global, comme indiqué dans la [documentation](https://marketing.adobe.com/resources/help/fr_FR/mcvid/getting-started.html).

## Implémentation de l’[!UICONTROL Opt-in] dans la page

Toutes ces configurations et ces tâches d’arrière-plan ne servent qu’à préparer une interface permettant de présenter des options de consentement aux visiteurs du site. Vous pouvez créer cette interface utilisateur ou vous pouvez utiliser un partenaire CMP (Plateforme de gestion du consentement) pour la créer.

Lors de la configuration d’une interface utilisateur afin qu’elle utilise l’[!UICONTROL Opt-in] pour recueillir le consentement, elle doit être configurée pour appeler des API qui se connecteront à l’[!UICONTROL Opt-in] et lui indiqueront de donner son consentement à certaines ou à toutes les solutions Adobe Experience Cloud. Vous trouverez des informations détaillées sur ces API dans la [documentation de référence d’Opt-in](https://marketing.adobe.com/resources/help/fr_FR/mcvid/api.html). Des informations supplémentaires sur l’Opt-in se trouvent également dans les pages de documentation environnantes.

## Démonstration de l’[!UICONTROL Opt-in]

Dans la vidéo suivante, visionnez une démonstration rapide de l’[!UICONTROL Opt-in] sur la page et découvrez comment il peut influer sur si oui ou non les solutions Experience Cloud définissent les cookies, déclenchent les balises, etc.

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**REMARQUE :** il est important de noter qu’au moment de la rédaction de cet article, l’[!UICONTROL Opt-in] n’a pas été intégré dans les bibliothèques pour toutes les solutions Experience Cloud. Les bibliothèques actuellement prises en charge pour l’[!UICONTROL Opt-in] sont les suivantes :

* Identity Service
* Analytics
* Audience Manager
* [!DNL Target]
