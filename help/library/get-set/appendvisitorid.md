---
description: Cette fonction permet de partager l’Experience Cloud ID d’un visiteur sur plusieurs domaines lorsque les navigateurs bloquent les cookies tiers. Pour utiliser cette fonction, vous devez avoir mis en œuvre le service d’ID et posséder les domaines source et de destination. Disponible dans VisitorAPI.js 1.7.0 ou version ultérieure.
keywords: Service d’identification
seo-description: Cette fonction permet de partager l’Experience Cloud ID d’un visiteur sur plusieurs domaines lorsque les navigateurs bloquent les cookies tiers. Pour utiliser cette fonction, vous devez avoir mis en œuvre le service d’ID et posséder les domaines source et de destination. Disponible dans VisitorAPI.js 1.7.0 ou version ultérieure.
seo-title: appendVisitorIDsTo (suivi interdomaines)
title: appendVisitorIDsTo (suivi interdomaines)
uuid: 06b453ee-73c5-4625-82d9-877ad2b4f702
translation-type: ht
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# appendVisitorIDsTo (suivi interdomaines){#appendvisitoridsto-cross-domain-tracking}

Cette fonction permet de partager l’Experience Cloud ID d’un visiteur sur plusieurs domaines lorsque les navigateurs bloquent les cookies tiers. Pour utiliser cette fonction, vous devez avoir mis en œuvre le service d’ID et posséder les domaines source et de destination. Disponible dans VisitorAPI.js 1.7.0 ou version ultérieure.

Contenu :

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> Suivi des visiteurs sur plusieurs domaines lorsque les navigateurs bloquent les cookies tiers </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> Ajout d’un exemple de code d’identifiant visiteur </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-168e313df6054af0a7e27b9fa0d69640" format="dita" scope="local"> Prise en charge de Dynamic Tag Management (DTM) et du SDK </a> </li> 
</ul>

## Suivi des visiteurs sur plusieurs domaines lorsque les navigateurs bloquent les cookies tiers {#section-7251d88befd440b4b79520e33c5aa44a}

Le service d’ID écrit un cookie propriétaire et tiers dans le navigateur lorsqu’une personne visite votre site (voir [Cookies et service Experience Cloud Identity](../../introduction/cookies.md) ). Le cookie propriétaire contient le MID, un identifiant unique pour ce visiteur. Le cookie tiers contient un autre ID utilisé par le service d’ID pour générer le MID. Lorsqu’un navigateur bloque ce cookie tiers, le service d’ID ne peut pas :

* régénérer l’ID unique pour le visiteur du site lorsque ce dernier accède à un autre domaine ;
* effectuer le suivi des visiteurs sur des domaines différents appartenant à votre organisation.

Pour résoudre ce problème, mettez en œuvre ` Visitor.appendVisitorIDsTo( *`l’URL`*)`. Cette propriété permet au service d’ID d’effectuer le suivi des visiteurs du site sur plusieurs domaines, même lorsque leurs navigateurs bloquent les cookies tiers. Elle fonctionne de la manière suivante :

* Lorsqu’un visiteur navigue sur vos autres domaines, ` Visitor.appendVisitorIDsTo( *`l’URL`*)` ajoute le MID comme paramètre de requête dans l’URL redirigée depuis le domaine d’origine vers le domaine de destination.
* Le code du service d’ID sur le domaine de destination extrait le MID de l’URL au lieu d’envoyer une requête d’identifiant à Adobe pour ce visiteur. Cette requête inclut l’ID de cookie tiers, qui n’est pas disponible dans ce cas.
* Le code du service d’ID sur la page de destination utilise le MID transmis pour effectuer le suivi du visiteur.

Pour plus d’informations, voir l’exemple de code.

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
     "www.destination.com?adobe_mc=MCMID=1234|MCAID=5678 
<draft-comment>
  |TS=123675879 
</draft-comment>" 
 
//Redirect to the destination
```

## Prise en charge de Dynamic Tag Management (DTM) et du SDK {#section-168e313df6054af0a7e27b9fa0d69640}

<table id="table_6E7152B4FD2B4C4D8C9477C68204C4FF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Prise en charge de </th> 
   <th colname="col2" class="entry"> Voir la section </th> 
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
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://marketing.adobe.com/resources/help/fr_FR/mobile/android/mc_methods.html" format="https" scope="external"> Méthodes du service d’ID Android </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://marketing.adobe.com/resources/help/fr_FR/mobile/ios/mc_methods.html" format="https" scope="external"> Méthodes du service d’ID iOS </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

