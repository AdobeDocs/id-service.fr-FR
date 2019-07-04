---
description: Cette fonction s’adresse principalement aux utilisateurs d’A4T, pour les aider à résoudre des problèmes liés à l’utilisation d’identifiants sur des sites, écrans ou applications d’une seule page.
keywords: Service d’identification
seo-description: Cette fonction s’adresse principalement aux utilisateurs d’A4T, pour les aider à résoudre des problèmes liés à l’utilisation d’identifiants sur des sites, écrans ou applications d’une seule page.
seo-title: resetState
title: resetState
uuid: ed7be76d-a7ee-4e51-b26c-456ff85fd096
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# resetState{#resetstate}

Cette fonction s’adresse principalement aux utilisateurs d’A4T, pour les aider à résoudre des problèmes liés à l’utilisation d’identifiants sur des sites, écrans ou applications d’une seule page.

## Cas d’utilisation {#section-840b88a5cdb042488b340cad5d7b22a5}

En tant que client d’A4T utilisant le service d’ID, vous pouvez utiliser la fonction `visitor.resetState()` lorsque vous devez :

* Transmettre un SDID (Supplemental Data ID) ou tout autre ID, d’une page ou d’un écran à un autre au moyen d’une redirection. Normalement, le service d’ID ne transmet pas cet ID sans cette fonction.
* Utiliser du code qui ne met à jour que des sections spécifiques d’une page ou d’une application via des appels Ajax et que vous souhaitez effectuer le suivi de ces actions. Par exemple, imaginons une page sur laquelle le fait de cliquer sur un objet ne fait que charger ou modifier une section spéciale. Dans ce cas, le service d’ID ne peut pas demander un ID différent tant que la page n’est pas rechargée. Cependant, avec `visitor.resetState()`, vous pouvez demander un nouvel ID.

Voir les exemples de code ci-dessous.

## Syntaxe {#section-9e63503e178f4be28ac850abf44d6d91}

**Syntaxe :** ` visitor.resetState( *`état`*);`

## Exemples de code {#section-d75b211bb4ea473887eb284de2ad838b}

La mise en œuvre de votre service d’ID affecte la manière dont vous utiliserez cette fonction. Reportez-vous au tableau ci-dessous pour obtenir des exemples.

**Mise en œuvre côté serveur**

Une mise en œuvre côté serveur concerne les clients d’A4T disposant d’un serveur mixte, des mises en œuvre de [!DNL Target] et d’[!DNL Analytics] côté client et du service d’ID. Si vous avez configuré le service d’ID avec cette méthode, il ne vous reste plus qu’à ajouter `visitor.resetState()` à la page. Les appels au service d’ID renvoient automatiquement un nouvel ID et un nouvel état du serveur.

**Mise en œuvre non standard** (avec ID)

Si vous avez configuré le service d’ID avec une [mise en œuvre non standard](../../mcvid-implementation-guides/mcvid-implementation-guides.md#section-2c4f2db1f9704315a7cccab6d2e07113), vous devez configurer un objet variable pour contenir le SDID (ou les autres ID) que vous souhaitez transmettre avec `visitor.resetState()`. Comme indiqué ci-dessous, cela inclut votre [ID d’organisation](../../mcvid-reference/mcvid-requirements.md#section-a02f537129a64ffbb690d5738d360c26) et l’ID que vous souhaitez transmettre. Voici à quoi pourrait ressembler votre code.

```js
//Instantiate server state variable 
var serverState = { 
     "Insert Experience Cloud organization ID here": { 
          //Specify the SDID or other ID 
          supplementalDataIDCurrent: "1234", 
          supplementalDataIDCurrentConsumed: { 
               "payload:top-center": false 
          } 
     } 
}; 
 
//Instantiate ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here", { 
     ... 
}); 
 
//Reset server state to pass the SDID 
visitor.resetState(serverState);
```

**Mise en œuvre non standard** (sans transmission d’un ID)

Dans ce cas, vous pouvez utiliser `visitor.resetState()` pour générer un nouvel ID. Cela peut être utile dans une application d’une seule page lorsqu’un utilisateur accède à un nouvel écran sans actualiser la page et que vous avez besoin d’un nouvel ID.

```js
 
//Instantiate ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here", { 
     ... 
}); 
 
//Request a supplemental Data ID for consumer1 and consumer2: 
var sdid1 = visitor.getSupplementalDataID("consumer1"); // sdid1: 1234 
var sdid2 = visitor.getSupplementalDataID("consumer2"); // sdid2: 1234 
 
//User navigates to a new screen in a single-page app, without refreshing the page. 
//To reset the Supplemental Data ID internal, call resetState without passing any parameters. 
//This way we will not be recycling the `1234` ID anymore. Instead Visitor will generate a new supplemental Data ID going forward. 
visitor.resetState(); 
 
//Request a supplemental Data ID for consumer3 and consumer4: 
var sdid1 = visitor.getSupplementalDataID("consumer3"); // sdid1: 5678 
 
var sdid2 = visitor.getSupplementalDataID("consumer4"); // sdid2: 5678
```

**Dynamic Tag Manager (DTM)**

À l’heure actuelle, il n’existe pas de parcours de configuration de DTM pour `visitor.resetState()`.
