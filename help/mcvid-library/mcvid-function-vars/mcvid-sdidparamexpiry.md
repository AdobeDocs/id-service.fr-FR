---
description: Cette configuration permet de remplacer l’intervalle d’expiration par défaut du SDID (Supplemental Data ID) lors de la transmission de cet ID d’une page à une autre au moyen de la fonction d’aide appendSupplementalDataIDTo. Par défaut, le code du service d’ID sur la page de réception dispose de 30 secondes pour obtenir le SDID auprès de l’URL envoyée par la page référente. Si le code du service d’ID sur la page de réception ne peut pas récupérer le SDID en moins de 30 secondes, il demande un nouveau SDID. Cette fonctionnalité est principalement destinée aux clients A4T qui ont besoin de transmettre le SDID d’une page à une autre et qui souhaitent contrôler l’intervalle d’expiration.
keywords: Service d’identification
seo-description: Cette configuration permet de remplacer l’intervalle d’expiration par défaut du SDID (Supplemental Data ID) lors de la transmission de cet ID d’une page à une autre au moyen de la fonction d’aide appendSupplementalDataIDTo. Par défaut, le code du service d’ID sur la page de réception dispose de 30 secondes pour obtenir le SDID auprès de l’URL envoyée par la page référente. Si le code du service d’ID sur la page de réception ne peut pas récupérer le SDID en moins de 30 secondes, il demande un nouveau SDID. Cette fonctionnalité est principalement destinée aux clients A4T qui ont besoin de transmettre le SDID d’une page à une autre et qui souhaitent contrôler l’intervalle d’expiration.
seo-title: sdidParamExpiry
title: sdidParamExpiry
uuid: cdaf 7 e 2 d-b 196-4 c 70-936 d -8 a 98191 cbb 85
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# sdidParamExpiry{#sdidparamexpiry}

Cette configuration permet de remplacer l’intervalle d’expiration par défaut du SDID (Supplemental Data ID) lors de la transmission de cet ID d’une page à une autre au moyen de la fonction d’aide appendSupplementalDataIDTo. Par défaut, le code du service d’ID sur la page de réception dispose de 30 secondes pour obtenir le SDID auprès de l’URL envoyée par la page référente. Si le code du service d’ID sur la page de réception ne peut pas récupérer le SDID en moins de 30 secondes, il demande un nouveau SDID. Cette fonctionnalité est principalement destinée aux clients A4T qui ont besoin de transmettre le SDID d’une page à une autre et qui souhaitent contrôler l’intervalle d’expiration.

**Remplacement du délai d’expiration du SDID**

Si vous devez modifier le délai d’expiration par défaut du SDID, ajoutez `sdidParamExpiry` à la fonction `Visitor.getInstance` en utilisant la syntaxe suivante :

**Syntaxe :**` sdidParamExpiry: *`heure en secondes`*`

**Exemple de code**

Une fois configuré, le code de votre service d’ID pourrait ressembler à l’exemple ci-dessous. Cet exemple définit le délai d’expiration du SDID sur 15 secondes. Cette configuration fonctionne avec la méthode d’aide [appendSupplementalDataIDTo](../../mcvid-library/mcvid-get-set/mcvid-appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d).

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

