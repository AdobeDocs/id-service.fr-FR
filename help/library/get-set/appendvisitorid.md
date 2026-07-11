---
description: Cette fonction permet de partager l’ECID d’un visiteur sur plusieurs domaines lorsque les navigateurs bloquent les cookies tiers. Pour utiliser cette fonction, vous devez avoir mis en œuvre le service d’identification des visiteurs et être propriétaire des domaines source et de destination. Disponible dans VisitorAPI.js 1.7.0 ou version ultérieure.
keywords: Service d’identification des visiteurs
title: appendVisitorIDsTo (suivi interdomaines)
exl-id: 3e4f4e2c-e658-4124-bd0e-59c63127bdde
TQID: https://experienceleague.adobe.com/F4rWmYj6NidX861-qU8KI9RRbdwNdzP0x4CZUxPZfYw
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 432
ht-degree: 61%

---

# appendVisitorIDsTo (suivi interdomaines){#appendvisitoridsto-cross-domain-tracking}

>[!TIP]
>
>Le suivi inter-domaines ne fonctionne pas comme prévu si l’ECID est initialement (ou précédemment) rejeté. Les identifiants précédemment transmis par URL ou stockés dans le cookie ne sont pas contrôlés, car ils avaient été définis lorsque le consentement était défini sur « NON ».

Cette fonction permet de partager l’ECID d’un visiteur sur plusieurs domaines lorsque les navigateurs bloquent les cookies tiers. Pour utiliser cette fonction, vous devez avoir mis en œuvre le service d’identification des visiteurs et être propriétaire des domaines source et de destination. Disponible dans `VisitorAPI.js` version 1.7.0 ou ultérieure.

Contenu :

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> Suivi des visiteurs sur plusieurs domaines lorsque les navigateurs bloquent les cookies tiers </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> Ajout d’un exemple de code d’identifiant visiteur </a> </li> 
 </a> </li> 
</ul>

## Suivre les visiteurs sur plusieurs domaines lorsque les navigateurs bloquent les cookies tiers {#section-7251d88befd440b4b79520e33c5aa44a}

Le service d’identification des visiteurs écrit un cookie propriétaire et tiers dans le navigateur lorsqu’une personne visite votre site (voir [&#x200B; Cookies et service d’identification des visiteurs &#x200B;](../../introduction/cookies.md) ). Le cookie propriétaire contient le MID, un ID unique pour ce visiteur. Le cookie tiers contient un autre identifiant utilisé par le service d’identification des visiteurs pour générer le MID. Lorsqu’un navigateur bloque ce cookie tiers, le service d’identification des visiteurs ne peut pas :

* Régénérer l’ID unique de ce visiteur de site lorsqu’il accède à un autre domaine.
* Effectuer le suivi des visiteurs sur différents domaines appartenant à votre entreprise.

Pour résoudre ce problème, mettez en œuvre `Visitor.appendVisitorIDsTo( *`l’URL`*)`. Cette propriété permet au service d’identification des visiteurs de suivre les visiteurs du site sur plusieurs domaines, même si leurs navigateurs bloquent les cookies tiers. Voici son fonctionnement :

* Lorsqu’un visiteur navigue sur vos autres domaines, `Visitor.appendVisitorIDsTo( *`l’URL`*)` ajoute le MID comme paramètre de requête dans l’URL redirigée depuis le domaine d’origine vers le domaine de destination.
* Le code du service d’identification des visiteurs sur le domaine de destination extrait le MID de l’URL au lieu d’envoyer une demande d’identification de ce visiteur à Adobe. Cette requête inclut l’ID de cookie tiers, qui n’est pas disponible dans ce cas.
* Le code du service d’identification des visiteurs sur la page de destination utilise le MID transmis pour suivre le visiteur.

Consultez l’exemple de code pour plus de détails.

## Ajout d’un exemple de code d’identifiant visiteur {#section-62d55f7f986542b0b9238e483d50d7b0}

L’exemple de code suivant peut vous aider à commencer à utiliser la fonction `appendVisitorIDsTo` :

>[!TIP]
>
>Ce code peut être placé dans l’éditeur de code personnalisé qui fait partie de l’extension Adobe Analytics ou dans la partie supérieure de [AppMeasurement.js](https://experienceleague.adobe.com/docs/analytics/implementation/js/overview.html?lang=fr).

```js
var adbeDomains = ["marketo.com", "figma.com", "workfront.com"];
var visitor = Visitor.getInstance("9E1005A551ED61CA0A490D45@AdobeOrg", {
  trackingServer: "sstats.adobe.com",
  trackingServerSecure: "sstats.adobe.com",
  marketingCloudServer: "sstats.adobe.com",
  marketingCloudServerSecure: "sstats.adobe.com"
});
adbeDomains.forEach(function(domain) {
  var domainRegex = RegExp(domain);
  if (!domainRegex.test(location.hostname)) {
    hrefSelector = '[href*="' + domain + '"]';
    document.querySelectorAll(hrefSelector).forEach(function(href) {
      href.addEventListener('mousedown', function(event) {
        var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(event.currentTarget.href)
        event.currentTarget.href = destinationURLWithVisitorIDs.replace(/MCAID%3D.*%7CMCORGID/, 'MCAID%3D%7CMCORGID');
      });
    });
  }
});
```

<!-- 
>[!IMPORTANT]
>
>In order for the values passed in the URL via appendVisitorsIDsTo to be picked up, the [ovewriteCrossDomainMCIDAndAID](../function-vars/overwrite-visitor-id.md) variable must be set to true.

The following example can help you get started with `Visitor.appendVisitorIDsTo( *`url`*)`. When implemented properly, your JavaScript code could look similar to the following example.

```js
//Code on Domain A 
var destinationURL = "www.destination.com"; 
 
//Call the Visitor ID Service 
var visitor = Visitor.getInstance(...); 
 
//Append visitor IDs to the destination URL 
var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(destinationURL); 
     //Result of appendVisitorIDsTo includes destination URL, ECID (MCMID), and Analytics ID (MCAID) 
     "www.destination.com?adobe_mc=MCMID=1234|MCAID=5678"
//Redirect to the destination
``` 
-->

<!--
## SDK Support {#section-168e313df6054af0a7e27b9fa0d69640}

<table id="table_6E7152B4FD2B4C4D8C9477C68204C4FF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Support for </th> 
   <th colname="col2" class="entry"> See </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>SDK</b> </p> </td> 
   <td colname="col2"> 
    <ul id="ul_9D7933FF68EE4C71BAE999B3747F8398"> 
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/mc-methods.html" format="https" scope="external"> Android Visitor ID Service Methods </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/mc-methods.html" format="https" scope="external"> iOS Visitor ID Service Methods </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table> 
-->

