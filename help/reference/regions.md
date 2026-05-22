---
description: Le cookie AMCV contient l’Experience Cloud ID (MID) et un identifiant de région pour les visiteurs de votre site. Ces identifiants sont stockés en tant que paires clé-valeur. Le mid user ID contient l’Experience Cloud ID des visiteurs. Le aamlh region ID contient l’identifiant de région des visiteurs de votre site. Vous pouvez récupérer ces informations en analysant le cookie AMCV.
keywords: Service d’ID
title: Obtenir les identifiants de région et d’utilisateur à partir du cookie AMCV ou du service d’ID
exl-id: 986e761e-4bc7-4511-86b7-7d13a7761a2b
TQID: https://experienceleague.adobe.com/OBzPrrLffDFgRisA27XIIl33x-4aWmj0krXF3prLPUk
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 240
ht-degree: 91%

---

# Obtenir les identifiants de région et d’utilisateur à partir du cookie AMCV ou du service d’ID {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

Le cookie AMCV contient l’Experience Cloud ID (MID) et un identifiant de région pour les visiteurs de votre site. Ces identifiants sont stockés en tant que paires clé-valeur. L’ID mid:user contient l’ID Experience Cloud du visiteur. L’aamlh:region ID contient l’ID de région pour les visiteurs de votre site. Vous pouvez récupérer ces informations en analysant le cookie AMCV.

Pour plus d’informations, voir [Obtention des identifiants de région et d’utilisateur via le service dʼidentités d’Experience Cloud](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html?lang=fr).

Si vous êtes un [!DNL Audience Manager] client, vous pouvez obtenir l’identifiant de région à partir de la réponse envoyée par le serveur de collecte des données (DCS). Voir [Obtention des identifiants de région à partir d’une réponse DCS](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html?lang=fr).

Vous pouvez également obtenir l’identifiant de région avec une `GET` méthode fournie par le service d’ID. Voir [Obtention des identifiants de région (indicateur de location)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).

