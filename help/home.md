---
description: Le service dʼidentités d’Experience Cloud active la structure d’identification courante pour les applications et services Experience Cloud. Il fonctionne en attribuant à un visiteur ou une visiteuse du site un identifiant persistant et unique, appelé Experience Cloud ID (ECID).
keywords: Service d’ID ; Service d’identités ; Experience Cloud Identity Service
title: Service d’identités d’Experience Cloud
exl-id: fe1368db-06ca-4c79-b655-b7064e316d74
source-git-commit: f7c25f5ebd0690c56c081422949eb34f1f277ae1
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 100%

---

# Service d’identités d’Adobe Experience Cloud {#experience-cloud-id-service}

Le service dʼidentités d’Experience Cloud active la structure d’identification courante pour les applications et services Experience Cloud. Il fonctionne en attribuant à un visiteur ou une visiteuse du site un identifiant persistant et unique, appelé Experience Cloud ID (ECID).

## Comprendre les principales entités identitaires

Pour mieux comprendre la façon unique dont Adobe identifie les visiteurs et visiteuses et résout les informations d’identité, lisez le résumé ci-dessous :

* **Experience Cloud Identity Service** : le service d’identités Experience Cloud Identity Service **est chargé de définir l’Experience Cloud ID (ECID)**. Pour plus d’informations, reportez-vous à la [Présentation du service d’identités d’Experience Cloud](./introduction/overview.md).
* **Experience Cloud ID (ECID)** : l’ECID est un espace de noms d’identité partagé utilisé dans les applications Adobe Experience Platform et Adobe Experience Cloud pour identifier les personnes et les appareils. Pour plus d’informations sur l’ECID, consultez la [Présentation de l’ECID](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html?lang=fr).
* **Experience Platform Identity Service** : le service d’identités Experience Platform Identity Service vous offre une vue d’ensemble complète de vos client(e)s et de leur comportement en rapprochant les identités sur les appareils et systèmes. Pour plus d’informations, reportez-vous à la [Présentation du service d’identités d’Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=fr).

<!-- The Adobe Experience Cloud Identity Service provides a universal, persistent ID that identifies your visitors across all the solutions in the Experience Cloud. It can replace ID generation code for Experience Cloud solutions and services. -->

<table id="table_5E612F746A704FE095B809A013EE977F" class="simpletable"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Prise en main</b> </p> <p> 
     <ul id="ul_D5EC6A54A03F4AB595B588116A7C1296"> 
      <li id="li_845F6DE25A1241439BCDCBC00459D7EB"> <a href="introduction/overview.md" format="dita" scope="local"> Aperçu </a> </li> 
      <li id="li_47F399E1D4AF4F08BD647DF01A423BA7"> <a href="reference/requirements.md" format="dita" scope="local"> Conditions requises pour le service d’identités d’Experience Cloud </a> </li> 
      <li id="li_CBEEE79B45644F28A52B58DDF23DAD4F"> <a href="https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=fr" format="html" scope="external"> Implémentation standard avec les balises Platform </a> </li> 
     </ul> </p> <p><b>Bibliothèques JavaScript d’Experience Cloud ID</b> </p> <p>Les ressources JavaScript pour le service d’identités d’Experience Cloud se situent à l’adresse : <a href="https://github.com/Adobe-Marketing-Cloud/id-service/releases" format="https" scope="external">https://github.com/Adobe-Marketing-Cloud/id-service/releases</a>. </p> <p> <b>Éléments nouveaux ou en vedette</b> </p> <p> 
     <ul id="ul_B0A25B6827734D55BB1E20D12334AC21"> 
      <li id="li_A66924F4948F4A5ABA545A89A28A6F6A"><a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> Service Opt-in</a> </li> 
      <li id="li_92D49CB788AD478EA74BCF5328CB9A14"> <a href="library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues </a> </li> 
      <li id="li_9E512C6DD15C46C3ABD06ACD60D97E4A"> <a href="faq-intro/faq-intro.md" format="dita" scope="local"> Questions fréquentes </a> </li> 
      <li id="li_7744A4898EA542B9BF009D2066810050"> <a href="library/function-vars/idsyncontainerid.md#reference-5cfbed2240fa4def90f535f017a36015" format="dita" scope="local"> idSyncContainerID </a> </li> 
     </ul> </p> 
     <!-- 
     <p> <b>Announcements:</b> </p> 
     <p> <p>Important:  ID service support for Internet Explorer 6, 7, and 8 is deprecated and will be discontinued in a future release. </p> </p> 
     --> </td> 
   <td colname="col2"> <p> <b>Notes de mise à jour</b> </p> <p><b>La version 4.4</b> du 17 juillet 2019 comprend la prise en charge de <a href="reference/hashing-support.md" format="dita" scope="local"> l’algorithme de hachage SHA-256</a> qui vous permet de transmettre des ID de client ou des adresses électroniques, et transmet des identifiants hachés.</p><p>La <b>version 4.0</b> du 12 février 2019 comprend le <a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local">service Opt-in</a> utilisé pour déterminer si vous pouvez placer un cookie sur l’appareil ou le navigateur d’un utilisateur lors de sa visite sur votre site. </p> <p> 
     <ul id="ul_4F06F170F214492780C7D25A069F799F"> 
      <li id="li_45A7CD556FE44F4DAB035C736A058F36"> Pour connaître les nouvelles fonctionnalités et les correctifs, voir les dernières <a href="https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=fr" format="https" scope="external">notes de mises à jour d’Experience Cloud</a>. </li> 
      <li id="li_10CC4FBFEFC947CA9AD15F52D9715257">Pour lire les anciennes notes de mise à jour, voir la section <a href="https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=fr" format="html" scope="external">notes de mise à jour précédentes</a>. </li> 
     </ul> </p> <p> <b>Ressources d’Experience Cloud</b> </p> <p> 
     <ul id="ul_E30EC96BDC624B5591F0470D430B7F41"> 
      <li id="li_F3A5CCFAE0F247CEB41A03CA8E03106B"> <a href="http://www.adobe.com/fr/privacy.html" format="http" scope="external"> Centre de traitement des données personnelles Adobe</a> </li> 
      <li id="li_A54C1EB170EA4B8FA6A81B90AB0C39DD"> <a href="https://experienceleague.adobe.com/docs/home.html?lang=fr" scope="external" format="http"> Adobe Experience Cloud</a> </li> 
      <li id="li_1938F7044F544481A6CC0F45CC22B80A"> <a href="http://helpx.adobe.com/fr/learning.html?promoid=KAUDK" scope="external" format="http"> Formations et didacticiels Adobe</a> </li> 
      <li id="li_C71459E0D1464C05B8B9387C43541F17"> <a href="https://helpx.adobe.com/fr/support/experience-cloud.html" scope="external" format="https"> Page d’accueil de la documentation du produit</a> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
