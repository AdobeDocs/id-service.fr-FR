---
description: Il s’agit d’une API asynchrone qui renvoie les identifiants pour Analytics, le service d’ID, le droit d’opposition à la collecte de données, l’emplacement géographique et le contenu d’objet blob de métadonnées par défaut. Vous pouvez également contrôler les ID que vous souhaitez renvoyer à l’aide de l’énumération facultative visitor.FIELDS.
keywords: Service d’ID
title: getVisitorValues
exl-id: bd023e8d-a804-4205-989f-e1e58080b63c
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: ht
source-wordcount: '407'
ht-degree: 100%

---

# getVisitorValues{#getvisitorvalues}

Il s’agit d’une API asynchrone qui renvoie les identifiants pour Analytics, le service d’ID, le droit d’opposition à la collecte de données, l’emplacement géographique et le contenu d’objet blob de métadonnées par défaut. Vous pouvez également contrôler les ID que vous souhaitez renvoyer à l’aide de l’énumération facultative visitor.FIELDS.

Contenu :

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-5aebe3907b2b46e997f45a1d1ed35c09" format="dita" scope="local"> Syntaxe </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-36a31683558742a5915db3a391e09f7b" format="dita" scope="local"> Cas d’utilisation 1 : demander le jeu de données par défaut </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-467b2f4e513344c89b7332b05f6f59f3" format="dita" scope="local"> Cas d’utilisation 2 : demander le jeu de données personnalisé </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5" format="dita" scope="local"> Paramètres de réponse définis </a> </li> 
</ul>

## Syntaxe {#section-5aebe3907b2b46e997f45a1d1ed35c09}

Cette fonction utilise la syntaxe suivante (le format italique représente un espace réservé pour une variable) : ` var *`valeurs`* = visitor.getVisitorValues (callback, [visitor.FIELDS. *`type d’ID`*, visitor.FIELDS. *`type d’ID`*]);`

Dans les paramètres de la fonction :

* ` *`callback`*` représente votre propre code de rappel qui reçoit les ID renvoyés.
* *(Facultatif)* ` visitor.FIELDS. *`type d’ID`*` est une énumération permettant d’indiquer les [valeurs d’ID](../../library/get-set/getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5) que vous souhaitez que cette fonction renvoie.

Pour plus d’informations, voir les cas d’utilisation et définitions suivants.

## Cas d’utilisation 1 : demander le jeu de données par défaut {#section-36a31683558742a5915db3a391e09f7b}

Ce code renvoie le jeu de données standard. Votre demande et votre réponse peuvent ressembler aux exemples suivants.

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{...}); 
   
//Add your callback to the GET method to return IDs and data. 
visitor.getVisitorValues(visitorIdsCallback);
```

Dans l’exemple de réponse par défaut, certaines valeurs ont été raccourcies à des fins de démonstration.

```js
//Formatted IDs in JSON response 
{ 
    MCMID: 'mid-1234', 
    MCOPTOUT: 'isoptedout-true', 
    MCAID: 'aid-1234', 
    MCAAMLH: 7, 
    MCAAMB: 'hgfe54236786oygj' 
}
```

## Cas d’utilisation 2 : demander le jeu de données personnalisé {#section-467b2f4e513344c89b7332b05f6f59f3}

Ce code utilise un tableau facultatif pour renvoyer un jeu d’ID spécifique à l’aide de `visitor.FIELDS` l’énumération. Dans ce cas, nous voulons uniquement l’Experience Cloud ID (MCID) et l’Analytics ID (MCAID) du visiteur. Votre demande et votre réponse peuvent ressembler aux exemples suivants.

```js
//Call the ID service 
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here", { ... });

// Add an optional array to specify which IDs you want to return. 
visitor.getVisitorValues(visitorIdsCallback, [visitor.FIELDS.MCMID, visitor.FIELDS.MCAID]);
```

L’exemple de réponse personnalisé renvoie uniquement les ID spécifiés dans la requête.

```js
//Formatted IDs in JSON response 
{ 
    MCMID: 'mid-1234', 
    MCAID: 'aid-4321' 
}
```

## Paramètres de réponse définis {#section-4c4c300167694c6fbff1d6c612f372b5}

Le tableau suivant répertorie et définit les paramètres de réponse. Il s’agit également de toutes les valeurs de `visitor.FIELDS` l’énumération. Remarque : cette méthode renvoie une chaîne vide si aucune valeur n’est définie pour une variable particulière.

<table id="table_32D0FEEA76CE4F298EED4B8F5C644232"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Valeur </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAAMB </span> </p> </td> 
   <td colname="col2"> <p>Métadonnées <span class="keyword">Audience Manager</span> chiffrées connues sous le nom d’objet blob. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAAMLH </span> </p> </td> 
   <td colname="col2"> <p>ID de la région de collecte de données. Il s’agit d’un identifiant numérique pour l’emplacement géographique d’un centre de données de service d’ID en particulier. </p> <p>Voir <a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html?lang=fr" format="https" scope="external"> ID de zone géographique, emplacements et noms d’hôte du serveur de collecte de données </a> (DCS Region IDs, Locations, and Host Names) et <a href="../../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c" format="dita" scope="local"> getLocationHint </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAID </span> </p> </td> 
   <td colname="col2"> <p><span class="keyword">Analytics</span> ID du visiteur. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCMID </span> </p> </td> 
   <td colname="col2"> <p>Experience Cloud ID du visiteur. </p> <p>Voir <a href="../../introduction/cookies.md" format="dita" scope="local"> Cookies et service Experience Cloud Identity </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCOPTOUT </span> </p> </td> 
   <td colname="col2"> <p>Indicateur qui indique si un visiteur a exercé son droit d’opposition à la collecte de données. </p> <p>Les valeurs sont les suivantes : </p> <p> 
     <ul id="ul_E82431DE12B449F8822499364B363798"> 
      <li id="li_2BAB7C15A38A408E8FC4B85E70B66E46"> <span class="codeph"> 'isoptedout-true'</span> : un visiteur a exercé son droit d’opposition à la collecte de données. </li> 
      <li id="li_BB80AE4CEBC44166BC04428B212FEF51"> <span class="codeph"> 'isoptedout-true'</span> : un visiteur n’a pas exercé son droit d’opposition à la collecte de données. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
