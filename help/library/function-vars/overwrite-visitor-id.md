---
description: Cette propriété remplace un Experience Cloud visiteur et les identifiants Analytics lorsqu’ils naviguent d’un domaine à un autre. Pour remplacer un ID, vous devez posséder et avoir mis en oeuvre le service d’ID sur chaque domaine. Ce code ne vous permet pas de remplacer les ID sur les domaines que vous ne contrôlez pas.
keywords: ID Service
seo-description: Cette propriété remplace un Experience Cloud visiteur et les identifiants Analytics lorsqu’ils naviguent d’un domaine à un autre. Pour remplacer un ID, vous devez posséder et avoir mis en oeuvre le service d’ID sur chaque domaine. Ce code ne vous permet pas de remplacer les ID sur les domaines que vous ne contrôlez pas.
seo-title: overwriteCrossDomainMCIDAndAID
title: overwriteCrossDomainMCIDAndAID
uuid: 8e48127a-ac62-4ea0-9756-2a27b20ecbcf
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 19%

---


# overwriteCrossDomainMCIDAndAID{#overwritecrossdomainmcidandaid}

Cette propriété remplace un Experience Cloud visiteur et les identifiants Analytics lorsqu’ils naviguent d’un domaine à un autre. Pour remplacer un ID, vous devez posséder et avoir mis en oeuvre le service d’ID sur chaque domaine. Ce code ne vous permet pas de remplacer les ID sur les domaines que vous ne contrôlez pas.

**Syntaxe :** `Visitor.overwriteCrossDomainMCIDAndAID: true|false` (la valeur par défaut est `false`)

**Exemple de code**

Votre code JavaScript peut ressembler à l’exemple suivant.

```js
//Call the ID service 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE", { 
     ... 
 
     //Set overwrite property 
     overwriteCrossDomainMCIDAndAID: true 
}); 
```

**Cas d’utilisation**

Pour effectuer le suivi des visiteurs d’un site, le service d’ID écrit un [!DNL Experience Cloud] ID (ou MID) sur un cookie du navigateur. Le tableau suivant liste et décrit les cas d’utilisation courants où vous pouvez vouloir remplacer un MID existant défini par le service d’ID dans un autre domaine.

<table id="table_FC1AF6551D6646E0BF1C4FB7C1316EBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Exemple d’utilisation </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Identification des visiteurs sur différents landings page de domaine</b> </p> </td> 
   <td colname="col2"> <p>Imaginons que vous possédiez les domaines A et B. Dans ce cas, vous pouvez définir <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> lorsque : </p> <p> 
     <ul id="ul_FB4704BFE7134F1688E34BF1A36627B7"> 
      <li id="li_FF71FD1FB9DD4702B675A140FAD2B481">Chaque domaine a son propre landing page. </li> 
      <li id="li_78F75469D32D473B93148B46D35E67F1">Un cookie (et un MID) ont déjà été définis pour un visiteur lors d’une précédente visite du domaine B. </li> 
      <li id="li_305CE5138EEB43D3BF9CE38D1E7FFA04">Vous souhaitez identifier de manière cohérente un visiteur s’il arrive au domaine B à partir du domaine A. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Identification des visiteurs sur les pages d'entrée et de conversion</b> </p> </td> 
   <td colname="col2"> <p>Imaginons que vous possédiez les domaines A et B. Dans ce cas, vous pouvez définir <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> lorsque : </p> 
    <ul id="ul_7BEBFD523A2F47AFB6963536E43692D0"> 
     <li id="li_71586080489340E2A6C0B263F231E3DE">Le domaine A est un landing page. </li> 
     <li id="li_4E3D3CB380EE4F1BAC4CD752194AE8DE">Le domaine B est une page distincte de conversion, de réservation ou d’autre page de fin de processus. </li> 
     <li id="li_FB393B16CFAC4D2D9B2328EBA4573C1A">Un cookie (et un MID) ont déjà été définis pour un visiteur lors d’une précédente visite du domaine B et vous savez qu’il s’agit de MID côté client moins souhaitables que de MID côté serveur. </li> 
     <li id="li_36FC138530A4476A995C0F9FD73C41DE">Vous souhaitez identifier de manière cohérente un visiteur s’il arrive au domaine B à partir du domaine A. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Identification des visiteurs des applications mobiles aux navigateurs Web</b> </p> </td> 
   <td colname="col2"> <p>Ce cas d’utilisation est légèrement différent. Il s’agit d’identifier les utilisateurs qui passent d’une application mobile à votre site Web. Dans ce cas, votre visiteur dispose déjà d’un MID défini localement par une application mobile et d’un MID différent défini dans un cookie sur votre site Web. Vous pouvez définir <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> de manière à remplacer le MID défini dans le cookie du navigateur par le MID défini dans l’application mobile. </p> </td> 
  </tr> 
 </tbody> 
</table>

