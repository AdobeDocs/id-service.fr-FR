---
description: Une fois que vous avez déployé le service d’identification des visiteurs, un visiteur peut être identifié de 5 manières différentes dans Analytics.
keywords: Service d’identification
seo-description: Une fois que vous avez déployé le service d’identification des visiteurs, un visiteur peut être identifié de 5 manières différentes dans Analytics.
seo-title: Ordre des opérations pour les identifiants Analytics
title: Ordre des opérations pour les identifiants Analytics
uuid: cb 1 d 136 e -093 f -43 b 0-a 7 e 1-96 f 1 e 61 fdad 0
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# Ordre des opérations pour les Analytics ID{#order-of-operations-for-analytics-ids}

Une fois que vous avez déployé le service d’identification des visiteurs, un visiteur peut être identifié de 5 manières différentes dans Analytics.

Dans de nombreux scénarios, il se peut qu’il y ait 2 ou 3 ID distincts pour un appel. Analytics utilisera comme [!DNL Experience Cloud] ID officiel le premier ID présent dans cette liste. Par exemple, si vous définissez un identifiant visiteur personnalisé (y compris dans le paramètre de requête `vid`), cet identifiant sera utilisé avant les autres identifiants susceptibles d’être présents pour ce même accès. Pour plus d&#39;informations, voir [Définition des identifiants Analytics](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6) et Experience Cloud ID.

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
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_custom" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p>Le <span class="codeph">s.visitorID</span> est défini. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>2<sup>e</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_analytics" format="http" scope="external"> aid (cookie s_vi)</a> </p> </td> 
   <td colname="col3"> <p>Le visiteur avait un cookie s_ vi existant avant le déploiement du service <span class="keyword"> Experience Cloud</span> ID ou vous avez configuré une <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> période</a> de grâce. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>3</b><sup>e</sup> </p> </td> 
   <td colname="col2"> <p> <a href="../../introduction/cookies.md#section-7ff7d96d6e4141b08a84a75a63d7814c" format="dita" scope="local"> Experience Cloud ID (MID) </a> </p> </td> 
   <td colname="col3"> <p>Le navigateur du visiteur accepte les cookies propriétaires. Cela est défini par le cookie AMCV. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>4</b><sup>e</sup> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> fid (cookie de secours sur H.25.3 ou plus récent ou AppMeasurement pour JavaScript)</a> </p> </td> 
   <td colname="col3"> <p>Un navigateur n’accepte pas les cookies tiers. Or, le serveur de suivi Analytics est configuré en tant que serveur de suivi tiers. </p> <p> <p>Remarque : Le <span class="codeph">fid</span> est un identifiant hérité. Il n’est pas utilisé si vous avez implémenté le service d’ID sur votre site. Dans ce cas, <span class="codeph"> le fid n'</span> est pas nécessaire, car le cookie <a href="../../introduction/cookies.md" format="dita" scope="local"> AMCV propriétaire</a> le rend obsolète. Il a été conservé pour prendre en charge le code hérité et pour des raisons historiques. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>5</b><sup>e</sup> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> Adresse IP, Agent utilisateur, Adresse IP de passerelle</a> </p> </td> 
   <td colname="col3"> <p>Le navigateur du visiteur n’accepte pas les cookies. </p> </td> 
  </tr> 
 </tbody> 
</table>

