---
description: Le service d’ID utilise l’ID d’organisation, le cookie AMCV d’Experience Cloud et un cookie demdex pour créer et stocker les identifiants uniques et persistants des visiteurs de votre site. Ces cookies permettent au service d’ID d’effectuer le suivi des visiteurs dans vos différents domaines et d’activer le partage de données entre différentes solutions Experience Cloud.
keywords: playstation ; service d’ID
seo-description: Le service d’ID utilise l’ID d’organisation, le cookie AMCV d’Experience Cloud et un cookie demdex pour créer et stocker les identifiants uniques et persistants des visiteurs de votre site. Ces cookies permettent au service d’ID d’effectuer le suivi des visiteurs dans vos différents domaines et d’activer le partage de données entre différentes solutions Experience Cloud.
seo-title: Cookies et service Experience Cloud Identity
title: Cookies et service Experience Cloud Identity
uuid: c5cbd235-37ee-4605-8792-b1a991e190ad
exl-id: 727c6381-56b9-44b8-8e59-355d072769be
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '997'
ht-degree: 100%

---

# Cookies et service Experience Cloud Identity {#cookies-and-the-experience-cloud-id-service}

Le service d’ID utilise l’ID d’organisation, le cookie AMCV d’Experience Cloud et un cookie demdex pour créer et stocker les identifiants uniques et persistants des visiteurs de votre site. Ces cookies permettent au service d’ID d’effectuer le suivi des visiteurs dans vos différents domaines et d’activer le partage de données entre différentes solutions Experience Cloud.

## Signification des cookies du service d’ID {#section-f438168beaec409ab8b2cc58bd021e26}

Le bon fonctionnement du service d’ID repose sur les cookies AMCV, AMCVS et Demdex. Ces cookies ne sont que des fichiers qui stockent les données utilisées par le service d’ID. Ces cookies du service d’ID ne sont ni dangereux, ni malveillants, ni différents des autres cookies propriétaires ou tiers stockés par un site web ou par un service dans un navigateur. Ces cookies suivent les mêmes règles que les autres cookies propriétaires ou tiers. Reportez-vous aux sections ci-dessous pour plus d’informations sur les cookies utilisés par le service d’ID.

### Ce que peuvent faire les cookies du service d’ID

* Définir et enregistrer un ID unique pour les visiteurs de votre site (le MID).
* Conserver cet ID unique afin que le service d’ID puisse collecter et partager des données avec d’autres solutions Experience Cloud.
* Effectuez le suivi des utilisateurs sur l’ensemble de vos domaines. Toutefois, cela nécessite que vous possédiez ces autres domaines et que le code du service d’ID soit déployé sur eux.

### Ce que ne peuvent pas faire les cookies du service d’ID

* Stocker, transmettre ou exécuter des virus informatiques.
* Accéder ou stocker des informations d’identification personnelle comme votre adresse e-mail.
* Contrôler le matériel informatique ou les logiciels.
* Rendre les ordinateurs instables ou causer des problèmes de performance.
* Effectuer le suivi des utilisateurs sur des sites qui n’utilisent pas le service d’ID.

## Cookie AMCV {#section-c55af54828dc4cce89f6118655d694c8}

Les attributs suivants du cookie défini par le service d’ID.

**Nom**

Le nom du cookie AMCV suit la syntaxe `AMCV_<variable name>@AdobeOrg`. Dans le nom, les `<variable name>` éléments représentent des espaces réservés à une partie de l’ID d’organisation d’Experience Cloud. Cet ID est transmis au serveur de collecte de données par la `Visitor.getInstance` fonction dans le code du service d’ID.

Un nom de cookie entièrement formé doit ressembler à celui-ci :

```
AMCV_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Contenu**

Le cookie AMCV contient l’ID de visiteur Experience Cloud ou MID. Le MID est stocké dans une paire clé-valeur qui suit la syntaxe suivante, `mid|<Experience Cloud ID>`.

Une paire clé-valeur entièrement formée doit être identique à celle-ci :

```
mid|20265673158980419722735089753036633573
```

Cet identifiant persistant permet le partage de données entre solutions.

**Domaine**

Le cookie AMCV est défini sur le domaine propriétaire d’un navigateur. Cela signifie qu’il est défini dans le domaine du site actuellement visité par un utilisateur. Ainsi, le code du service d’ID et d’autres bibliothèques de code Experience Cloud peuvent lire le MID stocké dans le cookie AMCV.

Cependant, comme le cookie AMCV est défini dans le domaine propriétaire, il ne peut pas être utilisé pour effectuer le suivi et identifier des utilisateurs sur différents domaines. Le service d’ID utilise plutôt l’ID d’organisation et l’ID demdex pour renvoyer le MID correct lorsqu’un visiteur de site accède à un autre domaine.

## Cookie AMCVS {#section-92a9454f1ac645948f9059b9fad928bf}

**Nom**

Le nom du cookie AMCVS suit la syntaxe `AMCVS_####@AdobeOrg`. Dans le nom, les éléments #### représentent des espaces réservés à une partie de l’ID d’organisation d’Experience Cloud. Cet ID est transmis au serveur de collecte de données par la `theVisitor.getInstance` fonction dans le code du service d’ID.

Un nom de cookie entièrement formé doit ressembler à celui-ci :

```
AMCVS_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Contenu**

Le cookie AMCVS sert de drapeau indiquant que la session a été initialisée. Sa valeur est toujours `1` et s’interrompt une fois la session terminée.

**Domaine**

Le cookie AMCVS est défini sur le domaine propriétaire d’un navigateur. Cela signifie qu’il est défini dans le domaine du site actuellement visité par un utilisateur.

![](assets/AMCVS-cookie.png)

## Cookie demdex {#section-7ff7d96d6e4141b08a84a75a63d7814c}

Le tableau suivant liste et définit certains attributs importants du cookie demdex.

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
   <td colname="col2"> <p>Le cookie demdex contient l’ID demdex, qui est généré par le serveur de collecte de données. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Domaine</b> </p> </td> 
   <td colname="col2"> <p>Le cookie demdex est défini sur le domaine demdex.net tiers dans le navigateur. Ce domaine est distinct du site actuellement visité par un utilisateur. </p> <p>Contrairement au cookie AMCV propriétaire, le cookie et l’ID demdex persistent dans les différents domaines. L’ID demdex et l’ID d’organisation sont les valeurs fréquentes qui permettent au service d’ID de renvoyer et d’identifier un visiteur de site avec l’ID de visiteur approprié. </p> </td> 
  </tr> 
 </tbody> 
</table>

Pour plus d’informations connexes, voir [Signification des appels vers le domaine Demdex](https://docs.adobe.com/content/help/fr-FR/audience-manager/user-guide/reference/demdex-calls.html).

## Génération de l’Experience Cloud ID {#section-15f69c0bac394b4b9966a23fbc586d17}

L’Experience Cloud ID (MID) est dérivé de manière mathématique de l’ID d’organisation et de l’ID demdex. Tant que ces identifiants restent constants, la génération du MID approprié pour un utilisateur spécifique est simplement un problème mathématique. Avec les mêmes ID d’organisation et ID demdex, vous obtenez à chaque fois la même valeur MID. Cela permet au service d’ID de suivre les visiteurs entre les domaines que vous contrôlez et que vous avez configurés avec le code du service d’ID.

Le service d’ID commence la création d’un MID au fur et à mesure du chargement de votre page. Au cours de ce processus, le code fourni par la `visitorAPI.js` bibliothèque de code envoie votre ID d’organisation dans un appel d’événement au service d’ID. Le service d’ID crée et renvoie le MID et un ID demdex dans les cookies AMCV et demdex respectivement.

## Indicateurs de cookies

Le tableau suivant décrit les indicateurs des cookies d’Experience Cloud :

| Cookie (défini par) | httpOnly | Sécurisé | SameSite |
|--- |--- |--- |--- |
| demdex (réponse http) | Non | Oui | &quot;Aucun&quot; |
| AMCV (JavaScript) | Non | Configurable | Unset (par défaut : Lax) |
| AMCVS (JavaScript) | Non | Configurable | Unset (par défaut : Lax) |

*Remarque : pour plus d’informations sur la configuration du cookie AMCV et AMCVS avec des attributs sécurisés, voir la rubrique relative à [secureCookie](https://docs.adobe.com/content/help/fr-FR/id-service/using/id-service-api/configurations/securecookie.html).*

## Étapes suivantes {#section-8db1727a63bc4ff68b495f270315d453}

Consultez la section [Requête et définition d’ID par le service Experience Cloud Identity...](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a).
