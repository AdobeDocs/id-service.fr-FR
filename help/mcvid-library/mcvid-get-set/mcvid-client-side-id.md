---
description: Appelez cette fonction du service d’ID pour déterminer s’il a généré un identifiant visiteur Experience Cloud (MID) côté client. Disponible dans VisitorAPI.js 1.7.0 ou version ultérieure.
keywords: Service d’identification
seo-description: Appelez cette fonction du service d’ID pour déterminer s’il a généré un identifiant visiteur Experience Cloud (MID) côté client. Disponible dans VisitorAPI.js 1.7.0 ou version ultérieure.
seo-title: isClientSideMarketingCloudVisitorID
title: isClientSideMarketingCloudVisitorID
uuid: 1 c 39 ac 60-1 d 2 b -4 ed 4-a 2 ea -30 d 680 e 61 e 10
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

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

