---
description: Appelez cette fonction du service d’identification des visiteurs pour déterminer si le service d’identification des visiteurs a généré un ECID (MID) côté client. Disponible dans VisitorAPI.js 1.7.0 ou version ultérieure.
keywords: Service d’identification des visiteurs
title: isClientSideMarketingCloudVisitorID
exl-id: ed2672e7-da1a-4c02-9f4e-c14419ec9ec7
TQID: https://experienceleague.adobe.com/kQK7Lw-j33luPqTSzQKGuf8fMPuOEDoQBzesZa-bvVo
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 128
ht-degree: 32%

---

# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}

Appelez cette fonction du service d’identification des visiteurs pour déterminer si le service d’identification des visiteurs a généré un ECID (MID) côté client. Disponible dans `VisitorAPI.js` version 1.7.0 ou ultérieure.

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
   <td colname="col2"> <p>Le service d'identification des visiteurs n'a pas pu ou n'a pas reçu de MID du serveur CX Enterprise. Il a créé un MID local, dans le navigateur (côté client). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> false</span> </p> </td> 
   <td colname="col2"> <p>Le service d’identification des visiteurs a reçu un MID du serveur CX Enterprise. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> null</span> </p> </td> 
   <td colname="col2"> <p>Le service d'identification des visiteurs n'a pas effectué d'appel au serveur CX Enterprise. </p> </td> 
  </tr> 
 </tbody> 
</table>

