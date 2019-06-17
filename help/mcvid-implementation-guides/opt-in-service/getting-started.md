---
description: Mettez en œuvre le service de souscription en tant que point de référence unique utilisé par les solutions Experience Cloud (désignées sous le nom de Catégories dans la souscription) pour déterminer si des cookies doivent être créés sur le périphérique d'un visiteur.
seo-description: Mettez en œuvre le service de souscription en tant que point de référence unique utilisé par les solutions Experience Cloud (désignées sous le nom de Catégories dans la souscription) pour déterminer si des cookies doivent être créés sur le périphérique d'un visiteur.
seo-title: Définition - Service de souscription
title: Définition - Service de souscription
uuid: f 1 c 27139-cef 2-4122-af 12-c 839 cfc 82 e 6 e
translation-type: tm+mt
source-git-commit: ae65e9c7da5ac9cbe22de3f956bcd7cbef2052a7

---


# Définition - Service de souscription{#setting-up-opt-in-service}

Mettez en œuvre le service de souscription en tant que point de référence unique utilisé par les solutions Experience Cloud (désignées sous le nom de Catégories dans la souscription) pour déterminer si des cookies doivent être créés sur le périphérique d&#39;un visiteur.

Le service de souscription est une bibliothèque JavaScript fournie avec [Experience Cloud ID (ECID)](https://marketing.adobe.com/resources/help/en_US/mcvid/) et existe dans le JS du visiteur dans l&#39;objet global `adobe` comme `adobe.optIn` objet. Le service de souscription installé vous permet de spécifier si un visiteur peut s&#39;abonner à des solutions Adobe à la fois ou pour présenter des solutions par ordre pour chaque autorisation. La fonctionnalité de gestion du consentement du service de souscription permet de mettre en œuvre diverses configurations en fonction de vos besoins spécifiques en matière de confidentialité.

Le service de souscription vous permet de spécifier si un visiteur peut s&#39;abonner à des solutions Adobe à la fois ou pour présenter des solutions par ordre pour chaque autorisation. Une fois le processus d’approbation terminé et enregistré par le client, l’ensemble des solutions Adobe peuvent récupérer les approbations visiteur de la CMP en réponse aux appels de consentement associés.

## Conditions préalables {#section-c39246f45e514c8ea9fdbe6f7ffa3ad0}

1. ECID version 4.0.

   [Téléchargez](https://github.com/Adobe-Marketing-Cloud/id-service/releases) la dernière mise à jour d’ECID.

1. Bibliothèques utilisées :

   * ECID 4.0 ou ultérieure
   * AppMeasurement 2.11 ou ultérieure
   * DIL 9.0
   * AT.js version 1.7.0
   * Extension Launch AT.js version 9.0
   * Pour Analytics, AppMeasurement 2.11 avec extension 1.6
   * Pour Target, extension 0.9.1

1. Se familiariser avec le framework de gestion de contenu que vous allez utiliser avec Opt-in et comprendre les conditions préalables supplémentaires.

   <!--
   For IAB, see here for additional pre-reqs.
   -->

1. Les besoins de confidentialité de votre société dépendent du degré de conformité au RGPD que vous souhaitez avoir. Vous devez savoir quelles bibliothèques les équipes chargées de la confidentialité de votre société sont prêtes à utiliser avec un consentement préalable.

Si vous utilisez [Adobe Launch](https://docs.adobelaunch.com/), profitez de l’ [Extension de souscription](../../mcvid-implementation-guides/opt-in-service/launch.md) pour configurer le service de souscription.

## Catégories de souscription {#section-9ab0492ab4414f0ca16dc08d3a905f47}

Les préférences d’un visiteur en matière d’opt-in dépendent d’une solution Adobe Experience Cloud, au sein de laquelle chaque solution est représentée par une catégorie. Les catégories sont fournies par l’objet `adobe.OptInCategories` où, par exemple, le composant ECID est représenté par `adobe.OptInCategories`. `ECID`. Voici la définition de `adobe.OptInCategories` :

Les paramètres d’opt-in sont gérés par catégorie. Chaque solution Experience Cloud est représentée par une catégorie.

```
adobe.OptInCategories = { 
    AAM: "aam", 
    TARGET: "target",  
    ANALYTICS: "aa", 
    ECID: "ecid", 
     
};
```

Le service de souscription permet de définir les préférences d&#39;autorisation des visiteurs par solution Adobe utilisée sur votre site. Cela comprend une bibliothèque pour la sauvegarde des paramètres d’un visiteur par catégorie approuvée. De plus, un flux séquentiel est pris en charge, où le processus d’approbation reçoit des préférences « confirmer » ou « refuser » pour chaque catégorie, chacune son tour. Vous pouvez définir les solutions ou catégories pour lesquelles demander le consentement, pour l’ensemble ou individuellement.
Toutes les bibliothèques côté client de solutions Adobe dépendent du service de souscription et ne génèrent aucun cookie, sauf si la solution a été accordée à la solution. Opt-in prend en charge plusieurs approches pour fournir et mettre à jour les paramètres de consentement pour le visiteur actuel. Cette section fournit des exemples pour définir les préférences de service de souscription. Voir la référence de l&#39;API [de souscription](../../mcvid-implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) pour obtenir la liste complète des fonctions et paramètres.

Les configurations de service de souscription sont fournies dans la `getInstance()` fonction JS du visiteur qui instancie `adobe` l&#39;objet global. Ce qui suit répertorie les paramètres [de configuration JS du visiteur](../../mcvid-implementation-guides/opt-in-service/api.md#section-d66018342baf401389f248bb381becbf) pour le service de souscription.

**Exemple de configuration de souscription dans l&#39;initialisation de`Visitor`l&#39;objet global**

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

**Gestion des modifications du consentement**

À tout moment lors de son passage sur votre site, un visiteur peut définir ses préférences pour la première fois ou modifier celles-ci à l’aide de votre CMP. Une fois le fichier JavaScript Visiteur initialisé avec les premiers paramètres, les autorisations du visiteur peuvent être modifiées. Voir [Modifications du consentement](../../mcvid-implementation-guides/opt-in-service/api.md#section-c3d85403ff0d4394bd775c39f3d001fc) pour obtenir une liste de gestion des fonctions de consentement.

<!--
<p> *** <b>sample code block </b>*** </p>
-->

## Processus de souscription {#section-70cd243dec834c8ea096488640ae20a5}

Le service de souscription prend en charge un flux de travail où les autorisations peuvent être collectées sur plusieurs cycles de requête et les préférences sont données un par un. En utilisant les fonctions suivantes et en stipulant *true* pour `shouldWaitForComplete`, votre solution peut collecter le consentement pour une catégorie ou pour un sous-ensemble de catégories parmi toutes celles qui existent, puis collecter le consentement pour la catégorie suivante ou le sous-ensemble de catégories suivant. A compter du premier appel, la `adobe.optIn.status` propriété *est en attente* jusqu&#39;à `adobe.optIn.complete()` ce qu&#39;elle soit appelée à la fin du flux. Une fois appelée, son état est défini sur *complete*.

```
adobe.optIn.approve(['AAM', 'ECID'], true); 
adobe.optIn.deny(['ANALYTICS'], true); 
adobe.optIn.complete();
```

Voir [Paramètres de configuration de processus](../../mcvid-implementation-guides/opt-in-service/api.md#section-2c5adfa5459c4e72b96d2693123a53c2).

## Inspection des autorisations d’Opt-in de votre visiteur {#section-f136a9024e054d84881e6667fb7c94eb}

Alors que vos visiteurs modifient leurs autorisations, vous devez connaître les autorisations résultantes pour synchroniser votre magasin de consentement avec les modifications apportées au service de souscription. Inspectez les préférences de votre visiteur à l’aide des [fonctions d’autorisation](../../mcvid-implementation-guides/opt-in-service/api.md#section-7fe57279b5b44b4f8fe47e336df60155). Par exemple :

**Échantillon de fetchPermissions**

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

Voir la [documentation sur l’API](../../mcvid-implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) pour plus de détails sur ces fonctions ou sur les autres fonctions, propriétés ou configurations mentionnées dans ce document.

## Stockage des préférences des visiteurs {#section-ef2884ae67e34879bf7c7c3372706c9f}

Le service de souscription fournit une option permettant de stocker les préférences de consentement adaptées à un environnement de développement ou à un environnement dans lequel il est impossible d&#39;utiliser une gestion de la relation client. La définition de la propriété `isOptInStorageEnabled` de configuration *comme vraie* déclenche le service de souscription pour créer un cookie sur le système du visiteur dans votre domaine.

L’objet `adobe.optIn` est sans état et ne fournit pas de mécanisme de stockage. Il est plutôt prévu que vous gériez les paramètres de consentement d’Adobe dans la plate-forme de gestion de contenu (CMP) existante, si celle-ci permet le stockage de données de consentement. Alternativement, vous pouvez stocker les préférences des visiteurs dans un cookie sur leur navigateur. Vous disposez de deux options pour fournir les préférences de l&#39;utilisateur au service de souscription :

* Si votre solution de persistance de consentement, qu&#39;il s&#39;agisse d&#39;un CMP ou d&#39;un cookie sur le navigateur du visiteur, autorise la récupération opportune des préférences du visiteur, vous pouvez les fournir au service de souscription pendant l&#39;initialisation du visiteur.
* Cependant, si la récupération peut être un processus long ou qu&#39;il est préférable dans un processus asynchrone, vous pouvez utiliser `approve()` la fonction du service pour fournir ces paramètres une fois qu&#39;ils ont été chargés avec succès.

