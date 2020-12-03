---
description: Dans certaines mises en œuvre, les identifiants visiteur sont transmis de JavaScript à un serveur, de sorte que des événements Analytics supplémentaires (tels qu’un achat) puissent être envoyés par le serveur.
keywords: ID Service
seo-description: Dans certaines mises en œuvre, les identifiants visiteur sont transmis de JavaScript à un serveur, de sorte que des événements Analytics supplémentaires (tels qu’un achat) puissent être envoyés par le serveur.
seo-title: Mise en œuvre côté serveur alliée à JavaScript
title: Mise en œuvre côté serveur alliée à JavaScript
uuid: 256ea0e7-1eb4-4c92-9a7e-f61cb1ed13c7
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 100%

---


# Mise en œuvre côté serveur alliée à JavaScript {#server-side-implementation-mixed-with-javascript}

Dans certaines mises en œuvre, les identifiants visiteur sont transmis de JavaScript à un serveur, de sorte que des événements Analytics supplémentaires (tels qu’un achat) puissent être envoyés par le serveur.

L’API du service d’ID fournit les méthodes, [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md) et [getAnalyticsVisitorID](../../library/get-set/getanalyticsvisitorid.md), pour récupérer les valeurs d’ID qui peuvent ensuite être transmises au serveur.

Veillez à rechercher les identifiants visiteur Experience Cloud et Analytics et envoyez les deux identifiants (s’ils existent) afin de vous assurer que les données envoyées sont associées au profil du visiteur Analytics existant.

>[!IMPORTANT]
>
>AppMeasurement pour Java ne prend actuellement pas en charge le service Experience Cloud Identity.

## API d’insertion de données {#section-955ce7664a4646d38b3005cb2df40baf}

Incluez l’identifiant visiteur Analytics (s’il est défini) dans l’élément `<visitorID>`.

Incluez l’identifiant visiteur Experience Cloud dans l’élément `<marketingCloudVisitorID>`.

Voir [Balises XML prises en charge](https://www.adobe.io).

## AppMeasurement pour Java {#section-d664b94934924d048300d9c2b6560085}

Le service Experience Cloud Identity n’est actuellement pas pris en charge par AppMeasurement pour Java.
