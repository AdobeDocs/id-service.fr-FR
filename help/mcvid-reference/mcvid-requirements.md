---
description: Consultez cette section pour vous assurer que vous utilisez les solutions, services et versions de code appropriés requis par le service Experience Cloud ID.
keywords: Service d’identification
seo-description: Consultez cette section pour vous assurer que vous utilisez les solutions, services et versions de code adéquats requis par le service Experience Cloud ID.
seo-title: Conditions requises pour le service Experience Cloud ID
title: Conditions requises pour le service Experience Cloud ID
uuid: 608 b 1082-6 e 9 e -4101-b 6 cb -60027950109 b
translation-type: tm+mt
source-git-commit: 5eb9eae07f5c0f9eb58b528cce05fc493dfdd584

---


# Conditions requises pour le service Experience Cloud ID {#requirements-for-the-experience-cloud-id-service}

Consultez cette section pour vous assurer que vous utilisez les solutions, services et versions de code adéquats requis par le service Experience Cloud ID.

## Les conditions requises assurent le succès et la prise en charge de la mise en œuvre {#section-15e54a9e9ad2443cb9dc950b4a78f1f1}

Une mise en œuvre réussie et prise en charge répond (ou dépasse) les conditions requises du code et suit les instructions telles qu’elles s’affichent sur l’aide [!DNL Adobe]. Une mise en œuvre non prise en charge entraîne des résultats inattendus et empêche le service à la clientèle et nos équipes d’ingénieurs d’accompagner vos efforts de dépannage ou de résoudre vos problèmes avec le service d’ID.

<table id="table_2216C44AA66248DCAA13BF64BDF2D88A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Type de mise en œuvre </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../mcvid-implementation-guides/mcvid-standard.md#concept-89cd0199a9634fc48644f2d61e3d2445" format="dita" scope="local"> Standard</a> </p> </td> 
   <td colname="col2"> <p>Pour une mise en œuvre standard de Dynamic Tag Management (DTM), vous devez : </p> 
    <ul id="ul_59CDE179566844B494F3068FF6333809"> 
     <li id="li_CCCB6AFC08EE405F94C42216D3CE50AC"> Insérez le code d’intégration du header dans la section <span class="codeph">&lt;head&gt;</span> de votre page. </li> 
     <li id="li_13962F2CB1764091A84863BE499675A2">Insérez le code d’intégration du footer avant la balise de fermeture <span class="codeph">&lt;/body&gt;</span>. </li> 
    </ul> <p>Une mise en œuvre standard n’est pas prise en charge si vous : </p> 
    <ul id="ul_3B62559317ED4C7AA548C3B8DBA281F7"> 
     <li id="li_1F16C6D412944197BEA56BC24730782C"> Insérez l’un de ces deux codes d’intégration DTM à un autre endroit de votre balisage et/ou code de page. </li> 
     <li id="li_05615C01F3A947BBBD41046E68377224"> Ajoutez ou chargez le code DTM avec des méthodes asynchrones, des méthodes d’appel/de rappel ou des wrappers. </li> 
     <li id="li_B2137DFF627B473FA876580449026D2B">Incluez plusieurs instances du code d’intégration sur la même page. </li> 
    </ul> <p>Voir <a href="https://marketing.adobe.com/resources/help/en_US/dtm/?f=deployment.html" format="https" scope="external">Code incorporé et options d’hébergement</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <a href="../mcvid-implementation-guides/mcvid-implementation-guides.md#section-2c4f2db1f9704315a7cccab6d2e07113" format="dita" scope="local"> Guide de mise en œuvre non standard </a> </p> </td> 
   <td colname="col2"> <p>Pour des mises en œuvre non standard ou manuelles, vous devez configurer le service d’ID de la manière décrite dans ce guide. Comme pour les consignes de DTM ci-dessus, un placement et un chargement de code erronés entraînent une mise en œuvre non prise en charge. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Conditions requises pour Experience Cloud : ID d’organisation {#section-a02f537129a64ffbb690d5738d360c26}

Pour utiliser le service d’ID, votre société doit être activée pour [!DNL Experience Cloud] et disposer d’un ID d’organisation. Consultez la liste ci-dessous si vous n’êtes pas sûr de l’état de votre société en ce qui concerne [!DNL Experience Cloud] et si vous devez rechercher votre ID d’organisation.

>[!IMPORTANT]
>
>L&#39;ID d&#39;organisation est sensible à la casse et doit être utilisé exactement comme indiqué.

<table id="table_6C74B676EB094C568D2439FDCC9A7830"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> État d’Experience Cloud </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Activé</b> </p> </td> 
   <td colname="col2"> <p>Si votre société est activée pour <span class="keyword">Experience Cloud</span> mais que vous n’avez pas votre ID d’organisation, consultez la rubrique d’aide sur les <a href="https://marketing.adobe.com/resources/help/en_US/mcloud/organizations.html" format="https" scope="external">ID d’organisation</a> (faites défiler la page jusqu’à la section <i>Trouver votre ID d’organisation</i>). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Pas sûr</b> </p> </td> 
   <td colname="col2"> <p> Si vous ne connaissez pas l’état de votre société en ce qui concerne <span class="keyword">Experience Cloud</span>, demandez à la personne en charge de votre compte Adobe si des employés de votre société peuvent se connecter à l’adresse <a href="https://marketing.adobe.com" format="https" scope="external">marketing.adobe.com</a> à l’aide d’un Adobe ID. S’ils le peuvent, cela signifie que votre société est activée et qu’un administrateur peut afficher l’ID d’organisation. Pour trouver l’ID d’organisation, voir la section Page d’administration dans <a href="https://marketing.adobe.com/resources/help/en_US/mcloud/?f=admin_getting_started" format="https" scope="external">Administration d’Experience Cloud</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Pas activé</b> </p> </td> 
   <td colname="col2"> <p> Si votre société n’est pas activée pour Experience Cloud, voir <a href="https://marketing.adobe.com/resources/help/en_US/mcloud/?f=core_services.html" format="https" scope="external">Services principaux – Comment activer vos solutions</a> pour commencer. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Conditions requises pour Analytics : collecte des données régionale{#section-7d04bb013bc84a25bae3b148bc0ca25f}

Tous les serveurs de suivi ont été convertis en CRD ; il n&#39;est donc pas nécessaire de modifier le serveur de suivi Analytics. [Plus d’informations...](https://docs.adobe.com/content/help/en/analytics/admin/data-collection/regional-data-collection/regional-data-collection.html)

## Bibliothèques de code et versions minimales requises {#section-ad7542a4317d430fa79fc6b095beb84d}

Les sections ci-après répertorient les versions de code minimales qui sont requises pour l’utilisation du service [!DNL Experience Cloud] ID.

>[!TIP]
>
>Nous vous recommandons d&#39;utiliser les dernières versions de code plutôt que les versions minimales requises.

**JavaScript **

<table id="table_8E773F76DBCB4797A0C117080CA8707C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Solution Experience Cloud </th> 
   <th colname="col3" class="entry"> Bibliothèque de code </th> 
   <th colname="col4" class="entry"> Version minimale requise </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b><span class="keyword"></span>  Service Experience Cloud ID</b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> VisitorAPI.js</span> </p> </td> 
   <td colname="col4"> <p>2.0 ou version ultérieure </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="2"> <p> <b> <span class="keyword"> Analytics </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> AppMeasurement.js</span> </p> <p>Voir <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=appmeasure_mjs.html" format="https" scope="external">AppMeasurement pour JavaScript</a>. </p> </td> 
   <td colname="col4"> <p>1.6.4 ou version ultérieure </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> s_code.js</span> </p> </td> 
   <td colname="col4"> <p>H.27 </p> <p> <p>Remarque :<span class="keyword"> Le s_code version H.27 d’Analytics</span> n’est plus pris en charge avec la mise à jour du service d’ID version 1.6.0. Mettez votre code à niveau avec la dernière version d’AppMeasurement. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p>Video Heartbeat </p> <p>Voir <a href="https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/hbvideo/index.html" format="https" scope="external">Video Heartbeat 2.x pour JavaScript</a>. </p> </td> 
   <td colname="col4"> <p>2.0 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> <span class="keyword"> Audience Manager </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> dil.js</span> </p> <p> <a href="https://marketing.adobe.com/resources/help/en_US/aam/?f=c_dil.html" format="https" scope="external">Bibliothèque d’intégration des données</a> (DIL). </p> </td> 
   <td colname="col4"> <p>5.0 </p> <p> 
     <draft-comment>
       mis à jour à partir de 4.9 
     </draft-comment> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="1"> <p> <b> <span class="keyword"> Target </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> mbox.js</span> </p> <p>Voir <a href="https://marketing.adobe.com/resources/help/en_US/target/ov/?f=c_mbox_technical.html" format="https" scope="external">Code mbox</a> </p> </td> 
   <td colname="col4"> <p>61 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> at.js</span> </p> <p>Voir <a href="https://marketing.adobe.com/resources/help/en_US/target/ov2/c_target-atjs-implementation.html" format="https" scope="external">Mise en œuvre de at.js</a>. </p> </td> 
   <td colname="col4"> <p>0.9.1 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Versions minimales des SDK pour Android et iOS {#section-73b2446fba8e463888642c7d7dfd94f1}

Le service d’ID nécessite au minimum les versions de SDK répertoriées ci-dessous.

* Android : 4.11.0
* iOS : 4.11.0

>[!TIP]
>
>Nous vous recommandons d&#39;utiliser les dernières versions de code plutôt que les versions minimales requises.

Le code de votre SDK doit être activé pour le service d’ID. Activez et téléchargez le dernier code du SDK pour chaque application depuis votre compte [Adobe Mobile Services](https://mobilemarketing.adobe.com/). Voir également:

* [Configuration des options du SDK Service d’identification des visiteurs](https://marketing.adobe.com/resources/help/en_US/mobile/t_config_visitor.html)
* [Méthodes des SDK Android](https://marketing.adobe.com/resources/help/en_US/mobile/android/c_marketing_cloud.html)
* [Méthodes des SDK iOS](https://marketing.adobe.com/resources/help/en_US/mobile/ios/marketing_cloud.html)

>[!MORE_ LIKE_ THIS]
>
>* [Bibliothèque de code](../mcvid-library/mcvid-library.md#concept-ff27497375644a898d47984aefb21c97)

