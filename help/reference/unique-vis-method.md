---
title: Identification des visiteurs uniques
description: Documentation pour Adobe ECID (Service d’ID)
exl-id: 379dbf0a-814d-4348-9ac4-d0e8fc13b9dc
TQID: https://experienceleague.adobe.com/1iZMkBA6-SnhhVmqp8qrFuk-Ev-tKOae5FAduivghXM
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 251
ht-degree: 100%

---

# Identification des visiteurs uniques

La méthode d’ID des visiteurs uniques entre plusieurs contextes comprend une séquence priorisée afin d’assurer la précision de cette détermination. Le tableau suivant présente cette séquence priorisée :

| Ordre utilisé | Paramètre de requête (méthode de collecte) | Valeur de colonne post_visid_type | Présenter quand |
|---|---|---|---|
|  1  | vid [s.visitorID](https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/visitorid.html?lang=fr)  | 0  | `s.visitorID` est défini. |
|  2  | aid  [s_vi cookie](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=fr#section-5d50a078de444d12b7d927d68ff3b679)  | 3  | Le visiteur avait un cookie s_vi existant avant le déploiement du service d’ID des visiteurs, ou vous avez configuré une [période de grâce](https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/grace-period.html?lang=fr) d’identifiant des visiteurs.  |
|  3  | mid [cookie AMCV_ défini par Identity Service](../introduction/cookies.md)  |  5  |  Le navigateur du visiteur accepte les cookies (propriétaires) et [!DNL Identity Service] est déployé.  |
|  4  | fid [cookie de secours sur H.25.3 ou plus récent ou AppMeasurement pour JavaScript](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=fr#section-65e33f9bfc264959ac1513e2f4b10ac7)  |  4  |  Le navigateur du visiteur accepte les cookies (propriétaires).  |
|  5  |  [En-tête d’abonné mobile HTTP](https://experienceleague.adobe.com/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-reference.html?lang=fr)  |  2  |  L’appareil est reconnu comme un appareil mobile.  |
|  6  |  [Adresse IP, Agent utilisateur, Adresse IP de passerelle](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=fr)  |  1  |  Le navigateur du visiteur n’accepte pas les cookies. |

{style="table-layout:auto"}

Pour plus d’informations sur les rapports de visiteurs uniques, voir [Visiteurs uniques dans Analytics](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=fr).

