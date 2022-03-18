---
description: Les fonctions du service d’ID idSyncByURL et idSyncByDataSource vous permettent de mettre en œuvre manuellement une synchronisation des identifiants dans l’iFrame de publication de destination. Elles sont disponibles dans VisitorAPI.js 1.10 ou version ultérieure.
keywords: Service d’ID
title: Synchronisation des ID par URL ou source de données
exl-id: a22e6b47-00ff-4b51-9958-ddeccc1e507e
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: ht
source-wordcount: '239'
ht-degree: 100%

---

# Synchronisation des ID par URL ou source de données{#id-synchronization-by-url-or-data-source}

Les fonctions du service d’ID idSyncByURL et idSyncByDataSource vous permettent de mettre en œuvre manuellement une synchronisation des identifiants dans l’iFrame de publication de destination. Elles sont disponibles dans VisitorAPI.js 1.10 ou version ultérieure.

## Syntaxe, propriétés et macros {#section-90ac61617482463aaf4c57009b830332}

**Syntaxe**

<table id="table_ADC7501511914805A6A6B24B2DFEBA51"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Code </th> 
   <th colname="col2" class="entry"> Synchronise les ID utilisateur </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByURL(); </span> </p> </td> 
   <td colname="col2"> <p>Entre différents partenaires de données et <span class="keyword">Audience Manager</span> en utilisant une URL de synchronisation d’identifiant personnalisé. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByDataSource(); </span> </p> </td> 
   <td colname="col2"> <p>Si vous connaissez déjà le DPID et DPUUID et si vous voulez l’envoyer à <span class="keyword">Audience Manager</span> dans le format d’URL de synchronisation d’identifiant standard. </p> <p></p> </td> 
  </tr> 
 </tbody> 
</table>

**Propriétés**

Le tableau suivant répertorie et définit les propriétés disponibles pour les deux fonctions.

<table id="table_5343BE784E694C67B09A0A8878CF8001"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Nom </th> 
   <th colname="col2" class="entry"> Type </th> 
   <th colname="col3" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> Dpid </span> </td> 
   <td colname="col2"> Chaîne </td> 
   <td colname="col3"> <p>ID de fournisseur de données attribué par Audience Manager. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> dpuuid </span> </td> 
   <td colname="col2"> Chaîne </td> 
   <td colname="col3"> <p>ID unique du fournisseur de données pour l’utilisateur. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> minutesToLive </span> </td> 
   <td colname="col2"> Nombre </td> 
   <td colname="col3"> <p> <i>(Facultatif)</i> Définit l’heure d’expiration du cookie. Doit être un nombre entier. La valeur par défaut est de 20160 minutes (14 jours). </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> url </span> </td> 
   <td colname="col2"> Chaîne </td> 
   <td colname="col3"> <p>URL de destination. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Macros**

Les deux fonctions acceptent les macros suivantes :

* `%TIMESTAMP%` : génère un horodatage (en millisecondes). Utilisé pour la mise en cache.
* `%DID%` : insère l’identifiant Audience Manager pour l’utilisateur.
* `%HTTP_PROTO%` : définit le protocole de communication (`http` ou `https`).

## Exemple de code et résultat {#section-0115615c37584a19a2ab11e917c4e7e9}

Les deux fonctions renvoient `Successfully queued` en cas de réussite. Autrement, elles renvoient une chaîne contenant un message d’erreur.

### visitor.idSyncByURL

**Exemple de code**

```javascript
   //Instatiate Visitor
    var visitor = Visitor.getInstance
    ("MARKETING-CLOUD-ORG-ID-HERE",{}); 
   // Fires url with macros replaced 
    visitor.idSyncByURL({ 
    dpid: '24', // must be a string 
    url: '//su.addthis.com/red/usync?pid=16&puid=%DID%&url=%HTTP_PROTO%://
    dpm.demdex.net/ibs:dpid=420&dpuuid={{uid}}', 
    minutesToLive: 20160 // optional, defaults to 20160 minutes (14 days) });
```

**Exemple de résultat**

```
http://su.addthis.com/red/usync?pid=16&puid=28777806459181003670799219185178493848&url=http%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D
```

### visitor.idSyncByDataSource

**Exemple de code**

```javascript
  //Instantiate Visitor
   var visitor = Visitor.getInstance
   ("MARKETING-CLOUD-ORG-ID-HERE",{}); 
  // Fires 'http:/https:' + '//dpm.demdex.net/ibs:dpid=&dpuuid='
   visitor.idSyncByDataSource({ 
     dpid: '24', // must be a string
     dp     minutesToLive: 20160 // optional, defaults to 20160 minutes (14 days) });
```

**Exemple de résultat**

```
http://dpm.demdex.net/ibs:dpid=24&dpuuid=98765
```

>[!MORELIKETHIS]
>
>* [DIL idSync](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-instance-methods.html?lang=fr#idsync)

