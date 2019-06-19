---
description: Cette propriété définit l’identifiant du conteneur de la source de données que vous souhaitez utiliser pour les synchronisations des identifiants.
keywords: Service d’identification
seo-description: Cette propriété définit l’identifiant du conteneur de la source de données que vous souhaitez utiliser pour les synchronisations des identifiants.
seo-title: idSyncContainerID
title: idSyncContainerID
uuid: e 35 dc 48 b -1 aa 1-41 e 3-91 c 1-ef 1 e 9 d 2 d 8 b 90
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# idSyncContainerID{#idsynccontainerid}

Cette propriété définit l’identifiant du conteneur de la source de données que vous souhaitez utiliser pour les synchronisations des identifiants.

Contenu :

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-b0c50732b1c84bed8616e82e8e83d58c" format="dita" scope="local"> Syntaxe et exemple de code </a> </li> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-6aed44fbe9d6401a8f912cb0d98339a7" format="dita" scope="local">Que sont les conteneurs et quand les utiliser ?</a> </li> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-f283cb69c8de4348b5316cc4e02a3e9e" format="dita" scope="local"> Définition des identifiants de conteneur lorsque vous utilisez DIL et VisitorAPI.js </a> </li> 
</ul>

## Syntaxe et exemple de code {#section-b0c50732b1c84bed8616e82e8e83d58c}

**Syntaxe :**` idSyncContainerID: *`valeur de l&#39;ID du conteneur`*`

**Exemple de code :**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Set container ID 
   idSyncContainerID:80 
});
```

## Que sont les conteneurs et quand les utiliser ? {#section-6aed44fbe9d6401a8f912cb0d98339a7}

**Conteneurs**

Les conteneurs sont des objets créés [!DNL Audience Manager]par. Bien qu’ils ne soient pas accessibles en dehors d’Audience Manager, les conteneurs répertorient toutes les sources de données qui :

* sont disponibles, mais non utilisées pour la synchronisation des identifiants ;
* sont utilisées pour la synchronisation des identifiants.

Même si vous n’êtes pas un client d’[!DNL Audience Manager], votre compte comporte ces conteneurs si vous échangez des identifiants avec différentes sources de données sur différentes pages de votre domaine. En effet, [!DNL Audience Manager] fournit la technologie et la fonctionnalité back-end qui permettent la synchronisation des identifiants.

**Cas d’utilisation**

Selon votre situation, vous pouvez, ou non, avoir besoin d’ajouter cette configuration au code de votre service d’ID.

<table id="table_48621F343C7F4760A75F6BCC2DB2DA20"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Condition </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Non requis</b> </p> </td> 
   <td colname="col2"> <p>Vous n’avez pas besoin d’utiliser cette configuration si : </p> <p> 
     <ul id="ul_4D6F794CD65C43D0BEFBA6F5DE420C2E"> 
      <li id="li_0F048A6AC7BE4450AFA1B20B1AC25808">Vous utilisez le service d’ID avec une solution <span class="keyword">Experience Cloud</span> et n’effectuez pas de synchronisation des identifiants avec d’autres sources de données. Dans ce cas, votre compte comporte un conteneur par défaut avec l’identifiant 0 et aucune action n’est requise. </li> 
      <li id="li_5657D64D9406407D9B4DB7D8BE4F8EE4">Toutes vos sources de données sont incluses dans ce seul conteneur. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Requis</b> </p> </td> 
   <td colname="col2"> <p>Vous devez utiliser cette configuration lorsque l’ensemble des conditions suivantes s’appliquent : </p> <p> 
     <ul id="ul_9AFD14FC5A2745F7BD7BE7B64545DA62"> 
      <li id="li_04F0EFBBD71B43608CAAA7E7409D33FE">Vous n’utilisez pas <span class="keyword">Audience Manager </span>. </li> 
      <li id="li_4BFA6DC76CE9455EBBC337FD2FE820BF">Vous devez synchroniser les identifiants avec d’autres sources de données organisées par conteneurs. </li> 
      <li id="li_731DA5D1CBF244F8BEBE57C0E2EBA713">Vous devez synchroniser les identifiants avec les sources de données de différents conteneurs sur différentes pages de votre domaine. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Définition des identifiants de conteneur lorsque vous utilisez DIL et VisitorAPI.js {#section-f283cb69c8de4348b5316cc4e02a3e9e}

Si vous avez déployé [!DNL DIL]*et* VisitorAPI.js sur la même page :

* Le code du service d’identification des visiteurs a la priorité sur DIL pour les synchronisations des identifiants.
* Définissez la configuration `idSyncContainerID` uniquement dans le code du service d’ID.

