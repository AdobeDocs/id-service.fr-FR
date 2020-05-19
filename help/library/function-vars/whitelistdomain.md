---
description: Ces configurations permettent à différentes instances du code du service d’ID implémentées dans un iFrame et sur la page parente de communiquer entre elles. Elles sont conçues pour aider à résoudre les problèmes liés à deux cas d’utilisation spécifiques où vous pouvez contrôler ou non la page/le domaine parent et où le code du service d’ID est chargé dans l’iFrame d’un domaine que vous contrôlez. Elles sont disponibles dans le code VisitorAPI.js version 2.2 ou ultérieure.
keywords: ID Service
seo-description: Ces configurations permettent à différentes instances du code du service d’ID implémentées dans un iFrame et sur la page parente de communiquer entre elles. Elles sont conçues pour aider à résoudre les problèmes liés à deux cas d’utilisation spécifiques où vous pouvez contrôler ou non la page/le domaine parent et où le code du service d’ID est chargé dans l’iFrame d’un domaine que vous contrôlez. Elles sont disponibles dans le code VisitorAPI.js version 2.2 ou ultérieure.
seo-title: whitelistParentDomain et whitelistIframeDomains
title: whitelistParentDomain et whitelistIframeDomains
uuid: 6b66a4d0-fea2-4d98-963e-0c4f4ab1efb6
translation-type: ht
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: ht
source-wordcount: '932'
ht-degree: 100%

---


# whitelistParentDomain et whitelistIframeDomains {#whitelistparentdomain-and-whitelistiframedomains}

Ces configurations permettent à différentes instances du code du service d’ID implémentées dans un iFrame et sur la page parente de communiquer entre elles. Elles sont conçues pour aider à résoudre les problèmes liés à deux cas d’utilisation spécifiques où vous pouvez contrôler ou non la page/le domaine parent et où le code du service d’ID est chargé dans l’iFrame d’un domaine que vous contrôlez. Elles sont disponibles dans le code VisitorAPI.js version 2.2 ou ultérieure.

Contenu :

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-f645198bbaba4fba8961acb6e88d1470" format="dita" scope="local"> Syntaxe </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-09d0049fe88a473baa69d404c50bf8ae" format="dita" scope="local"> Exemple de code </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-fc2eeb93546b406fae3b102dbcd11de7" format="dita" scope="local"> Cas d’utilisation </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2" format="dita" scope="local"> Sécurité des configurations </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-30c6a9f4dcdc4265a1149260b97cc057" format="dita" scope="local"> Méthodes API visiteur prises en charge </a> </li> 
</ul>

## Syntaxe {#section-f645198bbaba4fba8961acb6e88d1470}

Les deux éléments de configuration sont requis lorsque vous utilisez ce code.

<table id="table_237108A4D40F4AAC981D0060BA68F881"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Syntaxe de la configuration </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> whitelistParentDomain: " <span class="varname">Nom de domaine de la page parente</span>" </span> </p> </td> 
   <td colname="col2"> <p>Accepte un seul nom de domaine transmis en tant que chaîne. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> whitelistIframeDomains: [ <span class="varname"> "domaine iFrame","domaine iFrame","domaine iFrame" </span>] </span> </p> </td> 
   <td colname="col2"> <p>Accepte un ou plusieurs noms de domaine iFrame transmis en tant que tableau. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Exemple de code {#section-09d0049fe88a473baa69d404c50bf8ae}

Le code du [!UICONTROL service d’ID] que vous avez configuré pourrait ressembler à cet exemple.

```js
//Instantiate Visitor 
var visitor = Visitor.getInstance("Insert Experience Cloud Organization ID here",{ 
 ... 
 //Add parent page domain name and iFrame domain names 
 whitelistParentDomain: "parentpageA.com", 
 whitelistIframeDomains: ["iFrameDomain1.com","iFrameDomain2.com"], 
 ... 
 } 
);
```

## Cas d’utilisation {#section-fc2eeb93546b406fae3b102dbcd11de7}

Ces configurations permettent de résoudre le problème de définition d’un cookie du service d’ID et d’attribution d’un ID de visiteur lorsque les navigateurs bloquent les cookies tiers et si l’une des conditions suivantes s’applique :

* Vous contrôlez ou ne contrôlez pas la page/domaine parent.
* Le code du service d’ID n’est pas installé sur la page parente, mais est implémenté dans un iFrame.

>[!TIP]
>
>Vous pouvez également mettre en œuvre ces configurations lorsque vous diffusez de la vidéo dans un iFrame avec [Video Heartbeat](https://docs.adobe.com/content/help/fr-FR/media-analytics/using/media-overview.html). Video Heartbeat a besoin d’un service d’ID (le MID) pour fonctionner correctement.

**Exemple d’utilisation 1 : Le navigateur bloque les cookies tiers et le service d’ID est implémenté sur l’iFrame et la page parente.**

<table id="table_B479AA96DBE64685A253A6DF98D81B31"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Elément d’exemple d’utilisation </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Conditions</b> </p> </td> 
   <td colname="col2"> <p>Cet exemple d’utilisation comprend les conditions suivantes : </p> <p> 
     <ul id="ul_DC748846585745B0AB74398D82BDA53A"> 
      <li id="li_6E04CF0B6A204B4D8856656B0C9EF2A5">La Société A met en œuvre le service d’ID sur leur page d’accueil. </li> 
      <li id="li_B53AE0F0C69844E7B6C4D3464C57883B">La Société A met en œuvre le service d’ID dans iFrame sur leur page d’accueil. </li> 
      <li id="li_07E0A6D7BEB140E4B9FB6C7B9629B860">La Société A possède la page parente et l’iFrame et a mis en œuvre le service d’ID aux deux emplacements. </li> 
      <li id="li_76967BD69DDB40A8A9C915DADC58AC62">Un client charge la page parente dans un navigateur qui bloque les cookies tiers. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Résultats</b> </p> </td> 
   <td colname="col2"> <p>Dans ces conditions, le service d’ID : </p> <p> 
     <ul id="ul_12356701501E40DFA57903494FFE58F7"> 
      <li id="li_B57EDF1B0762486F95FA6526C047390C">Fonctionne correctement sur la page parente. Il demande et définit le cookie AMCV et affecte un identifiant unique au visiteur du site. </li> 
      <li id="li_BA9F42C759E747EAAE14DD3FBB6130A5">Ne fonctionne pas dans l’iFrame. En effet, le navigateur considère l’iFrame comme un domaine tiers et empêche le service d’ID de définir le cookie AMCV. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Solution</b> </p> </td> 
   <td colname="col2"> <p>Modifiez la fonction <span class="codeph">Visitor.getInstance</span> du service d’ID dans l’iFrame avec les configurations de liste blanche. Spécifiez les domaines parent et enfant dans le code. Ces configurations permettent au code du service d’ID de l’iFrame de vérifier le code du service d’ID sur la page parente pour un ID de visiteur. </p> <p>Si le code du service d’ID de l’iFrame ne reçoit pas de page parente de réponse, ces configurations génèrent un identifiant de visiteur local. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Exemple d’utilisation 2 : Demande d’un identifiant à partir d’un iFrame incorporé dans une page parente que vous ne contrôlez pas ou qui n’utilise pas le service d’ID**

<table id="table_1F21710F9D5F493BA6BA5974F2966DF4"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Elément d’exemple d’utilisation </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Conditions</b> </p> </td> 
   <td colname="col2"> <p>Cet exemple d’utilisation comprend les conditions suivantes : </p> <p> 
     <ul id="ul_356E8FB0B1D14F46A844FE5281967E28"> 
      <li id="li_1285D945361842268B46FB492A3B5AA5">La Société A n’utilise pas le service d’ID. </li> 
      <li id="li_880D6D473F8342FF9BB49FCE111FD61A">La Société A charge un iFrame sur la page. Cet iFrame appartient à la Société B et est chargé dans un domaine distinct de la Société A. </li> 
      <li id="li_7988F0272B094FE0B398006AD4E6F81B">Le navigateur bloque les cookies tiers. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Résultats</b> </p> </td> 
   <td colname="col2"> <p>Dans ces conditions, le service d’ID : </p> <p> 
     <ul id="ul_A92D90896E5A42C5804AC5CE83E8EB25"> 
      <li id="li_9734EA9C5D9D4F908DE783188C9E5530">Ne fonctionne pas dans l’iFrame. En effet, le navigateur considère l’iFrame comme un domaine tiers et empêche le service d’ID de définir le cookie AMCV. </li> 
      <li id="li_3F4BE9048E774902A867D67E5A80674D">Impossible d’obtenir un ID de visiteur à partir de la page parente, car la Société A n’utilise pas ce service. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Solution</b> </p> </td> 
   <td colname="col2"> <p>Modifiez la fonction <span class="codeph">Visitor.getInstance</span> du service d’ID dans l’iFrame avec les configurations de liste blanche. Spécifiez les domaines parent et enfant dans le code. Ces configurations permettent au code du service d’ID de l’iFrame de vérifier le code du service d’ID sur la page parente pour un ID de visiteur. </p> <p>Si le code du service d’ID de l’iFrame ne reçoit pas de page parente de réponse, ces configurations génèrent un identifiant de visiteur local. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Sécurité des configurations {#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2}

Vous pouvez mettre en œuvre ces configurations en toute sécurité car :

* Le service d’ID implémenté sur le domaine parent et le domaine iFrame doivent utiliser le même ID d’organisation. Ces configurations de liste blanche ne fonctionneront pas lorsque les ID d’organisation sur le parent ou dans l’iFrame sont différents.
* Ces configurations communiquent uniquement avec le domaine et les iFrames spécifiés dans le code.
* La communication entre l’iFrame et la page parente suit un format spécifique. Si le service d’ID de la page parente ne reçoit pas de demande au format attendu, ce processus de partage échoue.

## Méthodes API visiteur prises en charge {#section-30c6a9f4dcdc4265a1149260b97cc057}

Le service d’ID prend en charge un ensemble limité de méthodes API publiques lorsque vous implémentez ces configurations de liste blanche. Les méthodes prises en charge varient en fonction des scénarios d’utilisation décrits ci-dessus.

<table id="table_0FF9E529FD1C43A8A3B2B0D789C8E83C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Exemple d’utilisation </th> 
   <th colname="col2" class="entry"> Méthodes prises en charge </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Cas 1</b> </p> </td> 
   <td colname="col2"> <p> 
     <ul id="ul_99FAC8608F4C4B39805EEAA6297DB771"> 
      <li id="li_B13F6C4119F44F17963794B1E2046B1F"> <span class="codeph"> getMarketingCloudID </span> </li> 
      <li id="li_9C1B5C00A17F467CAB7EFE5F0D040777"> <span class="codeph"> getAudienceManagerLocationHint </span> </li> 
      <li id="li_30D4608F4C3849659FCBA97D88A10F0C"> <span class="codeph"> getAudienceManagerBlob </span> </li> 
      <li id="li_BA359596C80147EEA89CABCE83F123CA"> <span class="codeph"> getSupplementalDataID </span> </li> 
      <li id="li_26774089B6854CD6A3216043B6EEA01B"> <span class="codeph"> getCustomerIDs </span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Cas 2</b> </p> </td> 
   <td colname="col2"> <p> 
     <ul id="ul_CCAD7E362E7F4DAB9D5C3E166EEE6BDD"> 
      <li id="li_1F0B006BAD044ECBA5604625DE411E84"> <span class="codeph"> getSupplementalDataID </span> </li> 
      <li id="li_C6022223C8314B9C923202207C7472EA"> <span class="codeph"> getMarketingCloudVisitorID </span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

