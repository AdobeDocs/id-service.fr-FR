---
title: Utilisation de l’Opt-in pour contrôler les activités Experience Cloud en fonction du consentement de l’utilisateur
description: L’objet Opt-in d’Adobe est une extension du service d’identités d’Adobe Experience Platform, conçue pour vous aider à contrôler si et quelles solutions Experience Cloud peuvent créer des cookies sur les pages web ou lancer des balises, en fonction du consentement de l’utilisateur final.
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
TQID: https://experienceleague.adobe.com/YfYkXzK8wKw6JC3-EB2ljIOfXGXQV5r6Nw2-XYsGW6c
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 517
ht-degree: 39%

---

# Contrôle des activités Experience Cloud en fonction du consentement de l’utilisateur

L’objet [!UICONTROL Opt-in] d’Adobe est une extension d’Adobe [!UICONTROL Experience Platform Identity Service], conçu pour vous aider à contrôler si et quelles solutions Experience Cloud peuvent créer des cookies sur les pages web ou lancer des balises, en fonction du consentement de l’utilisateur final.

## Principes de base de [!UICONTROL Opt-In]

Un aspect important de la réglementation sur la protection des renseignements personnels est l’acquisition et la transmission du consentement des utilisateurs quant à la façon dont leurs données personnelles peuvent être utilisées et par qui. La dernière version de la [!UICONTROL Identity Service] inclut une fonctionnalité permettant le déclenchement conditionnel (par exemple avant et après le consentement) des balises de la solution Experience Cloud, selon que l’utilisateur final a donné ou non son consentement. L’image suivante illustre ce processus :

![Diagramme de fonctionnement de [!UICONTROL Opt-in]](assets/opt-in.png)

[!UICONTROL Opt-in] fonctionne comme suit :

**Si [!UICONTROL Opt-in] est activé dans Identity Service (par le biais d’une variable booléenne), les bibliothèques de solutions Experience Cloud ne déclenchent pas les balises ou ne définissent pas de cookies tant que le consentement n’a pas été donné pour cette solution.**

[!UICONTROL Opt-in] vous permet également de décider si des balises se déclenchent avant le consentement de l’utilisateur, puis ces informations de consentement (ainsi que le consentement donné par l’utilisateur final) sont stockées, afin qu’elles puissent être utilisées lors des accès suivants. Le stockage du consentement est disponible dans les options de [!UICONTROL Opt-in]. Vous pouvez également intégrer une CMP pour qu’elle stocke les sélections de consentement.

## Activation et configuration des [!UICONTROL Opt-In]

[!UICONTROL Opt-in] est plus facile à configurer avec les balises Adobe Experience Platform (anciennement Launch). Consultez la courte vidéo suivante pour découvrir comment procéder.

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Si vous n’utilisez pas de balises Experience Platform, vous pouvez définir la configuration de [!UICONTROL Opt-in] dans l’initialisation de l’objet Visiteur global, comme indiqué dans la [documentation](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/getting-started.html?lang=fr).

## Implémentation de [!UICONTROL Opt-In] sur la page

Toutes ces configurations et ces tâches d’arrière-plan ne servent qu’à préparer une interface permettant de présenter des options de consentement aux visiteurs du site. Vous pouvez créer cette interface utilisateur ou vous pouvez utiliser un partenaire CMP (Plateforme de gestion du consentement) pour la créer.

Lors de la configuration d’une interface utilisateur pour l’utilisation de [!UICONTROL Opt-in] afin de recueillir le consentement, celle-ci doit être configurée pour appeler les API qui se connectent à [!UICONTROL Opt-in] et l’informer afin de donner son consentement à certaines ou à toutes les solutions Adobe Experience Cloud. Vous trouverez des informations détaillées sur ces API dans la [documentation de référence d’Opt-in](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/api.html?lang=fr). Des informations supplémentaires sur l’Opt-in se trouvent également dans les pages de documentation environnantes.

## Démonstration [!UICONTROL Opt-In]

Dans la vidéo suivante, visionnez une démonstration rapide des [!UICONTROL Opt-in] qui travaillent sur la page et découvrez comment elles peuvent déterminer si les solutions Experience Cloud définissent les cookies, déclenchent les balises, etc.

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**REMARQUE :** il est important de noter qu’au moment de la rédaction de cet article, [!UICONTROL Opt-in] n’a pas été intégré dans les bibliothèques pour toutes les applications Experience Cloud. Les bibliothèques actuellement prises en charge pour [!UICONTROL Opt-in] sont les suivantes :

* Service d’identités
* Analytics
* Audience Manager
* [!DNL Target]

