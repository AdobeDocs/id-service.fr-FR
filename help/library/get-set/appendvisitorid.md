---
description: Cette fonction permet de partager l’Experience Cloud ID d’un visiteur sur plusieurs domaines lorsque les navigateurs bloquent les cookies tiers. Pour utiliser cette fonction, vous devez avoir mis en œuvre le service d’ID et posséder les domaines source et de destination. Disponible dans VisitorAPI.js 1.7.0 ou version ultérieure.
keywords: Service d’ID
title: appendVisitorIDsTo (suivi interdomaines)
exl-id: 3e4f4e2c-e658-4124-bd0e-59c63127bdde
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: ht
source-wordcount: '400'
ht-degree: 100%

---

# appendVisitorIDsTo (suivi interdomaines){#appendvisitoridsto-cross-domain-tracking}

Cette fonction permet de partager l’Experience Cloud ID d’un visiteur sur plusieurs domaines lorsque les navigateurs bloquent les cookies tiers. Pour utiliser cette fonction, vous devez avoir mis en œuvre le service d’ID et posséder les domaines source et de destination. Disponible dans VisitorAPI.js 1.7.0 ou version ultérieure.

Contenu :

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> Suivi des visiteurs sur plusieurs domaines lorsque les navigateurs bloquent les cookies tiers </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> Ajout d’un exemple de code d’identifiant visiteur </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-168e313df6054af0a7e27b9fa0d69640" format="dita" scope="local"> Prise en charge de Dynamic Tag Management (DTM) et du SDK </a> </li> 
</ul>

## Suivre les visiteurs sur plusieurs domaines lorsque les navigateurs bloquent les cookies tiers {#section-7251d88befd440b4b79520e33c5aa44a}

Le service d’ID écrit un cookie propriétaire et tiers dans le navigateur lorsqu’une personne visite votre site (voir [Cookies et service d’identités Experience Cloud](../../introduction/cookies.md) ). Le cookie propriétaire contient le MID, un ID unique pour ce visiteur. Le cookie tiers contient un autre ID utilisé par le service d’ID pour générer le MID. Lorsqu’un navigateur bloque ce cookie tiers, le service d’ID ne peut pas :

* Régénérer l’ID unique de ce visiteur de site lorsqu’il accède à un autre domaine.
* Effectuer le suivi des visiteurs sur différents domaines appartenant à votre entreprise.

Pour résoudre ce problème, mettez en œuvre ` Visitor.appendVisitorIDsTo( *`l’URL`*)`. Cette propriété permet au service d’ID de suivre les visiteurs du site sur plusieurs domaines, même si leurs navigateurs bloquent les cookies tiers. Voici son fonctionnement :

* Lorsqu’un visiteur navigue sur vos autres domaines, ` Visitor.appendVisitorIDsTo( *`l’URL`*)` ajoute le MID comme paramètre de requête dans l’URL redirigée depuis le domaine d’origine vers le domaine de destination.
* Le code du service d’ID sur le domaine de destination extrait l’MID de l’URL au lieu d’envoyer une requête d’identifiant à Adobe pour l’ID de ce visiteur. Cette requête inclut l’ID de cookie tiers, qui n’est pas disponible dans ce cas.
* Le code du service d’ID sur la page de destination utilise l’MID transmis pour effectuer le suivi du visiteur.

Consultez l’exemple de code pour plus de détails.

## Ajout d’un exemple de code d’identifiant visiteur {#section-62d55f7f986542b0b9238e483d50d7b0}

L’exemple suivant peut vous aider à démarrer avec ` Visitor.appendVisitorIDsTo( *`l’URL`*)`. Lorsque votre code JavaScript est correctement mis en œuvre, il peut ressembler à l’exemple suivant.

```js
//Code on Domain A 
var destinationURL = "www.destination.com"; 
 
//Call the ID service 
var visitor = Visitor.getInstance(...); 
 
//Append visitor IDs to the destination URL 
var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(destinationURL); 
     //Result of appendVisitorIDsTo includes destination URL, Experience Cloud ID (MCMID), and Analytics ID (MCAID) 
     "www.destination.com?adobe_mc=MCMID=1234|MCAID=5678"
//Redirect to the destination
```

## Prise en charge de Dynamic Tag Management (DTM) et du SDK {#section-168e313df6054af0a7e27b9fa0d69640}

<table id="table_6E7152B4FD2B4C4D8C9477C68204C4FF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Prise en charge de </th> 
   <th colname="col2" class="entry"> Voir </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>DTM</b> </p> </td> 
   <td colname="col2"> <p> <a href="https://helpx.adobe.com/fr/dtm/kb/how-to-set-marketing-cloud-id-service-helper-function-in-adobe-d.html" format="https" scope="external"> Définition de la fonction appendVisitorIDTo dans DTM </a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>SDK</b> </p> </td> 
   <td colname="col2"> 
    <ul id="ul_9D7933FF68EE4C71BAE999B3747F8398"> 
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/mc-methods.html?lang=fr" format="https" scope="external"> Méthodes du service d’ID Android </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/mc-methods.html?lang=fr" format="https" scope="external"> Méthodes du service d’ID iOS </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
