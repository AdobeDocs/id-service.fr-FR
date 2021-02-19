---
title: Identification des visiteurs uniques
description: Documentation pour Adobe ECID (Service d’ID)
translation-type: tm+mt
source-git-commit: 8ad5ae179540596913fccc59070aecc57b09f586
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 100%

---


# Identification des visiteurs uniques

La méthode d’identification des visiteurs uniques entre plusieurs contextes comprend une séquence priorisée afin d’assurer la précision de cette détermination. Le tableau suivant présente cette séquence priorisée :

| Ordre utilisé | Paramètre de requête (méthode de collecte) | Valeur de colonne post_visid_type | Présenter quand |
|---|---|---|---|
|  1  | vid [s.visitorID](https://docs.adobe.com/content/help/fr-FR/analytics/components/metrics/unique-visitors.translate.html)  | 0  | `s.visitorID` est défini. |
|  2  | aid  [s_vi cookie](https://docs.adobe.com/content/help/en/analytics/technotes/visitor-identification.html)  | 3  | Le visiteur avait un cookie s_vi existant avant le déploiement du service d’identification des visiteurs, ou vous avez configuré une [période de grâce](https://docs.adobe.com/content/help/fr-FR/id-service/using/reference/analytics-reference/grace-period.html) d’identification des visiteurs.  |
|  3  | mid [cookie AMCV_ défini par Identity Service](https://docs.adobe.com/content/help/fr-FR/id-service/using/home.html)  |  5  |  Le navigateur du visiteur accepte les cookies (propriétaires) et [!UICONTROL Identité] est déployé.  |
|  4  | fid [cookie de secours sur H.25.3 ou plus récent ou AppMeasurement pour JavaScript](https://docs.adobe.com/content/help/en/analytics/technotes/visitor-identification.html)  |  4  |  Le navigateur du visiteur accepte les cookies (propriétaires).  |
|  5  |  [En-tête d’abonné mobile HTTP](https://docs.adobe.com/content/help/en/analytics/technotes/visitor-identification.html)  |  2  |  L’appareil est reconnu comme un appareil mobile.  |
|  6  |  [Adresse IP, Agent utilisateur, Adresse IP de passerelle](https://docs.adobe.com/content/help/en/analytics/technotes/visitor-identification.html)  |  1  |  Le navigateur du visiteur n’accepte pas les cookies. |

Pour plus d’informations sur les rapports de visiteurs uniques, voir [Visiteurs uniques dans Analytics](https://docs.adobe.com/content/help/fr-FR/analytics/components/metrics/unique-visitors.translate.html).
