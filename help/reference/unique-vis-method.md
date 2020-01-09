---
title: Identification des visiteurs uniques
description: Documentation pour Adobe ECID (service d’ID)
translation-type: tm+mt
source-git-commit: 453a14a4b725dd14f445b089d083a83a5d2ffaa4

---


# Identification des visiteurs uniques

La méthode d’identification des visiteurs uniques entre plusieurs contextes comprend une séquence de priorités afin d’assurer la précision de cette détermination. Le tableau suivant présente cette séquence hiérarchisée :


 
| Commande utilisée| Paramètre de requête (méthode de collecte)| Valeur de colonne post_visid_type| Présente quand ||—|—|—|— || 1 |[vid (s.visitorID)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_custom.html)| 0 |s.visitorID est défini.| 
| 2 | [aid (s_vi cookie)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_analytics.html) | 3 |Visitor had an existing s_vi cookie before you deployed the Visitor ID service, or you have a Visitor ID [grace period](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid_grace_period.html) configured. || 3 |[mid (cookie AMCV_ défini par Identity Service)](https://marketing.adobe.com/resources/help/en_US/mcvid/)| 5 | Le navigateur du visiteur accepte les cookies (propriétaires) et le service d’identité est déployé. || 4 |[fid (cookie de secours sur H.25.3 ou version ultérieure, ou AppMeasurement pour JavaScript)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_fallback.html)| 4 | Le navigateur du visiteur accepte les cookies (propriétaires). || 5 | En-tête[d&#39;abonné mobile](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_mobile.html)HTTP | 2 | Le périphérique est reconnu comme un périphérique mobile. || 6 | Adresse[IP, Agent utilisateur, Adresse](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_fallback.html)IP de passerelle | 1 | Le navigateur du visiteur n’accepte pas les cookies. |


Pour plus d’informations sur le rapport des visiteurs uniques, voir Visiteurs [uniques dans Analytics](https://docs.adobe.com/content/help/en/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html).
