---
title: Utiliser l’inclusion pour contrôler les Activités des Experience Cloud en fonction du consentement de l’utilisateur
description: L’objet d’inclusion d’Adobe est une extension du service d’identité Adobe Experience Platform, conçu pour vous aider à contrôler si et quelles solutions Experience Cloud peuvent créer des cookies sur les pages Web ou lancer des balises, en fonction du consentement de l’utilisateur final.
translation-type: tm+mt
source-git-commit: 3aba8820ef40d068c732a637be5ab67652a8d35d
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---


# Contrôler les Activités des Experience Cloud en fonction du consentement de l’utilisateur

L&#39;objet [!UICONTROL d&#39;inclusion] d&#39;Adobe est une extension du service [!UICONTROL d&#39;identité]Experience Platform de l&#39;Adobe, conçu pour vous aider à contrôler si et quelles solutions Experience Cloud peuvent créer des cookies sur les pages Web ou lancer des balises, en fonction du consentement de l&#39;utilisateur final.

## Principes de base de la [!UICONTROL souscription]

Un aspect important de la réglementation sur la protection des renseignements personnels est l&#39;acquisition et la transmission du consentement des utilisateurs quant à la façon dont leurs données personnelles peuvent être utilisées et par qui. La dernière version du service  d&#39;identité comprend des fonctionnalités, qui se situent entre l&#39;utilisateur (l&#39;interface utilisateur) et les solutions d&#39;Adobe et fournit un déclenchement conditionnel (par exemple, pré-et post-consentement) des balises de solution Adobe Experience Cloud selon si l&#39;utilisateur final a donné son consentement. L’image suivante illustre cette situation :

![Diagramme de fonctionnement de l’ [!UICONTROL inclusion]](assets/opt-in.png)

[!UICONTROL L&#39;inscription] est en gros le gardien... ou est-ce le gardien de vitesse ? Vous décidez.

Cela se résume à ceci :

**Si [!UICONTROL l’inclusion] est activée dans le service d’identité (par le biais d’une variable booléenne), les bibliothèques de solutions Experience Cloud ne se voient pas décharger des balises ou définir des cookies tant que le consentement n’a pas été donné pour cette solution.**

[!UICONTROL L’inclusion] vous permet également de décider si des balises se déclenchent *avant* le consentement de l’utilisateur, puis ces informations de consentement (ainsi que le consentement donné par l’utilisateur final) sont stockées, de sorte qu’elles puissent être utilisées lors des accès suivants. L’Enregistrement du consentement est disponible dans les options d’ [!UICONTROL inclusion] , ou vous pouvez l’intégrer à un CMP et le faire stocker dans des sélections de consentement.

## Activation et configuration de l’ [!UICONTROL inclusion]

[!UICONTROL La souscription] est également plus facile à configurer avec Adobe Experience Platform Launch. Vue de la courte vidéo suivante pour découvrir comment procéder.

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Si vous n’utilisez pas l’Experience Platform Launch, vous pouvez définir la configuration de l’ [!UICONTROL inclusion]dans l’initialisation de l’objet Visiteur global, comme indiqué dans la [documentation](https://marketing.adobe.com/resources/help/en_US/mcvid/getting-started.html).

## Implémentation de l’ [!UICONTROL inclusion] dans la page

Toutes ces configurations et ces tâches d&#39;arrière-plan sont juste en préparation pour fournir une interface pour que les visiteurs du site soient présentés avec des options de consentement. Cette interface utilisateur peut être créée par vous ou vous pouvez utiliser un partenaire CMP (Plate-forme de gestion du consentement) pour créer l’interface utilisateur.

Lors de la configuration d’une interface utilisateur pour utiliser l’ [!UICONTROL inclusion] pour recueillir le consentement, elle doit être configurée pour appeler des API qui se connecteront à l’ [!UICONTROL inclusion] et l’informer de donner son consentement à certaines ou à toutes les solutions Adobe Experience Cloud. Vous trouverez des informations détaillées sur ces API dans la documentation [de référence d’](https://marketing.adobe.com/resources/help/en_US/mcvid/api.html)inclusion. Des informations supplémentaires sur l’inclusion se trouvent également dans les pages de documentation environnantes.

## [!UICONTROL Démo d’inclusion]

Dans la vidéo suivante, visionnez une démonstration rapide de l’ [!UICONTROL inclusion] qui fonctionne sur la page et comment elle peut affecter si les solutions Experience Cloud peuvent définir des cookies, lancer des balises, etc.

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**REMARQUE :** Il est important de noter qu&#39;au moment de la rédaction de cet article, [!UICONTROL l&#39;inclusion] n&#39;a pas été intégrée dans les bibliothèques pour toutes les solutions Experience Cloud. Les bibliothèques actuellement prises en charge pour l’ [!UICONTROL inclusion] sont les suivantes :

* Identity Service
* Analytics
* Audience Manager
* [!DNL Target]
