---
description: Consultez cette section pour vous assurer que vous utilisez les solutions, services et versions de code adéquats requis par le service Experience Cloud Identity.
keywords: Service d’ID
title: Conditions requises pour le service Experience Cloud Identity
exl-id: ebeac4c7-b36c-4a4e-9378-351fac5baf53
source-git-commit: 00ebcaa16ec6b432b480d96fbf79b6a745515b1b
workflow-type: ht
source-wordcount: '653'
ht-degree: 100%

---

# Conditions requises pour le service Experience Cloud Identity {#requirements-for-the-experience-cloud-id-service}

Consultez cette section pour vous assurer que vous utilisez les solutions, services et versions de code adéquats requis par le service Experience Cloud Identity.

## Les conditions requises assurent le succès et la prise en charge de la mise en œuvre {#section-15e54a9e9ad2443cb9dc950b4a78f1f1}

Une mise en œuvre réussie et prise en charge répond (ou dépasse) les conditions requises du code et suit les instructions telles qu’elles s’affichent sur l’aide [!DNL Adobe]. Une mise en œuvre non prise en charge produira des résultats inattendus et empêchera l’assistance clientèle et nos équipes d’ingénieurs de vous aider à résoudre les problèmes ou à les résoudre avec le service d’ID.

### Implémentations standard

Consultez la section [Balises Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=fr) pour votre implémentation standard.

### Implémentations non standard

Pour les mises en œuvre non standard ou manuelles, vous devez configurer le service d’ID comme décrit dans les procédures de ce guide. Comme pour les instructions relatives à DTM ci-dessus, un placement et un chargement de code incorrects créeront une mise en œuvre non prise en charge.

## Conditions requises pour Experience Cloud : ID d’organisation {#section-a02f537129a64ffbb690d5738d360c26}

Pour utiliser le service d’ID, votre société doit être activée pour [!DNL Experience Cloud] et disposer d’un ID d’organisation. Consultez la liste ci-dessous si vous n’êtes pas sûr de l’état de votre société en ce qui concerne [!DNL Experience Cloud] et si vous devez rechercher votre ID d’organisation.

>[!IMPORTANT]
>
>L’ID d’organisation est sensible à la casse est doit être utilisé tel quel.

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
   <td colname="col2"> <p>Si votre société est activée pour <span class="keyword">Experience Cloud</span> mais que vous n’avez pas votre ID d’organisation, consultez la rubrique d’aide sur les <a href="https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html?lang=fr" format="https" scope="external">ID d’organisation</a> (faites défiler la page jusqu’à la section <i>Trouver votre ID d’organisation</i>). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Pas sûr</b> </p> </td> 
   <td colname="col2"> <p> Si vous ne connaissez pas l’état de votre société en ce qui concerne <span class="keyword">Experience Cloud</span>, demandez à la personne en charge de votre compte Adobe si des employés de votre société peuvent se connecter à l’adresse <a href="https://experiencecloud.adobe.com" format="https" scope="external">marketing.adobe.com</a> à l’aide d’un Adobe ID. S’ils le peuvent, cela signifie que votre société est activée et qu’un administrateur peut afficher l’ID d’organisation. Pour trouver l’ID d’organisation, voir la section Page d’administration dans <a href="https://experienceleague.adobe.com/docs/core-services/interface/experience-cloud.html?lang=fr" format="https" scope="external">Administration d’Experience Cloud</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Pas activé</b> </p> </td> 
   <td colname="col2"> <p> Si votre société n’est pas activée pour Experience Cloud, voir <a href="https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html?lang=fr" format="https" scope="external">Services principaux – Comment activer vos solutions</a> pour commencer. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Conditions requises pour Analytics : collecte des données régionale {#section-7d04bb013bc84a25bae3b148bc0ca25f}

Tous les serveurs de suivi ont été convertis en RDC ; il n’est donc pas nécessaire de modifier le serveur de suivi Analytics. [Plus d’informations...](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html?lang=fr)

## Bibliothèques de code et versions minimales requises {#section-ad7542a4317d430fa79fc6b095beb84d}

Les sections ci-après répertorient les versions de code minimales qui sont requises pour l’utilisation du service [!DNL Experience Cloud] ID.

>[!TIP]
>
>Nous vous recommandons d’utiliser les dernières versions du code plutôt que la version minimale requise.

**JavaScript**

<table id="table_8E773F76DBCB4797A0C117080CA8707C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Solution Experience Cloud </th> 
   <th colname="col3" class="entry"> Bibliothèque de code </th> 
   <th colname="col4" class="entry"> Version requise </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b><span class="keyword"> Service </span>Experience Cloud ID</b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> VisitorAPI.js</span> </p> </td> 
   <td colname="col4"> <p>2.0 ou version ultérieure </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="2"> <p> <b> <span class="keyword"> Analytics </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> AppMeasurement.js</span> </p> <p>Voir <a href="https://experienceleague.adobe.com/docs/analytics/implementation/js/overview.html?lang=fr" format="https" scope="external">AppMeasurement pour JavaScript</a>. </p> </td> 
   <td colname="col4"> <p>1.6.4 ou version ultérieure </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> s_code.js</span> </p> </td> 
   <td colname="col4"> <p>H.27 </p> <p> <p>Remarque :<span class="keyword"> Le s_code version H.27 d’Analytics</span> n’est plus pris en charge avec la mise à jour du service d’ID version 1.6.0. Mettez votre code à niveau avec la dernière version d’AppMeasurement. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p>Video Heartbeat </p> <p>Voir <a href="https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=fr" format="https" scope="external">Video Heartbeat 2.x pour JavaScript</a>. </p> </td> 
   <td colname="col4"> <p>2.0 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> <span class="keyword"> Audience Manager </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> dil.js</span> </p> <p> <a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-overview.html?lang=fr" format="https" scope="external">Bibliothèque d’intégration des données</a> (DIL). </p> </td> 
   <td colname="col4"> <p>5.0 </p></td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="1"> <p> <b> <span class="keyword"> Target </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> mbox.js</span> </p> <p>Voir <a href="https://experienceleague.adobe.com/docs/target-dev/developer/client-side/at-js-implementation/overview.html?lang=fr" format="https" scope="external">Code mbox</a>. </p> </td> 
   <td colname="col4"> <p>61 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> at.js</span> </p> <p>Voir <a href="https://experienceleague.adobe.com/docs/target-dev/developer/client-side/at-js-implementation/at-js/how-atjs-works.html?lang=fr" format="https" scope="external">Mise en œuvre d’at.jss</a>. </p> </td> 
   <td colname="col4"> <p>0.9.1 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Versions minimales des SDK pour Android et iOS {#section-73b2446fba8e463888642c7d7dfd94f1}

Au minimum, le service d’ID requiert les versions du SDK répertoriées ci-dessous.

* Android : 4.11.0
* iOS : 4.11.0

>[!TIP]
>
>Nous vous recommandons d’utiliser les dernières versions du code plutôt que la version minimale requise.

Le code de votre SDK doit être activé pour le service d’ID. Activez et téléchargez le dernier code du SDK pour chaque application depuis votre compte [Adobe Mobile Services](https://mobilemarketing.adobe.com/). Voir également :

* [Configuration des options du SDK Service d’ID des visiteurs](https://experienceleague.adobe.com/docs/mobile-services/using/manage-app-settings-ug/configuring-app/t-config-visitor.html?lang=fr)
* [Méthodes du SDK Android](https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/c-marketing-cloud.html?lang=fr)
* [Méthodes du SDK iOS](https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/marketing-cloud.html?lang=fr)

>[!MORELIKETHIS]
>
>* [Bibliothèque de code](../library/library.md#concept-ff27497375644a898d47984aefb21c97)

