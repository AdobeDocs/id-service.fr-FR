---
description: Cette méthode d’aide permet d’ajouter le SDID (Supplemental Data ID) comme paramètre de chaîne de requête à une URL de redirection. Elle est utile lorsque vous utilisez A4T et que vous devez conserver le SDID d’une page à l’autre et assembler ces visites distinctes. Pour utiliser cette fonction, vous devez avoir mis en œuvre le service d’ID avec le même ID d’organisation sur les domaines source et de destination.
keywords: Service d’identification
seo-description: Cette méthode d’aide permet d’ajouter le SDID (Supplemental Data ID) comme paramètre de chaîne de requête à une URL de redirection. Elle est utile lorsque vous utilisez A4T et que vous devez conserver le SDID d’une page à l’autre et assembler ces visites distinctes. Pour utiliser cette fonction, vous devez avoir mis en œuvre le service d’ID avec le même ID d’organisation sur les domaines source et de destination.
seo-title: appendSupplementalDataIDTo
title: appendSupplementalDataIDTo
uuid: f 3504 d 82-8 da 3-4971-818 b -3 df 57 df 4 ec 2 d
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# appendSupplementalDataIDTo{#appendsupplementaldataidto}

Cette méthode d’aide permet d’ajouter le SDID (Supplemental Data ID) comme paramètre de chaîne de requête à une URL de redirection. Elle est utile lorsque vous utilisez A4T et que vous devez conserver le SDID d’une page à l’autre et assembler ces visites distinctes. Pour utiliser cette fonction, vous devez avoir mis en œuvre le service d’ID avec le même ID d’organisation sur les domaines source et de destination.

Contenu :

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> Syntaxe et exemple de code </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4" format="dita" scope="local"> Exemple de résultat </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> Syntaxe et exemple de code </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-99946715cefa4acc95200b093db5297e" format="dita" scope="local"> Modification du délai d’expiration du SDID à l’aide de la configuration sdidParamExpiry </a> </li> 
</ul>

## Syntaxe et exemple de code {#section-cbb0b2f73bcc418386796c24c01b2365}

**Syntaxe :**` appendSupplementalDataIDTo( *`URLSDID`*, *``*)`

**Exemple de code**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219");
```

## Exemple de résultat {#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4}

Comme indiqué ci-dessous, la redirection d’URL contient le SDID du visiteur, l’ID d’organisation et un horodatage UNIX dans l’appel à la page de réception.

<ul class="simplelist"> 
 <li> <span class="codeph"> www.domain.com/pageB?adobe_mc_sdid=SDID=123|MCORGID=123456789@AdobeOrg|TS=1498569322 </span> </li> 
</ul>

## Modification du délai d’expiration du SDID à l’aide de la configuration sdidParamExpiry {#section-99946715cefa4acc95200b093db5297e}

La configuration [sdidparamexpiry](../../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458) permet de modifier l&#39;intervalle d&#39;expiration SDID par défaut lors de la transmission de cet identifiant d&#39;une page à une autre à l&#39;aide de la fonction `appendSupplementalDataIDTo` helper. Par défaut, le code du service d’ID sur la page de réception dispose de 30 secondes pour obtenir le SDID auprès de l’URL envoyée par la page référente. Si le code du service d’ID sur la page de réception ne peut pas récupérer le SDID en moins de 30 secondes, il demande un nouveau SDID. Cette fonctionnalité est principalement destinée aux clients A4T qui ont besoin de transmettre le SDID d’une page à une autre et qui souhaitent contrôler l’intervalle d’expiration.

Si vous devez modifier le délai d’expiration par défaut du SDID, ajoutez `sdidParamExpiry` à la fonction `Visitor.getInstance` en utilisant la syntaxe suivante :

**Syntaxe :**` sdidParamExpiry: *`heure en secondes`*`

**Exemple de code**

Une fois configuré, le code de votre service d’ID pourrait ressembler à l’exemple ci-dessous. Cet exemple définit le délai d’expiration du SDID sur 15 secondes.

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
