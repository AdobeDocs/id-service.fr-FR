---
description: Dans certaines mises en œuvre, les identifiants visiteur sont transmis de JavaScript à un serveur, de sorte que des événements Analytics supplémentaires (tels qu’un achat) puissent être envoyés par le serveur.
keywords: Service d’identification
seo-description: Dans certaines mises en œuvre, les identifiants visiteur sont transmis de JavaScript à un serveur, de sorte que des événements Analytics supplémentaires (tels qu’un achat) puissent être envoyés par le serveur.
seo-title: Mise en œuvre côté serveur alliée à JavaScript
title: Mise en œuvre côté serveur alliée à JavaScript
uuid: 256ea0e7-1eb4-4c92-9a7e-f61cb1ed13c7
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Mise en œuvre côté serveur alliée à JavaScript {#server-side-implementation-mixed-with-javascript}

Dans certaines mises en œuvre, les identifiants visiteur sont transmis de JavaScript à un serveur, de sorte que des événements Analytics supplémentaires (tels qu’un achat) puissent être envoyés par le serveur.

L’API du service d’ID fournit les méthodes ([getMarketingCloudVisitorID](../../mcvid-library/mcvid-get-set/mcvid-getmcvid.md) et [getAnalyticsVisitorID](../../mcvid-library/mcvid-get-set/mcvid-getanalyticsvisitorid.md)) permettant de récupérer les valeurs d’ID qui peuvent alors être transmises au serveur.

Veillez à rechercher les identifiants visiteur Experience Cloud et Analytics et envoyez les deux identifiants (s’ils existent) afin de vous assurer que les données envoyées sont associées au profil du visiteur Analytics existant.

>[!IMPORTANT]
>
>AppMeasurement pour Java ne prend actuellement pas en charge le service Experience Cloud ID.

## API d’insertion de données {#section-955ce7664a4646d38b3005cb2df40baf}

Incluez l’identifiant visiteur Analytics (s’il est défini) dans l’élément `<visitorID>`.

Incluez l’identifiant visiteur Experience Cloud dans l’élément `<marketingCloudVisitorID>`.

Voir [Balises XML pris en charge](https://marketing.adobe.com/developer/fr_FR/documentation/data-insertion/r-supported-tags).

## AppMeasurement pour Java {#section-d664b94934924d048300d9c2b6560085}

Le service Experience Cloud ID n’est actuellement pas pris en charge par AppMeasurement pour Java.
