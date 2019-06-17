---
description: Le cookie AMCV contient l’Experience Cloud ID (MID), ainsi qu’un identifiant de zone géographique pour les visiteurs de votre site. Ces identifiants sont enregistrés en tant que paires clés-valeurs. L'utilisateur mid - id détient l'identifiant Experience Cloud ID du visiteur. L'identifiant de région aamlh contient l'identifiant de région des visiteurs de votre site. Vous pouvez récupérer ces informations en analysant le cookie AMCV.
keywords: Service d’identification
seo-description: Le cookie AMCV contient l’Experience Cloud ID (MID), ainsi qu’un identifiant de zone géographique pour les visiteurs de votre site. Ces identifiants sont enregistrés en tant que paires clés-valeurs. L'utilisateur mid - id détient l'identifiant Experience Cloud ID du visiteur. L'identifiant de région aamlh contient l'identifiant de région des visiteurs de votre site. Vous pouvez récupérer ces informations en analysant le cookie AMCV.
seo-title: Obtention des identifiants de région et d’utilisateur à partir du cookie AMCV et du service d’ID
title: Obtention des identifiants de région et d’utilisateur à partir du cookie AMCV et du service d’ID
uuid: bdd 9 d 001-f 29 f -4 ff 0-800 b -8182243 da 218
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Obtenir les identifiants de région et d’utilisateur à partir du cookie AMCV ou du service d’ID {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

Le cookie AMCV contient l’Experience Cloud ID (MID), ainsi qu’un identifiant de zone géographique pour les visiteurs de votre site. Ces identifiants sont enregistrés en tant que paires clés-valeurs. Le mid:user ID contient l’Experience Cloud ID du visiteur. L’identifiant aamlh:region contient l’identifiant de région du visiteur de votre site. Vous pouvez récupérer ces informations en analysant le cookie AMCV.

Pour plus d’informations, voir [Obtention des identifiants et des zones géographiques au moyen du service Experience Cloud ID](https://marketing.adobe.com/resources/help/en_US/aam/dcs-mcid-ids.html).

Si vous êtes un client [!DNL Audience Manager], vous pouvez obtenir l’identifiant de région à partir de la réponse envoyée par le serveur de collecte des données (DCS). Voir [Obtention des identifiants et des régions à partir d’une réponse DCS](https://marketing.adobe.com/resources/help/en_US/aam/dcs-aam-ids.html).

Vous pouvez également obtenir l’identifiant de région avec une méthode `GET` fournie par le service d’ID. Voir [Obtention des identifiants de région (indicateur d&#39;emplacement)](../mcvid-library/mcvid-get-set/mcvid-getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).