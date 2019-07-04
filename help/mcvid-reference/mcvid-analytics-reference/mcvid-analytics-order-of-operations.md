---
description: Une fois que vous avez déployé le service d’identification des visiteurs, un visiteur peut être identifié de 5 manières différentes dans Analytics.
keywords: Service d’identification
seo-description: Une fois que vous avez déployé le service d’identification des visiteurs, un visiteur peut être identifié de 5 manières différentes dans Analytics.
seo-title: Ordre des opérations pour les identifiants Analytics
title: Ordre des opérations pour les identifiants Analytics
uuid: cb1d136e-093f-43b0-a7e1-96f1e61fdad0
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Ordre des opérations pour les Analytics ID{#order-of-operations-for-analytics-ids}

Une fois que vous avez déployé le service d’identification des visiteurs, un visiteur peut être identifié de 5 manières différentes dans Analytics.

Dans de nombreux scénarios, il se peut qu’il y ait 2 ou 3 ID distincts pour un appel. Analytics utilisera comme [!DNL Experience Cloud] ID officiel le premier ID présent dans cette liste. Par exemple, si vous définissez un identifiant visiteur personnalisé (y compris dans le `vid` paramètre de requête), cet identifiant sera utilisé avant les autres identifiants susceptibles d’être présents pour ce même accès. Voir [Définition des Analytics ID et Experience Cloud ID](../../mcvid-reference/mcvid-analytics-reference/mcvid-analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6) pour plus d’informations.

<table id="table_D267D36451F643D1BB68AF6FEAA6AD1A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Ordre utilisé </th> 
   <th colname="col2" class="entry"> Paramètre de requête (méthode de collecte) </th> 
   <th colname="col3" class="entry"> Présent quand </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>1<sup>er</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/fr_FR/sc/implement/visid_custom.html" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p>Le <span class="codeph">s.visitorID</span> est défini. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>2<sup>e</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/fr_FR/sc/implement/visid_analytics.html" format="http" scope="external"> aid (cookie s_vi)</a> </p> </td> 
   <td colname="col3"> <p>Le visiteur disposait d’un cookie s_vi existant avant le déploiement du service <span class="keyword">Experience Cloud</span> ID ou vous avez configuré une <a href="../../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md" format="dita" scope="local">période de grâce</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>3<sup>e</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="../../mcvid-introduction/mcvid-cookies.md#section-7ff7d96d6e4141b08a84a75a63d7814c" format="dita" scope="local"> Experience Cloud ID (MID) </a> </p> </td> 
   <td colname="col3"> <p>Le navigateur du visiteur accepte les cookies propriétaires. Cela est défini par le cookie AMCV. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>4</b><sup>e</sup> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/fr_FR/sc/implement/visid_fallback.html" format="http" scope="external"> fid (cookie de secours sur H.25.3 ou plus récent ou AppMeasurement pour JavaScript)</a> </p> </td> 
   <td colname="col3"> <p>Un navigateur n’accepte pas les cookies tiers. Or, le serveur de suivi Analytics est configuré en tant que serveur de suivi tiers. </p> <p> <p>Remarque : Le <span class="codeph">fid</span> est un identifiant hérité. Il n’est pas utilisé si vous avez implémenté le service d’ID sur votre site. Dans ce cas, le <span class="codeph"> fid</span> n’est pas nécessaire, car le <a href="../../mcvid-introduction/mcvid-cookies.md" format="dita" scope="local"> cookie AMCV</a> propriétaire le rend obsolète. Il a été conservé pour prendre en charge le code hérité et pour des raisons historiques. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>5</b><sup>e</sup> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/fr_FR/sc/implement/visid_fallback.html" format="http" scope="external"> Adresse IP, Agent utilisateur, Adresse IP de passerelle</a> </p> </td> 
   <td colname="col3"> <p>Le navigateur du visiteur n’accepte pas les cookies. </p> </td> 
  </tr> 
 </tbody> 
</table>

