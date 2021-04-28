---
title: Identification des visiteurs uniques
description: Documentation pour Adobe ECID (Service d’ID)
exl-id: 379dbf0a-814d-4348-9ac4-d0e8fc13b9dc
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '234'
ht-degree: 100%

---

# Identification des visiteurs uniques

La méthode d’ID des visiteurs uniques entre plusieurs contextes comprend une séquence priorisée afin d’assurer la précision de cette détermination. Le tableau suivant présente cette séquence priorisée :

| Ordre utilisé | Paramètre de requête (méthode de collecte) | Valeur de colonne post_visid_type | Présenter quand |
|---|---|---|---|
|  1  | vid [s.visitorID](https://docs.adobe.com/content/help/fr-FR/analytics/components/metrics/unique-visitors.html)  | 0  | `s.visitorID` est défini. |
|  2  | aid  [s_vi cookie](https://docs.adobe.com/content/help/fr-FR/analytics/components/metrics/unique-visitors.html)  | 3  | Le visiteur avait un cookie s_vi existant avant le déploiement du service d’ID des visiteurs, ou vous avez configuré une [période de grâce](https://docs.adobe.com/content/help/fr-FR/id-service/using/reference/analytics-reference/grace-period.html) d’identifiant des visiteurs.  |
|  3  | mid [cookie AMCV_ défini par Identity Service](https://docs.adobe.com/content/help/fr-FR/id-service/using/home.html)  |  5  |  Le navigateur du visiteur accepte les cookies (propriétaires) et [!UICONTROL Identité] est déployé.  |
|  4  | fid [cookie de secours sur H.25.3 ou plus récent ou AppMeasurement pour JavaScript](https://docs.adobe.com/content/help/fr-FR/analytics/components/metrics/unique-visitors.html)  |  4  |  Le navigateur du visiteur accepte les cookies (propriétaires).  |
|  5  |  [En-tête d’abonné mobile HTTP](https://docs.adobe.com/content/help/fr-FR/analytics/components/metrics/unique-visitors.html)  |  2  |  L’appareil est reconnu comme un appareil mobile.  |
|  6  |  [Adresse IP, Agent utilisateur, Adresse IP de passerelle](https://docs.adobe.com/content/help/fr-FR/analytics/components/metrics/unique-visitors.html)  |  1  |  Le navigateur du visiteur n’accepte pas les cookies. |

Pour plus d’informations sur les rapports de visiteurs uniques, voir [Visiteurs uniques dans Analytics](https://docs.adobe.com/content/help/fr-FR/analytics/components/metrics/unique-visitors.html).
