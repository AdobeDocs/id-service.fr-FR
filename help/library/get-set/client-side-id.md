---
description: Appelez cette fonction du service d’ID pour déterminer si le service d’ID a généré un ID de visiteur Experience Cloud (MID) côté client. Disponible dans VisitorAPI.js 1.7.0 ou version ultérieure.
keywords: Service d’ID
title: isClientSideMarketingCloudVisitorID
exl-id: ed2672e7-da1a-4c02-9f4e-c14419ec9ec7
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 100%

---

# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}

Appelez cette fonction du service d’ID pour déterminer si le service d’ID a généré un ID de visiteur Experience Cloud (MID) côté client. Disponible dans VisitorAPI.js 1.7.0 ou version ultérieure.

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
