---
description: Consultez cette section pour vous assurer que vous utilisez les solutions, services et versions de code adéquats requis par le service d’identification des visiteurs.
keywords: Service d’identification des visiteurs
title: Conditions requises pour le service d’identification des visiteurs Adobe
exl-id: ebeac4c7-b36c-4a4e-9378-351fac5baf53
TQID: https://experienceleague.adobe.com/yOoLEIKihVSpDLeZsplTZzg-toOENKlBzsQt2G2YcKk
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 727
ht-degree: 39%

---

# Conditions requises pour le service d’identification des visiteurs Adobe {#requirements-for-the-experience-cloud-id-service}

Consultez cette section pour vous assurer que vous utilisez les solutions, services et versions de code adéquats requis par le service d’identification des visiteurs.

## Les conditions requises assurent le succès et la prise en charge de la mise en œuvre {#section-15e54a9e9ad2443cb9dc950b4a78f1f1}

Une implémentation réussie et prise en charge répond aux exigences du code (ou les dépasse) et suit les instructions telles qu’elles apparaissent dans l’aide d’Adobe. Une implémentation non prise en charge provoquera des résultats inattendus et empêchera l’assistance clientèle et nos équipes d’ingénieurs de vous aider à résoudre les problèmes liés au service d’identification des visiteurs.

### Implémentations standard

Voir [balises](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=fr) dans Collecte de données Adobe Experience Platform pour votre implémentation standard.

### Implémentations non standard

Pour les implémentations manuelles ou non standard, vous devez configurer le service d’identification des visiteurs comme décrit par les procédures dans ce guide. Comme pour les instructions d’implémentation standard ci-dessus, un placement et un chargement de code incorrects créeront une implémentation non prise en charge.

## Exigences des entreprises CX : ID d’organisation IMS {#section-a02f537129a64ffbb690d5738d360c26}

Pour utiliser le service d’identification des visiteurs, votre entreprise doit être activée pour CX Enterprise et disposer d’un identifiant d’organisation IMS. Vérifiez la liste suivante si vous n’êtes pas sûr du statut CX Enterprise de votre société et si vous devez trouver votre ID d’organisation IMS.

>[!IMPORTANT]
>
>L’ID d’organisation IMS est sensible à la casse et doit être utilisé exactement comme indiqué.

<table id="table_6C74B676EB094C568D2439FDCC9A7830"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Statut Entreprise CX </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Activé</b> </p> </td> 
   <td colname="col2"> <p>Si votre société est activée pour CX Enterprise, mais que vous ne disposez pas de votre identifiant d’organisation IMS, reportez-vous à <a href="https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html?lang=fr" format="https" scope="external"> identifiants d’organisation</a> (faites défiler l’écran jusqu’à la section <i>Rechercher votre identifiant d’organisation</i>). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Pas sûr</b> </p> </td> 
   <td colname="col2"> <p> Si vous ne connaissez pas le statut d’entreprise CX de votre société, demandez à la personne qui gère votre compte Adobe si les membres de votre société peuvent se connecter à <a href="https://experiencecloud.adobe.com" format="https" scope="external"> marketing.adobe.com</a> à l’aide d’une Adobe ID. Si vous le pouvez, vous êtes activé et un administrateur peut afficher votre ID d’organisation IMS. Pour trouver l’ID d’organisation IMS, consultez la section « Page d’administration » dans <a href="https://experienceleague.adobe.com/docs/core-services/interface/experience-cloud.html?lang=fr" format="https" scope="external"> Administration d’entreprise CX</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Pas activé</b> </p> </td> 
   <td colname="col2"> <p> Si votre société n’est pas activée pour CX Enterprise, reportez-vous à <a href="https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html?lang=fr" format="https" scope="external"> Services principaux - Activation de vos solutions</a> pour commencer. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Conditions requises pour Analytics : collecte des données régionale {#section-7d04bb013bc84a25bae3b148bc0ca25f}

Tous les serveurs de suivi ont été convertis en RDC ; il n’est donc pas nécessaire de modifier le serveur de suivi Analytics. [Plus d’informations...](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html?lang=fr)

## Bibliothèques de code et versions minimales requises {#section-ad7542a4317d430fa79fc6b095beb84d}

Les sections suivantes répertorient les versions de code minimales requises pour utiliser le service d’identification des visiteurs.

>[!TIP]
>
>Nous vous recommandons d’utiliser les dernières versions du code plutôt que la version minimale requise.

**JavaScript**

<table id="table_8E773F76DBCB4797A0C117080CA8707C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Solution d’entreprise CX </th> 
   <th colname="col3" class="entry"> Bibliothèque de code </th> 
   <th colname="col4" class="entry"> Version requise </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b> Service d’identification des visiteurs </b> </p> </td> 
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
   <td colname="col4"> <p>H.27 </p> <p> <p>Remarque : <span class="keyword"> Analytics</span> s_code version H.27 n’est plus pris en charge avec la version 1.6.0 du service d’identification des visiteurs. Mettez à niveau votre code vers la dernière version d’AppMeasurement. </p> </p> </td> 
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
   <td colname="col3"> <p> <span class="codeph"> mbox.js</span> </p> <p>Voir <a href="https://experienceleague.adobe.com/fr/docs/target-dev/developer/client-side/at-js-implementation/at-js/overview" format="https" scope="external">Code mbox</a>. </p> </td> 
   <td colname="col4"> <p>61 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> at.js</span> </p> <p>Voir <a href="https://experienceleague.adobe.com/fr/docs/target-dev/developer/client-side/at-js-implementation/at-js/how-atjs-works" format="https" scope="external">Mise en œuvre d’at.jss</a>. </p> </td> 
   <td colname="col4"> <p>0.9.1 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Versions minimales des SDK pour Android et iOS {#section-73b2446fba8e463888642c7d7dfd94f1}

Le service d’identification des visiteurs nécessite au minimum les versions de SDK répertoriées ci-dessous.

* Android : 4.11.0
* iOS : 4.11.0

>[!TIP]
>
>Nous vous recommandons d’utiliser les dernières versions du code plutôt que la version minimale requise.

Votre code SDK doit être activé pour le service d’identification des visiteurs. Activez et téléchargez le dernier code du SDK pour chaque application depuis votre compte [Adobe Mobile Services](https://mobilemarketing.adobe.com/). Voir également :

* [Configuration des options du SDK Service d’ID des visiteurs](https://experienceleague.adobe.com/docs/mobile-services/using/manage-app-settings-ug/configuring-app/t-config-visitor.html?lang=fr)
* [Méthodes du SDK Android](https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/c-marketing-cloud.html?lang=fr)
* [Méthodes de SDK iOS](https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/marketing-cloud.html?lang=fr)

>[!MORELIKETHIS]
>
>* [Bibliothèque de code](../library/library.md#concept-ff27497375644a898d47984aefb21c97)
