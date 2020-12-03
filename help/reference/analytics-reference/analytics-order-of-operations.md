---
description: Une fois que vous avez déployé le service d’identification des visiteurs, un visiteur peut être identifié de 5 manières différentes dans Analytics.
keywords: ID Service
seo-description: Une fois que vous avez déployé le service d’identification des visiteurs, un visiteur peut être identifié de 5 manières différentes dans Analytics.
seo-title: Ordre des opérations pour les Analytics ID
title: Ordre des opérations pour les Analytics ID
uuid: cb1d136e-093f-43b0-a7e1-96f1e61fdad0
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 100%

---


# Ordre des opérations pour les Analytics ID {#order-of-operations-for-analytics-ids}

Une fois que vous avez déployé le service d’identification des visiteurs, un visiteur peut être identifié de 5 manières différentes dans Analytics.

Dans de nombreux scénarios, il se peut qu’il y ait 2 ou 3 ID distincts pour un appel. Analytics utilisera comme [!DNL Experience Cloud] ID officiel le premier ID présent dans cette liste. Par exemple, si vous définissez un identifiant visiteur personnalisé (y compris dans le `vid` paramètre de requête), cet identifiant sera utilisé avant les autres identifiants susceptibles d’être présents pour ce même accès. Voir [Définition des Analytics ID et Experience Cloud ID](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6) pour plus d’informations.

<table id="table_D267D36451F643D1BB68AF6FEAA6AD1A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Ordre utilisé </th> 
   <th colname="col2" class="entry"> Paramètre de requête (méthode de collecte) </th> 
   <th colname="col3" class="entry"> Présenter quand </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>1<sup>er</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://docs.adobe.com/content/help/fr-FR/analytics/implementation/vars/config-vars/visitorid.html" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p>Le <span class="codeph">s.visitorID</span> est défini. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>2<sup>e</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://docs.adobe.com/content/help/fr-FR/core-services/interface/ec-cookies/cookies-analytics.html" format="http" scope="external"> aid (cookie s_vi)</a> </p> </td> 
   <td colname="col3"> <p>Le visiteur disposait d’un cookie s_vi existant avant le déploiement du service <span class="keyword">Experience Cloud</span> ID ou vous avez configuré une <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local">période de grâce</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>3<sup>e</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="../../introduction/cookies.md#section-7ff7d96d6e4141b08a84a75a63d7814c" format="dita" scope="local"> Experience Cloud ID (MID) </a> </p> </td> 
   <td colname="col3"> <p>Le navigateur du visiteur accepte les cookies propriétaires. Cela est défini par le cookie AMCV. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>4<sup>e</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://docs.adobe.com/content/help/fr-FR/id-service/using/reference/analytics-reference/analytics-ids.html" format="http" scope="external"> fid (cookie de secours sur H.25.3 ou plus récent ou AppMeasurement pour JavaScript)</a> </p> </td> 
   <td colname="col3"> <p>Un navigateur n’accepte pas les cookies tiers. Or, le serveur de suivi Analytics est configuré en tant que serveur de suivi tiers. </p> <p> <p>Remarque : Le <span class="codeph">fid</span> est un identifiant hérité. Il n’est pas utilisé si vous avez implémenté le service d’ID sur votre site. Dans ce cas, le <span class="codeph"> fid</span> n’est pas nécessaire, car le <a href="../../introduction/cookies.md" format="dita" scope="local"> cookie AMCV</a> propriétaire le rend obsolète. Il a été conservé pour prendre en charge le code hérité et pour des raisons historiques. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>5<sup>e</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://docs.adobe.com/content/help/fr-FR/analytics/technotes/visitor-identification.html" format="http" scope="external"> Adresse IP, Agent utilisateur, Adresse IP de passerelle</a> </p> </td> 
   <td colname="col3"> <p>Le navigateur du visiteur n’accepte pas les cookies. </p> </td> 
  </tr> 
 </tbody> 
</table>

