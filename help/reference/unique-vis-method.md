---
title: Identification des visiteurs uniques
description: Documentation pour l’ECID Adobe (service d’identification des visiteurs)
exl-id: 379dbf0a-814d-4348-9ac4-d0e8fc13b9dc
TQID: https://experienceleague.adobe.com/1iZMkBA6-SnhhVmqp8qrFuk-Ev-tKOae5FAduivghXM
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: c2be0313-b3ae-45e0-b454-d20bf54b23f2id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 257
ht-degree: 80%

---

# Identification des visiteurs uniques

La méthode d’ID des visiteurs uniques entre plusieurs contextes comprend une séquence priorisée afin d’assurer la précision de cette détermination. Le tableau suivant présente cette séquence priorisée :

| Ordre utilisé | Paramètre de requête (méthode de collecte) | Valeur de colonne post_visid_type | Présenter quand |
|---|---|---|---|
|  1  | vid [s.visitorID](https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/visitorid.html?lang=fr)  | 0  | `s.visitorID` est défini. |
|  2  | aid  [s_vi cookie](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=fr#section-5d50a078de444d12b7d927d68ff3b679)  | 3  | Un visiteur disposait d’un cookie s_vi existant avant le déploiement du service d’identification des visiteurs, ou un identifiant visiteur [période de grâce](https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/grace-period.html?lang=fr) est configuré.  |
|  3  | mid [Cookie AMCV_ défini par le service d’identification des visiteurs](../introduction/cookies.md)  |  5  |  Le navigateur du visiteur accepte les cookies (propriétaires) et le service d’identification des visiteurs est déployé.  |
|  4  | fid [cookie de secours sur H.25.3 ou plus récent ou AppMeasurement pour JavaScript](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=fr#section-65e33f9bfc264959ac1513e2f4b10ac7)  |  4  |  Le navigateur du visiteur accepte les cookies (propriétaires).  |
|  5  |  [En-tête d’abonné mobile HTTP](https://experienceleague.adobe.com/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-reference.html?lang=fr)  |  2  |  L’appareil est reconnu comme un appareil mobile.  |
|  6  |  [Adresse IP, Agent utilisateur, Adresse IP de passerelle](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=fr)  |  1  |  Le navigateur du visiteur n’accepte pas les cookies. |

{style="table-layout:auto"}

Pour plus d’informations sur les rapports de visiteurs uniques, voir [Visiteurs uniques dans Analytics](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=fr).

