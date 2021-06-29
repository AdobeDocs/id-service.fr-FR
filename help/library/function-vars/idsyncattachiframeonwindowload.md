---
description: Indicateur booléen facultatif qui contrôle la manière dont le service Experience Cloud Identity charge l’iFrame de synchronisation des identifiants.
keywords: Service d’ID
title: idSyncAttachIframeOnWindowLoad
exl-id: 44c45378-f007-4d87-913a-d6bb9961948c
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '77'
ht-degree: 100%

---

# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

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
