---
description: Indicateur booléen facultatif qui contrôle la manière dont le service Experience Cloud Identity charge l’iFrame de synchronisation des identifiants.
keywords: Service d’ID
seo-description: Indicateur booléen facultatif qui contrôle la manière dont le service Experience Cloud Identity charge l’iFrame de synchronisation des identifiants.
seo-title: idSyncAttachIframeOnWindowLoad
title: idSyncAttachIframeOnWindowLoad
uuid: aa2c2fa4-2cab-4e08-8d35-729a6c3e459a
exl-id: 44c45378-f007-4d87-913a-d6bb9961948c
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '95'
ht-degree: 100%

---

# idSyncAttachIframeOnWindowLoad {#idsyncattachiframeonwindowload}

Indicateur booléen facultatif qui contrôle la manière dont le service Experience Cloud Identity charge l’iFrame de synchronisation des identifiants.

**Syntaxe :** ` `idSyncAttachIframeOnWindowLoad= true false`` (la valeur par défaut est `false`).

Si `idSyncAttachIframeOnWindowLoad: true`, le service d’ID charge l’iFrame de synchronisation des identifiants au chargement de la fenêtre. Par défaut, le service d’ID charge l’iFrame de synchronisation des ID aussi rapidement que possible au lieu de charger la fenêtre.

**Exemple de code**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example loads ID sync iFrame on window load instad of ASAP. 
   idSyncAttachIframeOnWindowLoad: true 
});
```
