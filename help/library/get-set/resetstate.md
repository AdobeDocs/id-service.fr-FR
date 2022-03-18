---
description: Cette fonction s’adresse principalement aux utilisateurs d’A4T, pour les aider à résoudre des problèmes liés à l’utilisation d’identifiants sur des sites, écrans ou applications d’une seule page.
keywords: Service d’ID
title: resetState
exl-id: 8e8cb299-bb89-4bc1-8841-3091ce0cbd81
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '374'
ht-degree: 100%

---

# resetState{#resetstate}

Cette fonction s’adresse principalement aux utilisateurs d’A4T, pour les aider à résoudre des problèmes liés à l’utilisation d’identifiants sur des sites, écrans ou applications d’une seule page.

## Cas dʼutilisation {#section-840b88a5cdb042488b340cad5d7b22a5}

En tant que client d’A4T utilisant le service d’ID, vous pouvez utiliser la fonction `visitor.resetState()` lorsque vous devez :

* Transmettre un identifiant de données supplémentaires (SDID), ou tout autre identifiant, dʼune page ou dʼun écran à un autre par le biais dʼune redirection. Normalement, le service dʼidentification ne transmet pas cet identifiant sans cette fonction.
* Utiliser du code qui met uniquement à jour des sections spécifiques dʼune page ou dʼune application via des appels Ajax, et que vous souhaitez effectuer le suivi de ces actions. Supposons, par exemple, que vous ayez une page sur laquelle lorsque vous cliquez sur un objet seule une section spéciale est chargée ou modifiée. Dans ce cas, le service dʼidentification ne peut pas demander un autre identifiant, sauf si la page est rechargée. Cependant, avec `visitor.resetState()`, vous pouvez demander un nouvel ID.

Voir les exemples de code ci-dessous.

## Syntaxe {#section-9e63503e178f4be28ac850abf44d6d91}

**Syntaxe :** ` visitor.resetState( *`état`*);`

## Exemples de code {#section-d75b211bb4ea473887eb284de2ad838b}

La mise en œuvre de votre service dʼidentification affecte votre manière dʼutiliser cette fonction. Consultez des exemples dans le tableau ci-dessous.

**Mise en œuvre côté serveur**

Une mise en œuvre côté serveur concerne les clients d’A4T disposant d’un serveur mixte, des mises en œuvre de [!DNL Target] et d’[!DNL Analytics] côté client et du service d’ID. Si vous avez configuré le service d’ID avec cette méthode, il ne vous reste plus qu’à ajouter `visitor.resetState()` à la page. Les appels au service d’ID renvoient automatiquement un nouvel ID et un nouvel état du serveur.

**Mise en œuvre non standard** (avec ID)

Si vous avez configuré le service d’ID avec une [mise en œuvre non standard](../../implementation-guides/implementation-guides.md#section-2c4f2db1f9704315a7cccab6d2e07113), vous devez configurer un objet variable pour contenir le SDID (ou les autres ID) que vous souhaitez transmettre avec `visitor.resetState()`. Comme indiqué ci-dessous, cela inclut votre [ID d’organisation](../../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26) et l’ID que vous souhaitez transmettre. Voici à quoi pourrait ressembler votre code.

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

Dans ce cas, vous pouvez utiliser `visitor.resetState()` pour générer un nouvel ID. Cela peut sʼavérer utile dans une application monopage lorsquʼun utilisateur accède à un nouvel écran sans actualiser la page et que vous avez besoin dʼun nouvel identifiant.

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

**Gestionnaire dynamique de balises**

À l’heure actuelle, il n’existe pas de parcours de configuration de DTM pour `visitor.resetState()`.
