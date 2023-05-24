---
description: Appelez ces fonctions du service d’ID pour déterminer l’état du délai d’expiration pour une requête d’ID du service Experience Cloud Identity, d’Analytics ou d’Audience Manager. Disponible dans VisitorAPI.js 1.7.0 ou version ultérieure.
keywords: Service d’ID
title: Méthodes callTimeOut
exl-id: ff3a2c5e-a0a8-4257-b538-0e4ce454b4e8
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 100%

---

# Méthodes callTimeOut{#calltimeout-methods}

Appelez ces fonctions du service d’ID pour déterminer l’état du délai d’expiration pour une requête d’ID du service Experience Cloud Identity, d’Analytics ou d’Audience Manager. Disponible dans VisitorAPI.js 1.7.0 ou version ultérieure.

## Fonctions du délai d’expiration {#section-e08228ef5f9b45c9a84139bbb763164a}

<table id="table_B3ACE584B3224D838070D32A8462EF28"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Solution ou service </th> 
   <th colname="col2" class="entry"> Syntaxe de la fonction </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Service Experience Cloud Identity </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.MCIDCallTimedOut()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Analytics</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.AnalyticsIDCallTimedOut()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Audience Manager</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.AAMIDCallTimedOut()</span> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Réponses de la fonction {#section-ff73aaca58b74e10a0953c49a3387160}

<table id="table_5D08A5DD6FD04F94818B0E8B790D3136"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Réponse </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> TRUE</span> </p> </td> 
   <td colname="col2"> <p>Le service d’ID a envoyé une demande et la demande a expiré. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> FALSE</span> </p> </td> 
   <td colname="col2"> <p>Le service d’ID a envoyé une demande et a reçu une réponse positive du serveur. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> NULL</span> </p> </td> 
   <td colname="col2"> <p>Le service d’ID n’a pas envoyé de demande. </p> </td> 
  </tr> 
 </tbody> 
</table>
