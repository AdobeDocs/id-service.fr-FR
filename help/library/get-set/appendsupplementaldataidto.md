---
description: Cette méthode d’assistance vous permet d’ajouter l’ID de données supplémentaires (SDID) en tant que paramètre de chaîne de requête à une URL de redirection. Cela s’avère utile lorsque vous utilisez A4T et que vous devez conserver le SDID d’une page à l’autre et regrouper ces visites distinctes. Pour utiliser cette fonction, vous devez avoir mis en oeuvre le service d’ID avec le même ID d’organisation sur les domaines source et de destination.
keywords: Service d’identification
seo-description: Cette méthode d’assistance vous permet d’ajouter l’ID de données supplémentaires (SDID) en tant que paramètre de chaîne de requête à une URL de redirection. Cela s’avère utile lorsque vous utilisez A4T et que vous devez conserver le SDID d’une page à l’autre et regrouper ces visites distinctes. Pour utiliser cette fonction, vous devez avoir mis en oeuvre le service d’ID avec le même ID d’organisation sur les domaines source et de destination.
seo-title: appendSupplementalDataIDTo
title: appendSupplementalDataIDTo
uuid: f3504d82-8da3-4971-818b-3df57df4ec2d
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 28%

---


# appendSupplementalDataIDTo{#appendsupplementaldataidto}

Cette méthode d’assistance vous permet d’ajouter l’ID de données supplémentaires (SDID) en tant que paramètre de chaîne de requête à une URL de redirection. Cela s’avère utile lorsque vous utilisez A4T et que vous devez conserver le SDID d’une page à l’autre et regrouper ces visites distinctes. Pour utiliser cette fonction, vous devez avoir mis en oeuvre le service d’ID avec le même ID d’organisation sur les domaines source et de destination.

Contenu :

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> Syntaxe et exemple de code </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4" format="dita" scope="local"> Exemple de résultat </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> Syntaxe et exemple de code </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-99946715cefa4acc95200b093db5297e" format="dita" scope="local"> Modification du délai d’expiration du SDID à l’aide de la configuration sdidParamExpiry </a> </li> 
</ul>

## Syntaxe et exemple de code {#section-cbb0b2f73bcc418386796c24c01b2365}

**Syntaxe :** ` appendSupplementalDataIDTo( *`URL`*, *`SDID`*)`

**Exemple de code**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219");
```

## Exemple de résultat  {#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4}

Comme indiqué ci-dessous, la redirection d’URL contient le SDID du visiteur, l’ID d’organisation et un horodatage UNIX dans l’appel à la page de réception.

<ul class="simplelist"> 
 <li> <span class="codeph"> www.domain.com/pageB?adobe_mc_sdid=SDID=123|MCORGID=123456789@AdobeOrg|TS=1498569322 </span> </li> 
</ul>

## Modification du délai d’expiration du SDID à l’aide de la configuration sdidParamExpiry {#section-99946715cefa4acc95200b093db5297e}

La configuration [sdidParamExpiry](../../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458) permet de modifier l’intervalle d’expiration par défaut du SDID lors de la transmission de cet ID d’une page à une autre au moyen de la fonction d’aide `appendSupplementalDataIDTo`. Par défaut, le code du service d’ID sur la page de réception dispose de 30 secondes pour obtenir le SDID à partir de l’URL envoyée par la page de référence. Si le code du service d’ID sur la page de réception ne parvient pas à récupérer le SDID en moins de 30 secondes, il demande un nouveau SDID. Cette fonctionnalité s’adresse principalement aux clients A4T qui doivent transmettre le SDID d’une page à une autre et qui souhaitent contrôler cet intervalle de temporisation.

Si vous devez modifier le délai d’expiration par défaut du SDID, ajoutez `sdidParamExpiry` à la `Visitor.getInstance` fonction en utilisant la syntaxe suivante :

**Syntaxe :** ` sdidParamExpiry: *`temps en secondes`*`

**Exemple de code**

Une fois configuré, votre code de service d’ID peut ressembler à cet exemple. Cet exemple définit le délai d’attente SDID à 15 secondes.

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Change the default SDID timeout to 15 seconds 
   sdidParamExpiry: 15 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219"); 
```

