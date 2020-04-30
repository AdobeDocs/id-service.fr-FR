---
title: Identification des visiteurs uniques
description: Documentation pour Adobe ECID (Service d’ID)
translation-type: tm+mt
source-git-commit: dee27fb0150ce2c40f570f98b9af0b6904c16814

---


# Identification des visiteurs uniques

La méthode d’identification des visiteurs uniques entre plusieurs contextes comprend une séquence priorisée afin d’assurer la précision de cette détermination. Le tableau suivant présente cette séquence priorisée :
 
| Ordre utilisé | Paramètre de requête (méthode de collecte) | valeur de colonne post_visid_type | Présent quand |
|--- |--- |--- |--- |
| 1 | [vid (s.visitorID)](https://marketing.adobe.com/resources/help/fr_FR/sc/implement/visid_custom.html) | 0 |s.visitorID est défini.|
| 2 | [aid (s_vi cookie)](https://marketing.adobe.com/resources/help/fr_FR/sc/implement/visid_analytics.html) | 3 |Visitor had an existing s_vi cookie before you deployed the Visitor ID service, or you have a Visitor ID [grace period](https://docs.adobe.com/content/help/fr-FR/id-service/using/reference/analytics-reference/grace-period.html) configured. |
| 3 | [mid (cookie AMCV_ défini par le service d’ID)](https://marketing.adobe.com/resources/help/fr_FR/mcvid/) | 5 | Le navigateur du visiteur accepte les cookies (propriétaires), et le service d’ID est déployé. |
| 4 | [fid (cookie de secours sur H.25.3 ou version ultérieure, ou AppMeasurement pourr JavaScript)](https://marketing.adobe.com/resources/help/fr_FR/sc/implement/visid_fallback.html) | 4 | Le navigateur du visiteur accepte les cookies (propriétaires). |
| 5 | [En-tête d’abonné mobile HTTP](https://marketing.adobe.com/resources/help/fr_FR/sc/implement/visid_mobile.html) | 2 | L’appareil est reconnu comme appareil mobile. |
| 6 | [Adresse IP, Agent utilisateur, Adresse IP de passerelle](https://marketing.adobe.com/resources/help/fr_FR/sc/implement/visid_fallback.html) | 1 | Le navigateur du visiteur n’accepte pas les cookies. |

Pour plus d’informations sur les rapports de visiteurs uniques, voir [Visiteurs uniques dans Analytics](https://docs.adobe.com/content/help/fr-FR/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html).
