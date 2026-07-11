---
description: Cette fonction s’adresse principalement aux utilisateurs d’A4T, pour les aider à résoudre des problèmes liés à l’utilisation d’identifiants sur des sites, écrans ou applications d’une seule page.
keywords: Service d’identification des visiteurs
title: resetState
exl-id: 8e8cb299-bb89-4bc1-8841-3091ce0cbd81
TQID: https://experienceleague.adobe.com/ud8yTufRC6V5T58oh20G65MYNTCZvMlK5FdHVrrZFpU
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 377
ht-degree: 54%

---

# resetState{#resetstate}

Cette fonction s’adresse principalement aux utilisateurs d’A4T, pour les aider à résoudre des problèmes liés à l’utilisation d’identifiants sur des sites, écrans ou applications d’une seule page.

## Cas d’utilisation {#section-840b88a5cdb042488b340cad5d7b22a5}

En tant que client A4T utilisant le service d’identification des visiteurs , vous pouvez utiliser la fonction `visitor.resetState()` lorsque vous devez :

* Transmettre un identifiant de données supplémentaires (SDID), ou tout autre identifiant, dʼune page ou dʼun écran à un autre par le biais dʼune redirection. Normalement, le service d’identification des visiteurs ne transmet pas cet identifiant sans cette fonction.
* Utiliser du code qui met uniquement à jour des sections spécifiques dʼune page ou dʼune application via des appels Ajax, et que vous souhaitez effectuer le suivi de ces actions. Supposons, par exemple, que vous ayez une page sur laquelle lorsque vous cliquez sur un objet seule une section spéciale est chargée ou modifiée. Dans ce cas, le service d’identification des visiteurs ne peut pas demander un identifiant différent à moins que la page ne soit rechargée. Cependant, avec `visitor.resetState()`, vous pouvez demander un nouvel ID.

Voir les exemples de code ci-dessous.

## Syntaxe {#section-9e63503e178f4be28ac850abf44d6d91}

**Syntaxe :** `visitor.resetState( *`état`*);`

## Exemples de code {#section-d75b211bb4ea473887eb284de2ad838b}

L’implémentation de votre service d’identification des visiteurs affecte la manière dont vous utiliseriez cette fonction. Consultez des exemples dans le tableau ci-dessous.

**Mise en œuvre côté serveur**

Une implémentation côté serveur est destinée aux clients A4T avec des implémentations mixtes côté serveur et côté client de Target, d’Analytics et du service d’identification des visiteurs. Si vous avez configuré le service d’identification des visiteurs avec cette méthode, il vous suffit d’ajouter des `visitor.resetState()` à la page. Les appels au service d’identification des visiteurs renverront automatiquement un nouvel ID et l’état du serveur.

**Mise en œuvre non standard** (avec ID)

Si vous avez configuré le service d’identification des visiteurs avec une [implémentation non standard](../../implementation-guides/implementation-guides.md#section-2c4f2db1f9704315a7cccab6d2e07113), vous devez configurer un objet variable pour contenir le SDID (ou d’autres ID) que vous souhaitez transmettre avec `visitor.resetState()`. Comme illustré ci-dessous, cela inclut votre [ID d’organisation IMS](../../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26) et l’identifiant que vous souhaitez transmettre. Voici à quoi pourrait ressembler votre code.

```js
//Instantiate server state variable 
var serverState = { 
     "INSERT-IMS-ORG-ID-HERE": { 
          //Specify the SDID or other ID 
          supplementalDataIDCurrent: "1234", 
          supplementalDataIDCurrentConsumed: { 
               "payload:top-center": false 
          } 
     } 
}; 
 
//Instantiate Visitor ID Service 
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE", { 
     ... 
}); 
 
//Reset server state to pass the SDID 
visitor.resetState(serverState);
```

**Mise en œuvre non standard** (sans transmission d’un ID)

Dans ce cas, vous pouvez utiliser `visitor.resetState()` pour générer un nouvel ID. Cela peut sʼavérer utile dans une application monopage lorsquʼun utilisateur accède à un nouvel écran sans actualiser la page et que vous avez besoin dʼun nouvel identifiant.

```js
 
//Instantiate Visitor ID Service 
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE", { 
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

