---
description: Cette configuration vous permet de remplacer l’intervalle d’expiration SDID (Supplemental Data ID) par défaut lors du transfert de cet ID d’une page à une autre à l’aide de la fonction d’assistance appendSupplementalDataIDTo. Par défaut, le code du service d’ID sur la page de réception dispose de 30 secondes pour obtenir le SDID à partir de l’URL envoyée par la page de référence. Si le code du service d’ID sur la page de réception ne parvient pas à récupérer le SDID en moins de 30 secondes, il demande un nouveau SDID. Cette fonctionnalité s’adresse principalement aux clients A4T qui doivent transmettre le SDID d’une page à une autre et qui souhaitent contrôler cet intervalle de temporisation.
keywords: ID Service
seo-description: Cette configuration vous permet de remplacer l’intervalle d’expiration SDID (Supplemental Data ID) par défaut lors du transfert de cet ID d’une page à une autre à l’aide de la fonction d’assistance appendSupplementalDataIDTo. Par défaut, le code du service d’ID sur la page de réception dispose de 30 secondes pour obtenir le SDID à partir de l’URL envoyée par la page de référence. Si le code du service d’ID sur la page de réception ne parvient pas à récupérer le SDID en moins de 30 secondes, il demande un nouveau SDID. Cette fonctionnalité s’adresse principalement aux clients A4T qui doivent transmettre le SDID d’une page à une autre et qui souhaitent contrôler cet intervalle de temporisation.
seo-title: sdidParamExpiry
title: sdidParamExpiry
uuid: cdaf7e2d-b196-4c70-936d-8a98191cbb85
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 9%

---


# sdidParamExpiry{#sdidparamexpiry}

Cette configuration vous permet de remplacer l’intervalle d’expiration SDID (Supplemental Data ID) par défaut lors du transfert de cet ID d’une page à une autre à l’aide de la fonction d’assistance appendSupplementalDataIDTo. Par défaut, le code du service d’ID sur la page de réception dispose de 30 secondes pour obtenir le SDID à partir de l’URL envoyée par la page de référence. Si le code du service d’ID sur la page de réception ne parvient pas à récupérer le SDID en moins de 30 secondes, il demande un nouveau SDID. Cette fonctionnalité s’adresse principalement aux clients A4T qui doivent transmettre le SDID d’une page à une autre et qui souhaitent contrôler cet intervalle de temporisation.

**Remplacer le délai d’expiration SDID**

Si vous devez modifier le délai d’expiration par défaut du SDID, ajoutez `sdidParamExpiry` à la `Visitor.getInstance` fonction en utilisant la syntaxe suivante :

**Syntaxe :** ` sdidParamExpiry: *`temps en secondes`*`

**Exemple de code**

Une fois configuré, votre code de service d’ID peut ressembler à cet exemple. Cet exemple définit le délai d’attente SDID à 15 secondes. Cette configuration fonctionne avec la méthode d’aide  [appendSupplementalDataIDTo](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d).

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

