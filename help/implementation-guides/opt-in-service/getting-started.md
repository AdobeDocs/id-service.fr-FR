---
description: Mettez le service Opt-in en œuvre en tant que seul point de référence pris en compte par les solutions Experience Cloud (Catégories dans Opt-in) pour décider de la création ou non de cookies sur l’appareil d’un visiteur.
seo-description: Mettez le service Opt-in en œuvre en tant que seul point de référence pris en compte par les solutions Experience Cloud (Catégories dans Opt-in) pour décider de la création ou non de cookies sur l’appareil d’un visiteur.
seo-title: Configuration du service Opt-in
title: Configuration du service Opt-in
uuid: f1c27139-cef2-4122-af12-c839cfc82e6e
exl-id: 6e8a6531-9924-4523-a842-cb4614a7a7a0
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '941'
ht-degree: 100%

---

# Configuration du service Opt-in {#setting-up-opt-in-service}

Mettez le service Opt-in en œuvre en tant que seul point de référence pris en compte par les solutions Experience Cloud (Catégories dans Opt-in) pour décider de la création ou non de cookies sur l’appareil d’un visiteur.

Le service Opt-in est une bibliothèque JavaScript inclue avec Experience Cloud ID (ECID) et existe dans le JavaScript du visiteur dans l’objet `adobe` global comme objet `adobe.optIn`. Le service Opt-in installé vous permet de définir si un visiteur peut donner son consentement pour toutes les solutions Adobe à la fois ou pour les solutions actuelles l’une après l’autre. Le service Opt-in, fonctionnalité de gestion de contenu, vous permet de mettre en œuvre plusieurs configurations pour vos besoins spécifiques de confidentialité.

Le service Opt-in vous permet de définir si un visiteur peut donner son consentement pour toutes les solutions Adobe à la fois ou pour les solutions actuelles l’une après l’autre. Une fois le processus d’approbation terminé et enregistré par le client, l’ensemble des solutions Adobe peuvent récupérer les approbations visiteur de la CMP en réponse aux appels de consentement associés.

## Conditions préalables   {#section-c39246f45e514c8ea9fdbe6f7ffa3ad0}

1. ECID version 4.0.

   [Téléchargez](https://github.com/Adobe-Marketing-Cloud/id-service/releases) la dernière mise à jour d’ECID.

1. Bibliothèques d’aide :

   * ECID 4.0 ou une version ultérieure
   * AppMeasurement 2.11 ou une version ultérieure
   * DIL 9.0
   * AT.js version 1.7.0
   * Extension Launch AT.js version 9.0
   * Pour Analytics, App Measurement 2.11 avec l’extension 1.6
   * Pour Target, l’extension 0.9.1

1. Améliorez votre connaissance du cadre de gestion du consentement que vous utiliserez avec l’Opt-in et découvrez toutes les conditions préalables supplémentaires.

   <!--
   For IAB, see here for additional pre-reqs.
   -->

1. Les besoins de confidentialité de votre société dépendent du degré de conformité au RGPD que vous souhaitez avoir. Découvrez les bibliothèques que les équipes de protection de la vie privée de votre société peuvent utiliser à l’état de consentement préalable.

Si vous utilisez [Adobe Launch](https://docs.adobe.com/content/help/fr-FR/launch/using/overview.html), tirez parti de l’[extension Opt-in](../../implementation-guides/opt-in-service/launch.md) pour configurer le service Opt-in.

## Catégories Opt-in {#section-9ab0492ab4414f0ca16dc08d3a905f47}

Les préférences d’un visiteur en matière d’opt-in dépendent d’une solution Adobe Experience Cloud, au sein de laquelle chaque solution est représentée par une catégorie. Les catégories sont fournies par `adobe.OptInCategories` l’objet où, par exemple, le composant ECID est représenté par `adobe.OptInCategories`. `ECID`. Voici la définition de `adobe.OptInCategories` :

Les paramètres d’opt-in sont gérés par catégorie. Chaque solution Experience Cloud est représentée par une catégorie.

```
adobe.OptInCategories = { 
    AAM: "aam", 
    TARGET: "target",  
    ANALYTICS: "aa", 
    ECID: "ecid", 
     
};
```

Le service Opt-in vous permet de définir les préférences d’autorisation des visiteurs pour chaque solution Adobe utilisée sur votre site. Cela comprend une bibliothèque pour la sauvegarde des paramètres d’un visiteur par catégorie approuvée. De plus, un flux séquentiel est pris en charge, où le processus d’approbation reçoit des préférences « confirmer » ou « refuser » pour chaque catégorie, chacune son tour. Vous pouvez définir les solutions ou catégories pour lesquelles demander le consentement, pour l’ensemble ou individuellement. 
L’ensemble des bibliothèques côté client des solutions Adobe dépend du service Opt-in. Elles ne génèrent pas de cookie, sauf si l’autorisation a été donnée pour la solution. Opt-in prend en charge plusieurs approches pour fournir et mettre à jour les paramètres de consentement pour le visiteur actuel. Cette section présente des exemples de définition des préférences du service Opt-in. Voir les [Références de l’API d’Opt-in](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) pour obtenir la liste complète des fonctions et paramètres.

Les configurations du service Opt-in sont fournies dans la `getInstance()` fonction du fichier JavaScript Visiteur, qui instancie `adobe` l’objet global. Vous trouverez ci-après les [paramètres de configuration](../../implementation-guides/opt-in-service/api.md#section-d66018342baf401389f248bb381becbf) JavaScript Visiteur pour le service Opt-in.

**Exemple de configuration d’Opt-in lors de l’initialisation de `Visitor` l’objet global**

```
// FORMAT: Object<adobe.OptInCategories enum: boolean> 
var preOptInApprovalsConfig = {}; 
preOptInApprovals[adobe.OptInCategories.ANALYTICS] = true; 
  
// FORMAT: Object<adobe.OptInCategories enum: boolean> 
// If you are storing the OptIn permissions on your side (in a cookie you manage or in a CMP), 
// you have to provide those permissions through the previousPermissions config. 
// previousPermissions will overwrite preOptInApprovals. 
var previousPermissionsConfig = {}; 
previousPermissionsConfig[adobe.OptInCategories.AAM] = true; 
previousPermissionsConfig[adobe.OptInCategories.ANALYTICS] = false; 
  
Visitor.getInstance("YOUR_ORG_ID", { 
    "doesOptInApply": true, // NOTE: This can be a function that evaluates to true or false. 
    "preOptInApprovals": preOptInApprovalsConfig, 
    "previousPermissions": previousPermissionsConfig, 
    "isOptInStorageEnabled": true 
});
```

**Gestion des modifications apportées au consentement**

À tout moment lors de son passage sur votre site, un visiteur peut définir ses préférences pour la première fois ou modifier celles-ci à l’aide de votre CMP. Une fois le fichier JavaScript Visiteur initialisé avec les premiers paramètres, les autorisations du visiteur peuvent être modifiées. Voir [Modifications du consentement](../../implementation-guides/opt-in-service/api.md#section-c3d85403ff0d4394bd775c39f3d001fc) pour obtenir la liste des fonctions de gestion du consentement.

<!--
<p> *** <b>sample code block </b>*** </p>
-->

## Processus d’Opt-in {#section-70cd243dec834c8ea096488640ae20a5}

Le service Opt-in prend en charge un processus avec lequel des autorisations peuvent être collectées sur plus d’un cycle de requêtes et les préférences sont délivrées une par une. En utilisant les fonctions suivantes et en stipulant *true* pour `shouldWaitForComplete`, votre solution peut collecter le consentement pour une catégorie ou pour un sous-ensemble de catégories parmi toutes celles qui existent, puis collecter le consentement pour la catégorie suivante ou le sous-ensemble de catégories suivant. La propriété `adobe.optIn.status` démarre au premier appel et est mise *en attente* jusqu’à ce que `adobe.optIn.complete()` soit appelée en fin de flux. Une fois appelée, son état est défini sur *complete*.

```
adobe.optIn.approve(['AAM', 'ECID'], true); 
adobe.optIn.deny(['ANALYTICS'], true); 
adobe.optIn.complete();
```

Voir les [Paramètres de configuration du workflow](../../implementation-guides/opt-in-service/api.md#section-2c5adfa5459c4e72b96d2693123a53c2).

## Inspection des autorisations d’Opt-in de votre visiteur {#section-f136a9024e054d84881e6667fb7c94eb}

Lorsque vos visiteurs modifient leurs autorisations, vous avez besoin d’informations sur les autorisations qui résultent de ces modifications, afin de synchroniser le stockage des consentements avec les modifications apportées au service Opt-in. Inspectez les préférences de vos visiteurs à l’aide des [fonctions d’autorisations](../../implementation-guides/opt-in-service/api.md#section-7fe57279b5b44b4f8fe47e336df60155), par exemple :

**Exemple fetchPermissions**

```
optIn.fetchPermissions(function (permissions) { 
    // Here you can check if your category has been approved or not. 
    // We recommend using optIn.isApproved() to check for permissions because it abstracts out the details of knowing exactly how the permissions list looks like. 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
});

OR: You can pass in shouldAutoSubscribe as true, your callback will be used to subscribe to all OptIn events going forward:

function callback() { 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
}

optIn.fetchPermissions(callback, true);
```

Consultez la [documentation sur l’API](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) pour plus de détails sur ces fonctions et sur d’autres, ainsi que sur les propriétés ou les configurations mentionnées dans ce document.

## Stockage des préférences des visiteurs {#section-ef2884ae67e34879bf7c7c3372706c9f}

Le service Opt-in fournit une option de stockage des préférences de consentement adaptée à un environnement de développement ou à un environnement dans lequel l’utilisation d’un CRM est impossible. Le fait de définir la propriété de configuration `isOptInStorageEnabled` sur *true* entraîne le service Opt-in à créer un cookie sur le système du visiteur dans votre domaine.

`adobe.optIn` L’objet est sans état et ne fournit pas de mécanisme de stockage. Il est plutôt prévu que vous gériez les paramètres de consentement d’Adobe dans la plate-forme de gestion de contenu (CMP) existante, si celle-ci permet le stockage de données de consentement. Alternativement, vous pouvez stocker les préférences des visiteurs dans un cookie sur leur navigateur. Deux options s’offrent à vous pour transmettre les préférences d’un utilisateur au service Opt-in :

* Si votre solution de consentement permanente, que ce soit une CMP ou un cookie sur le navigateur du visiteur, autorise l’extraction opportune des préférences d’un visiteur, vous pouvez transmettre celles-ci au service Opt-in lors de l’initialisation du visiteur.
* Cependant, lorsque l’extraction risque de durer un certain temps et qu’elle peut par ailleurs servir de processus asynchrone, vous pouvez utiliser la `approve()` fonction pour fournir ces paramètres une fois qu’ils sont bien chargés.
