---
description: Le cookie AMCV contient l’Experience Cloud ID (MID) et un identifiant de région pour les visiteurs de votre site. Ces identifiants sont stockés en tant que paires clé-valeur. Le mid user ID contient l’Experience Cloud ID des visiteurs. Le aamlh region ID contient l’identifiant de région des visiteurs de votre site. Vous pouvez récupérer ces informations en analysant le cookie AMCV.
keywords: Service d’ID
title: Obtenir les identifiants de région et d’utilisateur à partir du cookie AMCV ou du service d’ID
exl-id: 986e761e-4bc7-4511-86b7-7d13a7761a2b
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 100%

---

# Obtenir les identifiants de région et d’utilisateur à partir du cookie AMCV ou du service d’ID {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

Le cookie AMCV contient l’Experience Cloud ID (MID) et un identifiant de région pour les visiteurs de votre site. Ces identifiants sont stockés en tant que paires clé-valeur. Le mid:user ID contient l’Experience Cloud ID des visiteurs. Le aamlh:region ID contient l’identifiant de région des visiteurs de votre site. Vous pouvez récupérer ces informations en analysant le cookie AMCV.

Pour plus d’informations, voir [Obtention des identifiants de région et d’utilisateur via Experience Cloud Identity Service](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html?lang=fr).

Si vous êtes un [!DNL Audience Manager] client, vous pouvez obtenir l’identifiant de région à partir de la réponse envoyée par le serveur de collecte des données (DCS). Voir [Obtention des identifiants de région à partir d’une réponse DCS](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html?lang=fr).

Vous pouvez également obtenir l’identifiant de région avec une `GET` méthode fournie par le service d’ID. Voir [Obtention des identifiants de région (indicateur de location)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).
