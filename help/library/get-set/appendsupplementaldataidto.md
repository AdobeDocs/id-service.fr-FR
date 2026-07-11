---
description: Cette méthode d’aide vous permet d’ajouter le SDID (Supplemental Data ID) comme paramètre de chaîne de requête à une URL de redirection. Cette opération est utile lorsque vous utilisez A4T et que vous devez conserver le SDID d’une page à une autre afin de regrouper ces visites distinctes. Pour utiliser cette fonction, vous devez avoir mis en œuvre le service d’identification des visiteurs avec le même identifiant d’organisation IMS sur les domaines source et de destination.
keywords: Service d’identification des visiteurs
title: appendSupplementalDataIDTo
exl-id: 7f0e7fca-4551-4165-a12b-c7e5514d6818
TQID: https://experienceleague.adobe.com/oR2LCiVk5N-Xnt3wTOKMt7UYFXzwEGFwJpKoz-ikzh8
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 354
ht-degree: 61%

---

# appendSupplementalDataIDTo{#appendsupplementaldataidto}

Cette méthode d’aide vous permet d’ajouter le SDID (Supplemental Data ID) comme paramètre de chaîne de requête à une URL de redirection. Cette opération est utile lorsque vous utilisez A4T et que vous devez conserver le SDID d’une page à une autre afin de regrouper ces visites distinctes. Pour utiliser cette fonction, vous devez avoir mis en œuvre le service d’identification des visiteurs avec le même identifiant d’organisation IMS sur les domaines source et de destination.

Contenu :

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> Syntaxe et exemple de code </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4" format="dita" scope="local"> Exemple de résultat </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> Syntaxe et exemple de code </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-99946715cefa4acc95200b093db5297e" format="dita" scope="local"> Modification du délai d’expiration du SDID à l’aide de la configuration sdidParamExpiry </a> </li> 
</ul>

## Syntaxe et exemple de code {#section-cbb0b2f73bcc418386796c24c01b2365}

**Syntaxe :** `appendSupplementalDataIDTo( *`URL`*, *`SDID`*)`

**Exemple de code**

```js
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE"); 

//Get current supplemental data id
var theCurrentSDID = visitor._supplementalDataIDCurrent ? visitor._supplementalDataIDCurrent : "";

//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, theCurrentSDID));
```

## Exemple de résultat {#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4}

Comme illustré ci-dessous, la redirection d’URL contient le SDID du visiteur ou de la visiteuse, l’ID d’organisation IMS et un horodatage UNIX dans l’appel à la page de réception.

<ul class="simplelist"> 
 <li> <span class="codeph"> www.domain.com/pageB?adobe_mc_sdid=SDID=7996F0B028999505-13DA591039D6226|MCORGID=123456789@AdobeOrg|TS=1498569322 </span> </li> 
</ul>

## Modifier le délai d’expiration du SDID à l’aide de la configuration sdidParamExpiry {#section-99946715cefa4acc95200b093db5297e}

La configuration [sdidParamExpiry](../../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458) permet de modifier l’intervalle d’expiration par défaut du SDID lors de la transmission de cet ID d’une page à une autre au moyen de la fonction d’aide `appendSupplementalDataIDTo`. Par défaut, le code du service d’identification des visiteurs sur la page de réception dispose de 30 secondes pour obtenir le SDID à partir de l’URL envoyée par la page référente. Si le code du service d’identification des visiteurs sur la page de réception ne parvient pas à récupérer le SDID en moins de 30 secondes, il demande un nouveau SDID. Cette fonctionnalité s’adresse principalement aux clients A4T qui doivent transmettre le SDID d’une page à une autre et qui souhaitent contrôler cet intervalle de délai d’expiration.

Si vous devez modifier le délai d’expiration par défaut du SDID, ajoutez `sdidParamExpiry` à la `Visitor.getInstance` fonction en utilisant la syntaxe suivante :

**Syntaxe :** `sdidParamExpiry: *`temps en secondes`*`

**Exemple de code**

Voici à quoi pourrait ressembler votre code du service d’identification des visiteurs une fois configuré. Cet exemple définit le délai d’expiration du SDID sur 15 secondes.

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   ... 
   //Change the default SDID timeout to 15 seconds 
   sdidParamExpiry: 15 
}); 
 
//Get current supplemental data id
var theCurrentSDID = visitor._supplementalDataIDCurrent ? visitor._supplementalDataIDCurrent : "";

//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, theCurrentSDID)); 
```

