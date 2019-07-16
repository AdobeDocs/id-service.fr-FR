---
description: Le cookie AMCV contient l’Experience Cloud ID (MID), ainsi qu’un identifiant de zone géographique pour les visiteurs de votre site. Ces identifiants sont enregistrés en tant que paires clés-valeurs. Le mid user ID contient l’Experience Cloud ID des visiteurs. Le aamlh region ID contient l’identifiant de région des visiteurs de votre site. Vous pouvez récupérer ces informations en analysant le cookie AMCV.
keywords: Service d’identification
seo-description: Le cookie AMCV contient l’Experience Cloud ID (MID), ainsi qu’un identifiant de zone géographique pour les visiteurs de votre site. Ces identifiants sont enregistrés en tant que paires clés-valeurs. Le mid user ID contient l’Experience Cloud ID des visiteurs. Le aamlh region ID contient l’identifiant de région des visiteurs de votre site. Vous pouvez récupérer ces informations en analysant le cookie AMCV.
seo-title: Obtenir les identifiants de région et d’utilisateur à partir du cookie AMCV ou du service d’ID
title: Obtenir les identifiants de région et d’utilisateur à partir du cookie AMCV ou du service d’ID
uuid: bdd9d001-f29f-4ff0-800b-8182243da218
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# Obtenir les identifiants de région et d’utilisateur à partir du cookie AMCV ou du service d’ID {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

Le cookie AMCV contient l’Experience Cloud ID (MID), ainsi qu’un identifiant de zone géographique pour les visiteurs de votre site. Ces identifiants sont enregistrés en tant que paires clés-valeurs. Le mid:user ID contient l’Experience Cloud ID du visiteur. L’identifiant aamlh:region contient l’identifiant de région du visiteur de votre site. Vous pouvez récupérer ces informations en analysant le cookie AMCV.

For more information, see [Get User IDs and Regions Through the Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/aam/dcs-mcid-ids.html).

Si vous êtes un [!DNL Audience Manager] client, vous pouvez obtenir l’identifiant de région à partir de la réponse envoyée par le serveur de collecte des données (DCS). Voir [Obtention des identifiants et des régions à partir d’une réponse DCS](https://marketing.adobe.com/resources/help/en_US/aam/dcs-aam-ids.html).

Vous pouvez également obtenir l’identifiant de région avec une `GET` méthode fournie par le service d’ID. Voir [Obtention des identifiants de région (indicateur de location)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).
