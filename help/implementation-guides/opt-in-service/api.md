---
description: API pour la bibliothèque et références des paramètres de configuration d’Opt-in.
seo-description: API pour la bibliothèque et références des paramètres de configuration d’Opt-in.
seo-title: Références d’Opt-in
title: Références d’Opt-in
uuid: d5023a34-2f3e-464d-b21f-579b2f416ce6
translation-type: tm+mt
source-git-commit: 4fbfefddcf36855f32f2a4047e19ef0b22fc508c

---


# Références d’Opt-in{#opt-in-reference}

API pour la bibliothèque et références des paramètres de configuration d’Opt-in.

Les paramètres de consentement sont fournis aux fonctions d’Opt-in par catégories :

```
adobe.OptInCategories = { 
    "AAM": "aam", 
    "ANALYTICS": "aa", 
    "ECID": "ecid", 
    "TARGET": "target" 
}
```

## Paramètres de configuration d’Opt-in {#section-d66018342baf401389f248bb381becbf}

Cette section aborde l’utilisation de l’API pour configurer Opt-in. Une grande partie de la configuration et de la mise en œuvre peut être effectuée avec l’extension Experience Platform Launch.

Les configurations d’Opt-in sont fournies dans la fonction `getInstance()` du fichier JavaScript Visiteur, qui instancie l’objet `adobe` global. Vous trouverez ci-après les configurations du fichier JavaScript Visiteur liées au service Opt-in.

**`doesOptInApply (boolean or function that evaluates to a boolean)`** :

« False » indique que les visiteurs n’ont pas besoin de donner leur accord. Entraîne la création de cookies par Experience Cloud quelles que soient les catégories pour lesquelles le visiteur donne son accord ou se désinscrit. De manière globale, cette configuration active ou désactive Opt-in.

**`preOptInApprovals (Object <adobe.OptInCategories enum: boolean>)`**

Définit les catégories approuvées ou refusées lorsqu’aucune préférence n’a encore été définie par le visiteur, considérées comme les autorisations par défaut de la structure.

**`previousPermissions (Object<adobe.OptInCategories enum: boolean>)`**

Le visiteur définit ses préférences de façon explicite. Les autorisations de cette configuration remplacent les autorisations par défaut de la structure (`previousPermissions` remplace `preOptInApprovals`).

**`isOptInStorageEnabled (boolean)`**

Permet à Opt-in de stocker les autorisations dans un cookie propriétaire (dans le domaine actuel du client).

(Facultatif) **`optInCookiesDomain (string)`**

Domaine propriétaire ou sous-domaine à utiliser pour le cookie d’Opt-in (si `isOptInStorageEnabled` est défini sur « true »).

(Facultatif) **`optInStorageExpiry (integer)`**

Nombre de secondes nécessaires au remplacement de l’expiration par défaut de 13 mois.

## Modification des paramètres de consentement {#section-c3d85403ff0d4394bd775c39f3d001fc}

À tout moment lors de son passage sur votre site, un visiteur peut définir ses préférences pour la première fois ou modifier celles-ci à l’aide de votre CMP. Une fois le fichier JavaScript Visiteur initialisé avec les premiers paramètres, les autorisations du visiteur peuvent être modifiées grâce aux fonctions suivantes :

**`adobe.optIn.approve(categories, shouldWaitForComplete)`**

Fonction qui approuve ou engage le consentement du visiteur pour l’ensemble des catégories d’une liste. Pour plus d’informations sur le paramètre shouldWaitForComplete, voir [Workflow d’Opt-in](../../implementation-guides/opt-in-service/getting-started.md#section-70cd243dec834c8ea096488640ae20a5).

**`adobe.optIn.deny(categories, shouldWaitForComplete)`**

Fonction qui refuse ou désinscrit le visiteur de l’ensemble des catégories spécifiées.

**`adobe.optIn.approveAll()`** :

Si la demande d’autorisation de création de cookies pour votre site est formulée de façon à ce que le visiteur accepte ou refuse de manière globale d’accorder l’autorisation de création, utilisez `approveAll()` ou `denyAll()`, selon la réponse donnée par celui-ci.

**`adobe.optIn.denyAll()`** :

Si la demande d’autorisation de création de cookies pour votre site est formulée de façon à ce que le visiteur accepte ou refuse de manière globale d’accorder l’autorisation de création, utilisez `approveAll()` ou `denyAll()`, selon la réponse donnée par celui-ci.

## Paramètres des workflows d’Opt-in {#section-2c5adfa5459c4e72b96d2693123a53c2}

Opt-in prend en charge un workflow avec lequel des autorisations peuvent être collectées sur plus d’un cycle de requêtes et les préférences sont délivrées une par une. En utilisant les fonctions suivantes et en stipulant *true* pour le paramètre `shouldWaitForComplete`, votre solution peut collecter le consentement pour une catégorie ou pour un sous-ensemble de catégories parmi toutes celles qui existent, puis collecter le consentement pour la catégorie suivante ou le sous-ensemble de catégories suivant. La propriété `adobe.optIn.status` démarre au premier appel et est mise en attente jusqu’à ce que `adobe.optIn.complete()` soit appelée en fin de flux. Une fois appelée, son état est défini sur *Complete*.

**`adobe.optIn.approve(categories, shouldWaitForComplete)`**

Fonction qui approuve ou engage le consentement du visiteur pour l’ensemble des catégories d’une liste.

`adobe.optIn.deny(categories, shouldWaitForComplete)`

Fonction qui refuse ou désinscrit le visiteur de l’ensemble des catégories spécifiées.

`adobe.optIn.complete()`

Fonction qui entraîne l’agrégation des appels faisant partie de la procédure d’approbation [approve()] ou de refus [deny()] en une requête unique pour définir les préférences d’un visiteur. Lorsque vous souscrivez aux modifications d’Opt-in (voir `adobe.optIn.fetchPermissions(callback, shouldAutoSubscribe`) ci-dessous, votre rappel (callback) se déclenche uniquement lors de l’appel de cette fonction.

## Paramètres des autorisations d’Opt-in des visiteurs {#section-7fe57279b5b44b4f8fe47e336df60155}

Collectez à tout moment les autorisations d’Opt-in d’un visiteur grâce à l’une des fonctions d’autorisation :

`adobe.optIn.permissions`

Objet qui reprend toutes les solutions d’Experience Cloud, comme les catégories, ayant été acceptées ou refusées par le visiteur.

`adobe.optIn.isApproved(categories)`

Si l’ensemble des catégories a été approuvé, cette fonction renvoie « true ».

`adobe.optIn.fetchPermissions(callback, shouldAutoSubscribe)`

Récupère la liste des autorisations de façon asynchrone. Le rappel est effectué avec la liste des autorisations, une fois le processus d’acceptation ou de refus des autorisations terminé. En stipulant la valeur *true* pour le paramètre `shouldAutoSubscribe`, le rappel est désormais enregistré pour toute modification d’Opt-in. Les paramètres suivants sont des propriétés d’`adobe.OptIn` :

**`permissions`**

Un objet qui reprend toutes les solutions d’Experience Cloud, comme les catégories, ayant été acceptées ou refusées par le visiteur. Par exemple : `{ aa: true, ecid: false, aam: true... }`

**`status`**

* pending (en attente)
* changed (modifié)
* terminé

**`doesOptInApply`**

« True » ou « false », selon la configuration fournie au moment de l’initialisation.

**`isPending`**

« True » ou « false », selon l’état. Opt-in renvoie « true » pour cette propriété quand un visiteur n’a pas encore explicitement accepté ou décliné l’autorisation.

**`isComplete`**

« True » ou « false », selon l’état. Il se pourrait qu’Opt-in renvoie « false » pour cette propriété lorsqu’un processus de consentement pouvant appartenir au workflow a débuté, mais qu’il n’a pas été jusqu’au bout.

## Méthodes de l’objet Opt-in {#section-e0417801a82548d199d833010033e433}

**`approve(categories, shouldWaitForComplete)`**

**`categories`** : Une ou plusieurs catégories à approuver. Par exemple : `adobe.optIn.approve([adobe.OptInCategories.AAM, adobe.OptInCategories.ECID])`
**`shouldWaitForComplete`** : (facultatif) paramètre booléen, réglé sur « false » par défaut. Si vous le réglez sur « true », Opt-in ne termine pas le processus d’approbation, jusqu’à ce que vous appeliez `adobe.optIn.complete()`. Ce processus est similaire à un workflow.

```
<codeblock>
  adobe.optIn.approve(adobe.OptInCategories.ANALYTICS, 
         true); adobe.optIn.approve(adobe.OptInCategories.ECID, true); 
         adobe.optIn.complete() 
</codeblock>
```

**`deny(categories, shouldWaitForComplete)`**

* Transmet une catégorie ou plus pour vérifier si elles ont été approuvées ou pas.
* Si aucune catégorie n’est transmise, cette vérification est effectuée sur l’ensemble des catégories disponible.

**`isApproved(categories)`**

Vérifiez si au moins une catégorie a été approuvée par le client.

**`isPreApproved(categories)`**

Vérifiez si au moins une des catégories a été préalablement approuvée par le client. (Si elles ont été transmises dans la `preOptInApprovals` configuration).

**`fetchPermissions(callback, shouldAutoSubscribe)`**

API asynchrone pour récupérer la liste des autorisations. Le rappel est effectué avec la liste des autorisations, une fois le processus d’acceptation ou de refus des autorisations terminé. **`shouldAutoSubscribe` :** Utilitaire d’aide qui souscrit automatiquement à ce rappel à tous les futurs événements. Cela signifie que le rappel est effectué chaque fois qu’une approbation ou un refus est déclenché dans Opt-in. De cette façon, vous êtes informé en continu, sans devoir vous-même vous abonner aux événements.

**Exemple**

`fetchPermissions`

```
optIn.fetchPermissions(function (permissions) { 
    // Here you can check if your category has been approved or not. 
    // We recommend using `optIn.isApproved()` to check for permissions because it abstracts  
       out the details of knowing exactly how the `permissions` list looks like. 
 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
});

// OR: You can pass in `shouldAutoSubscribe` as true, your callback will be used to subscribe  
to all OptIn events going forward:

function callback() { 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
} 
 
optIn.fetchPermissions(callback, true);
```

**`complete()` :**

>[!NOTE]
>
>À utiliser uniquement si vous avez utilisé le `shouldWaitForComplete` paramètre pour approuver ou refuser. L’API termine le processus d’approbation. Exemple : `adobe.optIn.complete()`.

**`approveAll()` :**

Approuve l’ensemble des catégories existantes.

**`denyAll()`**

Refuse l’ensemble des catégories existantes.

## Événements de l’objet Opt-in {#section-06f25b33cab54bafb053183e937fb710}

**`complete` :**

L’événement « complete » se déclenche une fois le processus d’approbation terminé. Si vous appelez l’approbation ou le refus sans transmettre `shouldWaitForComplete`, ou `approveAll`/ `denyAll`, cet événement se déclenche. Ou alors, si vous transmettez `shouldWaitForComplete`, cet événement se déclenche lors de l’appel de `complete`.

**Exemple**

```
<codeph>
  adobe.optIn.on("complete", callback); 
</codeph>
```
