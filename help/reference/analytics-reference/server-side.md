---
description: Dans certaines mises en œuvre, les identifiants visiteur sont transmis de JavaScript à un serveur, de sorte que des événements Analytics supplémentaires (tels qu’un achat) puissent être envoyés par le serveur.
keywords: Service d’ID
title: Mise en œuvre côté serveur alliée à JavaScript
exl-id: 1986ee11-2021-4f34-bb56-6eaa87b6dd6d
source-git-commit: fa2549090e6790763a7ac6b87348789678d18ab6
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 100%

---

# Mise en œuvre côté serveur alliée à JavaScript {#server-side-implementation-mixed-with-javascript}

Dans certaines mises en œuvre, les identifiants visiteur sont transmis de JavaScript à un serveur, de sorte que des événements Analytics supplémentaires (tels qu’un achat) puissent être envoyés par le serveur.

L’API du service d’ID fournit les méthodes, [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md) et [getAnalyticsVisitorID](../../library/get-set/getanalyticsvisitorid.md), pour récupérer les valeurs d’ID qui peuvent ensuite être transmises au serveur.

Veillez à rechercher les identifiants visiteur Experience Cloud et Analytics et envoyez les deux identifiants (s’ils existent) afin de vous assurer que les données envoyées sont associées au profil du visiteur Analytics existant.

>[!IMPORTANT]
>
>AppMeasurement pour Java ne prend actuellement pas en charge le service d’identités d’Experience Cloud.

## API d’insertion de données {#section-955ce7664a4646d38b3005cb2df40baf}

Incluez l’identifiant visiteur Analytics (s’il est défini) dans l’élément `<visitorID>`.

Incluez l’identifiant visiteur Experience Cloud dans l’élément `<marketingCloudVisitorID>`.

Voir [Balises XML prises en charge](https://developer.adobe.com/).

## AppMeasurement pour Java {#section-d664b94934924d048300d9c2b6560085}

Le service dʼidentités d’Experience Cloud n’est actuellement pas pris en charge par AppMeasurement pour Java.
