---
description: 'Le service Experience Cloud ID fournit un identifiant universel et permanent qui identifie vos visiteurs à l’échelle de toutes les solutions Experience Cloud. '
keywords: Service d’identification
seo-description: Le service Adobe Experience Cloud ID fournit un identifiant permanent et permanent qui identifie vos visiteurs pour toutes les solutions dans Experience Cloud. Il peut remplacer le code de génération des identifiants pour des services tels que Analytics, Audience Manager, Target et d’autres solutions ou fonctionnalités d’Experience Cloud.
seo-title: Service Experience Cloud ID
title: Service Experience Cloud ID
uuid: b 68194 b 5-e 549-4 f 6 f-bfaf -7744926 aeaac
translation-type: tm+mt
source-git-commit: cce8f5559baa0598fedaccf2fece6ec90cb641b7

---


# Service Experience Cloud ID {#experience-cloud-id-service}

Le service Experience Cloud ID (service d’ID) fournit un identifiant universel et permanent qui identifie vos visiteurs à l’échelle de toutes les solutions Experience Cloud. Il peut remplacer le code de génération des identifiants pour des services tels que Analytics, Audience Manager, Target et d’autres solutions ou fonctionnalités d’Experience Cloud.

<table id="table_5E612F746A704FE095B809A013EE977F" class="simpletable"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Prise en main</b> </p> <p> 
     <ul id="ul_D5EC6A54A03F4AB595B588116A7C1296"> 
      <li id="li_845F6DE25A1241439BCDCBC00459D7EB"> <a href="mcvid-introduction/mcvid-overview.md" format="dita" scope="local"> Aperçu </a> </li> 
      <li id="li_47F399E1D4AF4F08BD647DF01A423BA7"> <a href="mcvid-reference/mcvid-requirements.md" format="dita" scope="local"> Conditions requises pour le service Experience Cloud ID </a> </li> 
      <li id="li_CBEEE79B45644F28A52B58DDF23DAD4F"> <a href="mcvid-implementation-guides/mcvid-standard.md#concept-89cd0199a9634fc48644f2d61e3d2445" format="dita" scope="local">Mise en œuvre standard avec la gestion dynamique des balises (DTM)</a> </li> 
     </ul> </p> <p><b>Bibliothèques JavaScript d’Experience Cloud ID</b> </p> <p>Les ressources JavaScript pour le service Experience Cloud ID se situent à l’adresse : <a href="https://github.com/Adobe-Marketing-Cloud/id-service/releases" format="https" scope="external">https://github.com/Adobe-Marketing-Cloud/id-service/releases</a>. </p> <p> <b>Éléments nouveaux ou en vedette</b> </p> <p> 
     <ul id="ul_B0A25B6827734D55BB1E20D12334AC21"> 
      <li id="li_A66924F4948F4A5ABA545A89A28A6F6A"><a href="mcvid-implementation-guides/opt-in-service/mcvid-optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> Service Opt-in</a> </li> 
      <li id="li_92D49CB788AD478EA74BCF5328CB9A14"> <a href="mcvid-library/mcvid-get-set/mcvid-getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues </a> </li> 
      <li id="li_9E512C6DD15C46C3ABD06ACD60D97E4A"> <a href="mcvid-faq-intro/ecid-faq-intro.md" format="dita" scope="local"> Questions fréquentes </a> </li> 
      <li id="li_B28082F3D075413D89E5AFB718657E17"> <a href="mcvid-library/mcvid-function-vars/mcvid-coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local"> isCoopSafe </a> </li> 
      <li id="li_7744A4898EA542B9BF009D2066810050"> <a href="mcvid-library/mcvid-function-vars/mcvid-idsyncontainerid.md#reference-5cfbed2240fa4def90f535f017a36015" format="dita" scope="local"> idSyncContainerID </a> </li> 
     </ul> </p> 
    <draft-comment> 
     <p> <b>Annonces :</b> </p> 
     <p> <p>Important : La prise en charge du service d'ID pour Internet Explorer 6, 7 et 8 est abandonnée et sera interrompue dans une version ultérieure. </p> </p> 
    </draft-comment> </td> 
   <td colname="col2"> <p> <b>Notes de mise à jour</b> </p> <p><b>La version 4.0</b> du 12 février 2019 comprend le service <a href="mcvid-implementation-guides/opt-in-service/mcvid-optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> de souscription</a> utilisé pour déterminer si vous pouvez placer un cookie sur le périphérique ou le navigateur d'un utilisateur lors de la visite de votre site. </p> <p>La version du 18 janvier 2018 inclut la mise à jour JavaScript 3.0.0 ainsi que les mises à jour des méthodes API. Voir <a href="mcvid-library/mcvid-function-vars/mcvid-disableidsync.md#reference-589d6b489ac64eddb5a7ff758945e414" format="dita" scope="local"> Disableidsyncs</a> et <a href="mcvid-library/mcvid-function-vars/mcvid-disable-cookies.md#reference-2dd2d60d12f34f0b98bbb5606b3734cc" format="dita" scope="local"> disablethirdpartycookies</a>. </p> 
    <draft-comment> 
     <p>La version d'octobre 2017 n'inclut pas de modifications ou de mises à jour du code pour le service d'ID. Le code du service d'ID reste inchangé à la v 2.5. </p> 
    </draft-comment> 
    <draft-comment> 
     <p> La version de septembre 2017 incrémente le code du service d'ID à la version 2.5. </p> 
    </draft-comment> <p> 
     <ul id="ul_4F06F170F214492780C7D25A069F799F"> 
      <li id="li_45A7CD556FE44F4DAB035C736A058F36"> Pour connaître les nouvelles fonctionnalités et les correctifs, voir les dernières <a href="https://marketing.adobe.com/resources/help/en_US/whatsnew/" format="https" scope="external">notes de mises à jour d’Experience Cloud</a>. </li> 
      <li id="li_10CC4FBFEFC947CA9AD15F52D9715257">Pour lire les anciennes notes de mise à jour, voir les <a href="https://marketing-stage.adobe.com/resources/help/en_US/whatsnew/c_legacy_releases.html" format="html" scope="external">notes de mise à jour précédentes</a>. </li> 
     </ul> </p> <p> <b>Ressources d’Experience Cloud</b> </p> <p> 
     <ul id="ul_E30EC96BDC624B5591F0470D430B7F41"> 
      <li id="li_F3A5CCFAE0F247CEB41A03CA8E03106B"> <a href="http://www.adobe.com/privacy.html" format="http" scope="external"> Centre de traitement des données personnelles Adobe</a> </li> 
      <li id="li_A54C1EB170EA4B8FA6A81B90AB0C39DD"> <a href="http://www.adobe.com/marketing-cloud.html" scope="external" format="http"> Adobe Experience Cloud</a> </li> 
      <li id="li_1938F7044F544481A6CC0F45CC22B80A"> <a href="http://helpx.adobe.com/learning.html?promoid=KAUDK" scope="external" format="http"> Formations et didacticiels Adobe</a> </li> 
      <li id="li_C71459E0D1464C05B8B9387C43541F17"> <a href="https://marketing.adobe.com/resources/help/en_US/home/index.html" scope="external" format="https"> Page d’accueil de la documentation du produit</a> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
