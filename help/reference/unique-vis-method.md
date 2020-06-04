---
title: Identification des visiteurs uniques
description: Documentation pour Adobe ECID (Service d’ID)
translation-type: tm+mt
source-git-commit: d39cb79bac3a0a277e6390a8127c1f1b68579fa6
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 56%

---


# Identification des visiteurs uniques

La méthode d’identification des visiteurs uniques entre plusieurs contextes comprend une séquence priorisée afin d’assurer la précision de cette détermination. Le tableau suivant présente cette séquence priorisée :

| Ordre utilisé | Paramètre de Requête (méthode de collecte) | Valeur de colonne post_visid_type | Présente lorsque |
|---|---|---|---|
|  1  | vid [(s.visitorID)](https://docs.adobe.com/content/help/fr-FR/analytics/technotes/visitor-identification.html)  | 0  | `s.visitorID` est définie. |
|  2  | aid  [(s_vi cookie)](https://docs.adobe.com/content/help/fr-FR/analytics/technotes/visitor-identification.html)  | 3  | Visitor had an existing s_vi cookie before you deployed the Visitor ID service, or you have a Visitor ID [grace period](https://docs.adobe.com/content/help/fr-FR/id-service/using/reference/analytics-reference/grace-period.html) configured.  |
|  3  | mid[(cookie AMCV_ défini par Identity Service)](https://docs.adobe.com/content/help/fr-FR/id-service/using/home.html)  |  5  |  Le navigateur du Visiteur accepte les cookies (propriétaires) et le serviced’identité est déployé.  |
|  4  | fid [(fallback cookie on H.25.3 or newer, or AppMeasurement for JavaScript)](https://docs.adobe.com/content/help/fr-FR/analytics/technotes/visitor-identification.html)  |  4  |  le navigateur du Visiteur accepte les cookies (propriétaires).  |
|  5  |  [En-tête d&#39;abonné mobile HTTP](https://docs.adobe.com/content/help/fr-FR/analytics/technotes/visitor-identification.html)  |  2  |  Le périphérique est reconnu comme un périphérique mobile.  |
|  6  |  [IP Address, User Agent, Gateway IP Address](https://docs.adobe.com/content/help/fr-FR/analytics/technotes/visitor-identification.html)  |  1  |  Le navigateur du Visiteur n’accepte pas les cookies. |

Pour plus d’informations sur les rapports de visiteurs uniques, voir [Visiteurs uniques dans Analytics](https://docs.adobe.com/content/help/fr-FR/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html).
