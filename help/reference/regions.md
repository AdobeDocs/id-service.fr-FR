---
description: Le cookie AMCV contient l’Experience Cloud ID (MID) et un identifiant de région pour les visiteurs de votre site. Ces identifiants sont stockés en tant que paires clé-valeur. Le mid user ID contient l’Experience Cloud ID des visiteurs. Le aamlh region ID contient l’identifiant de région des visiteurs de votre site. Vous pouvez récupérer ces informations en analysant le cookie AMCV.
keywords: ID Service
seo-description: Le cookie AMCV contient l’Experience Cloud ID (MID) et un identifiant de région pour les visiteurs de votre site. Ces identifiants sont stockés en tant que paires clé-valeur. Le mid user ID contient l’Experience Cloud ID des visiteurs. Le aamlh region ID contient l’identifiant de région des visiteurs de votre site. Vous pouvez récupérer ces informations en analysant le cookie AMCV.
seo-title: Obtenir les identifiants de région et d’utilisateur à partir du cookie AMCV ou du service d’ID
title: Obtenir les identifiants de région et d’utilisateur à partir du cookie AMCV ou du service d’ID
uuid: bdd9d001-f29f-4ff0-800b-8182243da218
translation-type: ht
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: ht
source-wordcount: '295'
ht-degree: 100%

---


# Obtenir les identifiants de région et d’utilisateur à partir du cookie AMCV ou du service d’ID {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

Le cookie AMCV contient l’Experience Cloud ID (MID) et un identifiant de région pour les visiteurs de votre site. Ces identifiants sont stockés en tant que paires clé-valeur. Le mid:user ID contient l’Experience Cloud ID des visiteurs. Le aamlh:region ID contient l’identifiant de région des visiteurs de votre site. Vous pouvez récupérer ces informations en analysant le cookie AMCV.

Pour plus d’informations, voir [Obtention des identifiants de région et d’utilisateur via Experience Cloud Identity Service](https://docs.adobe.com/content/help/fr-FR/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html).

Si vous êtes un [!DNL Audience Manager] client, vous pouvez obtenir l’identifiant de région à partir de la réponse envoyée par le serveur de collecte des données (DCS). Voir [Obtention des identifiants de région à partir d’une réponse DCS](https://docs.adobe.com/content/help/fr-FR/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html).

Vous pouvez également obtenir l’identifiant de région avec une `GET` méthode fournie par le service d’ID. Voir [Obtention des identifiants de région (indicateur de location)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).
