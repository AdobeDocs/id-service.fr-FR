---
description: 'Le service Experience Cloud Identity fournit un identifiant universel et permanent qui identifie vos visiteurs à l’échelle de toutes les solutions Experience Cloud. '
keywords: ID Service
seo-description: Le service Adobe Experience Cloud Identity (service d’ID) fournit un identifiant universel et permanent qui identifie vos visiteurs à l’échelle de toutes les solutions Experience Cloud. Il peut remplacer le code de génération des identifiants pour des services tels qu’Analytics, Audience Manager, Target et d’autres solutions ou fonctionnalités d’Experience Cloud.
seo-title: Service Experience Cloud Identity
title: Service Experience Cloud Identity
uuid: b68194b5-e549-4f6f-bfaf-7744926aeaac
translation-type: ht
source-git-commit: 6e77622817d9881efd9039d9073ba4ae14e8e14e
workflow-type: ht
source-wordcount: '303'
ht-degree: 100%

---


# Service Adobe Experience Cloud Identity {#experience-cloud-id-service}

Le service Adobe Experience Cloud Identity (service d’ID) fournit un identifiant universel et permanent qui identifie vos visiteurs à l’échelle de toutes les solutions Experience Cloud. Il peut remplacer le code de génération des identifiants pour des services tels qu’Analytics, Audience Manager, Target et d’autres solutions ou fonctionnalités d’Experience Cloud.

<table id="table_5E612F746A704FE095B809A013EE977F" class="simpletable"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Prise en main</b> </p> <p> 
     <ul id="ul_D5EC6A54A03F4AB595B588116A7C1296"> 
      <li id="li_845F6DE25A1241439BCDCBC00459D7EB"> <a href="introduction/overview.md" format="dita" scope="local"> Aperçu </a> </li> 
      <li id="li_47F399E1D4AF4F08BD647DF01A423BA7"> <a href="reference/requirements.md" format="dita" scope="local"> Conditions requises pour le service Experience Cloud Identity </a> </li> 
      <li id="li_CBEEE79B45644F28A52B58DDF23DAD4F"> <a href="implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445" format="dita" scope="local"> Mise en œuvre standard avec la gestion dynamique des balises (DTM)</a> </li> 
     </ul> </p> <p><b>Bibliothèques JavaScript d’Experience Cloud ID</b> </p> <p>Les ressources JavaScript pour le service Experience Cloud Identity se situent à l’adresse : <a href="https://github.com/Adobe-Marketing-Cloud/id-service/releases" format="https" scope="external">https://github.com/Adobe-Marketing-Cloud/id-service/releases</a>. </p> <p> <b>Éléments nouveaux ou en vedette</b> </p> <p> 
     <ul id="ul_B0A25B6827734D55BB1E20D12334AC21"> 
      <li id="li_A66924F4948F4A5ABA545A89A28A6F6A"><a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> Service Opt-in</a> </li> 
      <li id="li_92D49CB788AD478EA74BCF5328CB9A14"> <a href="library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues </a> </li> 
      <li id="li_9E512C6DD15C46C3ABD06ACD60D97E4A"> <a href="faq-intro/faq-intro.md" format="dita" scope="local"> Questions fréquentes </a> </li> 
      <li id="li_B28082F3D075413D89E5AFB718657E17"> <a href="library/function-vars/coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local"> isCoopSafe </a> </li> 
      <li id="li_7744A4898EA542B9BF009D2066810050"> <a href="library/function-vars/idsyncontainerid.md#reference-5cfbed2240fa4def90f535f017a36015" format="dita" scope="local"> idSyncContainerID </a> </li> 
     </ul> </p> 
     <!-- 
     <p> <b>Announcements:</b> </p> 
     <p> <p>Important:  ID service support for Internet Explorer 6, 7, and 8 is deprecated and will be discontinued in a future release. </p> </p> 
     --> </td> 
   <td colname="col2"> <p> <b>Notes de mise à jour</b> </p> <p><b>La version 4.4</b> du 17 juillet 2019 comprend la prise en charge de <a href="reference/hashing-support.md" format="dita" scope="local"> l’algorithme de hachage SHA-256</a> qui vous permet de transmettre des ID de client ou des adresses électroniques, et transmet des identifiants hachés.</p><p><b>La version 4.0</b> du 12 février 2019 comprend le <a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> service Opt-in</a> utilisé pour déterminer si vous pouvez placer un cookie sur le périphérique ou le navigateur d’un utilisateur lors de sa visite sur votre site. </p> <p> 
     <ul id="ul_4F06F170F214492780C7D25A069F799F"> 
      <li id="li_45A7CD556FE44F4DAB035C736A058F36"> Pour connaître les nouvelles fonctionnalités et les correctifs, voir les dernières <a href="https://docs.adobe.com/content/help/fr-FR/release-notes/experience-cloud/current.html" format="https" scope="external">notes de mises à jour d’Experience Cloud</a>. </li> 
      <li id="li_10CC4FBFEFC947CA9AD15F52D9715257">Pour lire les anciennes notes de mise à jour, voir la section <a href="https://docs.adobe.com/content/help/fr-FR/release-notes/experience-cloud/current.html" format="html" scope="external">notes de mise à jour précédentes</a>. </li> 
     </ul> </p> <p> <b>Ressources d’Experience Cloud</b> </p> <p> 
     <ul id="ul_E30EC96BDC624B5591F0470D430B7F41"> 
      <li id="li_F3A5CCFAE0F247CEB41A03CA8E03106B"> <a href="http://www.adobe.com/fr/privacy.html" format="http" scope="external"> Centre de traitement des données personnelles Adobe</a> </li> 
      <li id="li_A54C1EB170EA4B8FA6A81B90AB0C39DD"> <a href="https://docs.adobe.com/content/help/fr-FR/experience-cloud/user-guides/home.html" scope="external" format="http"> Adobe Experience Cloud</a> </li> 
      <li id="li_1938F7044F544481A6CC0F45CC22B80A"> <a href="http://helpx.adobe.com/fr/learning.html?promoid=KAUDK" scope="external" format="http"> Formations et didacticiels Adobe</a> </li> 
      <li id="li_C71459E0D1464C05B8B9387C43541F17"> <a href="https://helpx.adobe.com/fr/support/experience-cloud.html" scope="external" format="https"> Page d’accueil de la documentation du produit</a> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

