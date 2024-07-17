---
description: Cette configuration vous permet de remplacer l’intervalle d’expiration par défaut du SDID (Supplemental Data ID) lors de la transmission de cet ID d’une page à une autre au moyen de la fonction d’aide appendSupplementalDataIDTo. Par défaut, le code du service d’ID sur la page de réception dispose de 30 secondes pour obtenir le SDID à partir de l’URL envoyée par la page référente. Si le code du service d’ID sur la page de réception ne parvient pas à récupérer le SDID en moins de 30 secondes, il demande un nouveau SDID. Cette fonctionnalité s’adresse principalement aux clients A4T qui doivent transmettre le SDID d’une page à une autre et qui souhaitent contrôler cet intervalle d’expiration.
keywords: Service d’ID
title: sdidParamExpiry
exl-id: 5458ffa5-03d1-4c52-907d-c50fe00ce35d
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 96%

---

# sdidParamExpiry{#sdidparamexpiry}

Cette configuration vous permet de remplacer l’intervalle d’expiration par défaut du SDID (Supplemental Data ID) lors de la transmission de cet ID d’une page à une autre au moyen de la fonction d’aide appendSupplementalDataIDTo. Par défaut, le code du service d’ID sur la page de réception dispose de 30 secondes pour obtenir le SDID à partir de l’URL envoyée par la page référente. Si le code du service d’ID sur la page de réception ne parvient pas à récupérer le SDID en moins de 30 secondes, il demande un nouveau SDID. Cette fonctionnalité s’adresse principalement aux clients A4T qui doivent transmettre le SDID d’une page à une autre et qui souhaitent contrôler cet intervalle d’expiration.

**Remplacement de le délai d’expiration du SDID**

Si vous devez modifier le délai d’expiration par défaut du SDID, ajoutez `sdidParamExpiry` à la `Visitor.getInstance` fonction en utilisant la syntaxe suivante :

**Syntaxe :** ` sdidParamExpiry: *`temps en secondes`*`

**Exemple de code**

Voici à quoi pourrait ressembler votre code de service d’ID une fois configuré. Cet exemple définit le délai d’expiration du SDID sur 15 secondes. Cette configuration fonctionne avec la méthode d’assistance [appendSupplementalDataIDTo](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d) .

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
