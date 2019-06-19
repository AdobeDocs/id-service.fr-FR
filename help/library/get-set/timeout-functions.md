---
description: Appelez ces fonctions du service d'ID pour déterminer le délai d'expiration pour une demande d'identifiant de plateforme Experience Platform, Analytics ou Audience Manager. Disponible dans VisitorAPI.js 1.7.0 ou version ultérieure.
keywords: Service d’identification
seo-description: Appelez ces fonctions du service d'ID pour déterminer le délai d'expiration pour une demande d'identifiant de plateforme Experience Platform, Analytics ou Audience Manager. Disponible dans VisitorAPI.js 1.7.0 ou version ultérieure.
seo-title: Méthodes callTimeOut
title: Méthodes callTimeOut
uuid: e 5047498-11 db -4945-b 356-c 92 b 7 d 447573
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Méthodes callTimeOut{#calltimeout-methods}

Appelez ces fonctions du service d&#39;ID pour déterminer le délai d&#39;expiration pour une demande d&#39;identifiant de plateforme Experience Platform, Analytics ou Audience Manager. Disponible dans VisitorAPI.js 1.7.0 ou version ultérieure.

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
   <td colname="col1"> <p>Service d'identité de Platform Platform </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variablename</span> = visitor. mcidcalltimedout ()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Analytics</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variablename</span> = visitor. analyticsidcalltimedout ()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Audience Manager</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variablename</span> = visitor. aamidcalltimedout ()</span> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Réponse de la fonction {#section-ff73aaca58b74e10a0953c49a3387160}

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

