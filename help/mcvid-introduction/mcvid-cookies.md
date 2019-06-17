---
description: Le service d’ID utilise l’ID d’organisation, le cookie AMCV d’Experience Cloud et un cookie demdex pour créer et stocker les identifiants uniques et persistants des visiteurs de votre site. Ces cookies permettent au service d’ID d’effectuer le suivi des visiteurs dans vos différents domaines et d’activer le partage de données entre différentes solutions Experience Cloud.
keywords: playstation ; Service d'ID
seo-description: Le service d’ID utilise l’ID d’organisation, le cookie AMCV d’Experience Cloud et un cookie demdex pour créer et stocker les identifiants uniques et persistants des visiteurs de votre site. Ces cookies permettent au service d’ID d’effectuer le suivi des visiteurs dans vos différents domaines et d’activer le partage de données entre différentes solutions Experience Cloud.
seo-title: Les cookies et le service Experience Cloud ID
title: Les cookies et le service Experience Cloud ID
uuid: c 5 cbd 235-37 ee -4605-8792-b 1 a 991 e 190
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Les cookies et le service Experience Cloud ID{#cookies-and-the-experience-cloud-id-service}

Le service d’ID utilise l’ID d’organisation, le cookie AMCV d’Experience Cloud et un cookie demdex pour créer et stocker les identifiants uniques et persistants des visiteurs de votre site. Ces cookies permettent au service d’ID d’effectuer le suivi des visiteurs dans vos différents domaines et d’activer le partage de données entre différentes solutions Experience Cloud.

## Comprendre les cookies du service d&#39;ID {#section-f438168beaec409ab8b2cc58bd021e26}

Le bon fonctionnement du service d’ID repose sur les cookies AMCV, AMCVS et Demdex. Ces cookies ne sont que des fichiers qui stockent les données utilisées par le service d’ID. Ces cookies du service d’ID ne sont ni dangereux, ni malveillants, ni différents des autres cookies propriétaires ou tiers stockés par un site web ou par un service dans un navigateur. Ces cookies suivent les mêmes règles que les autres cookies propriétaires ou tiers. Pour plus d&#39;informations sur les cookies utilisés par le service d&#39;ID, reportez-vous aux sections ci-dessous.

**Les cookies du service d&#39;ID**

* Définir et enregistrer un ID unique pour les visiteurs de votre site (le MID)
* Conserver cet ID unique afin que le service d’ID puisse collecter et partager des données avec d’autres solutions Experience Cloud
* Effectuer le suivi des utilisateurs dans vos domaines. Cependant, cela nécessite que vous possédiez ces autres domaines et que le code du service d’ID soit déployé sur ces derniers.

** Ce que ne peuvent pas faire les ookies du service d&#39;ID**

* Stocker, transmettre ou exécuter des virus informatiques
* Accéder ou stocker des informations d’identification personnelle comme votre adresse e-mail
* Contrôler le matériel informatique ou les logiciels
* Rendre les ordinateurs instables ou causer des problèmes de performance
* Effectuer le suivi des utilisateurs sur des sites qui n’utilisent pas le service d’ID

## Cookie AMCV {#section-c55af54828dc4cce89f6118655d694c8}

Attributs suivants du cookie défini par le service d&#39;ID.

**Nom**

Le nom du cookie AMCV suit la syntaxe `AMCV_<variable name>@AdobeOrg`. Dans le nom, `<variable name>` les éléments sont des espaces réservés pour une partie de votre ID d&#39;organisation Experience Cloud. Cet ID est transmis au serveur de collecte de données par la fonction `Visitor.getInstance` dans le code du service d’ID.

Un nom de cookie entièrement formé doit ressembler à celui-ci :

```
AMCV_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Contenu**

Le cookie AMCV contient l’identifiant visiteur Experience Cloud ou MID. The MID is stored in a key-value pair that follows this syntax, `mid|<Experience Cloud ID>`.

Une paire clé-valeur entièrement formée doit être identique à celle-ci :

```
mid|20265673158980419722735089753036633573
```

Cet identifiant persistant permet le partage des données entre les solutions.

**Domaine**

Le cookie AMCV est défini sur le domaine propriétaire d’un navigateur. Il est donc défini dans le domaine du site actuellement visité par un utilisateur. Le code du service d’ID et d’autres bibliothèques de code Experience Cloud peuvent ainsi lire le MID stocké dans le cookie AMCV.

Toutefois, comme le cookie AMCV est défini dans le domaine propriétaire, il ne peut pas être utilisé pour suivre et identifier les visiteurs dans les différents domaines. Le service d’ID repose sur l’ID d’organisation et l’ID demdex pour renvoyer le MID correct lorsqu’un visiteur du site accède à un autre domaine.

## Cookie AMCVS {#section-92a9454f1ac645948f9059b9fad928bf}

**Nom**

Le nom du cookie AMCVS suit la syntaxe `AMCVS_####@AdobeOrg`. Dans le nom, les éléments #### représentent des espaces réservés à une partie de l’ID d’organisation d’Experience Cloud. Cet ID est transmis au serveur de collecte de données par `theVisitor.getInstance` fonction dans le code du service d&#39;ID.

Un nom de cookie entièrement formé doit ressembler à celui-ci :

```
AMCVS_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Contenu**

Le cookie AMCVS sert de drapeau indiquant que la session a été initialisée. Sa valeur est toujours `1` et interrompue lorsque la session est terminée.

**Domaine**

Le cookie AMCVS est défini sur le domaine propriétaire d’un navigateur. Il est donc défini dans le domaine du site actuellement visité par un utilisateur.

![](assets/AMCVS-cookie.png)

## Cookie demdex {#section-7ff7d96d6e4141b08a84a75a63d7814c}

Le tableau ci-dessous répertorie et définit quelques attributs importants du cookie demdex.

<table id="table_18E3CAF3550E4BB6A199736AACE39202"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Attribut </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Nom</b> </p> </td> 
   <td colname="col2"> <p>Le nom du cookie est « demdex ». </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Contenu</b> </p> </td> 
   <td colname="col2"> <p>Le cookie demdex contient l’ID demdex qui est généré par le serveur de collecte de données. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Domaine</b> </p> </td> 
   <td colname="col2"> <p>Le cookie demdex est défini sur le domaine demdex.net tiers dans le navigateur. Ce domaine est distinct du site actuellement visité par un utilisateur. </p> <p>Contrairement au cookie AMCV propriétaire, le cookie et l’ID demdex persistent dans les différents domaines. L’ID demdex et votre ID d’organisation sont les valeurs communes qui permettent au service d’ID de renvoyer et d’identifier un visiteur du site avec l’identifiant visiteur correct. </p> </td> 
  </tr> 
 </tbody> 
</table>

Pour plus d&#39;informations, voir [Présentation des appels au domaine Demdex](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html).

## Génération de l’Experience Cloud ID {#section-15f69c0bac394b4b9966a23fbc586d17}

L’Experience Cloud ID (MID) est dérivé de manière mathématique de l’ID d’organisation et de l’ID demdex. Tant que ces identifiants restent constants, la génération du MID approprié pour un utilisateur spécifique est simplement un problème mathématique. Avec les mêmes ID d’organisation et ID demdex, vous obtenez chaque fois la même valeur MID. Ainsi, le service d’ID peut effectuer le suivi des visiteurs sur les domaines que vous contrôlez et que vous avez configurés au moyen du code du service d’ID.

Le service d’ID commence à créer un MID lorsque votre page se charge. Au cours de ce processus, le code fourni par la bibliothèque de code `visitorAPI.js` envoie votre ID d’organisation dans un appel d’événement au service d’ID. Le service d’ID crée et renvoie le MID et un ID demdex dans les cookies AMCV et demdex respectivement.

## Étapes suivantes {#section-8db1727a63bc4ff68b495f270315d453}

Voir [Comment le service Experience Cloud ID demande et définit des identifiants….](../mcvid-introduction/mcvid-id-request.md#concept-2caacebb1d244402816760e9b8bcef6a)