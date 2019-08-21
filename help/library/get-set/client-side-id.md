---
description: Appelez cette fonction du service d’ID pour déterminer s’il a généré un identifiant visiteur Experience Cloud (MID) côté client. Disponible dans VisitorAPI.js 1.7.0 ou version ultérieure.
keywords: Service d’identification
seo-description: Appelez cette fonction du service d’ID pour déterminer s’il a généré un identifiant visiteur Experience Cloud (MID) côté client. Disponible dans VisitorAPI.js 1.7.0 ou version ultérieure.
seo-title: isClientSideMarketingCloudVisitorID
title: isClientSideMarketingCloudVisitorID
uuid: 1c39ac60-1d2b-4ed4-a2ea-30d680e61e10
translation-type: ht
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}

Appelez cette fonction du service d’ID pour déterminer s’il a généré un identifiant visiteur Experience Cloud (MID) côté client. Disponible dans VisitorAPI.js 1.7.0 ou version ultérieure.

**Syntaxe**

`var *`variableName`* = visitor.isClientSideMarketingCloudVisitorID()`

Le tableau suivant répertorie et décrit les réponses renvoyées par cette fonction.

<table id="table_5D08A5DD6FD04F94818B0E8B790D3136"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Réponse </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> true</span> </p> </td> 
   <td colname="col2"> <p>Le service d’ID n’a pas pu recevoir ou n’a pas reçu un MID depuis le serveur <span class="keyword">Experience Cloud</span>. Il a créé un MID local, dans le navigateur (côté client). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> false</span> </p> </td> 
   <td colname="col2"> <p>Le service d’ID a reçu un MID depuis le serveur <span class="keyword">Experience Cloud</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> valeur nulle</span> </p> </td> 
   <td colname="col2"> <p>Le service d’ID n’a pas effectué d’appel au serveur <span class="keyword">Experience Cloud</span>. </p> </td> 
  </tr> 
 </tbody> 
</table>

