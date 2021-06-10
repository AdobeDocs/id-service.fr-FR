---
description: Une configuration booléenne facultative permet de déterminer si le service d’ID envoie (ou n’envoie pas) des données à Adobe Experience Cloud Device Co-op.
keywords: Service d’ID
title: isCoopSafe
exl-id: 827f7819-9f95-4e8d-90c3-dcf86b67715b
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 97%

---

# isCoopSafe{#iscoopsafe}

Une configuration booléenne facultative permet de déterminer si le service d’ID envoie (ou n’envoie pas) des données à Adobe Experience Cloud Device Co-op.

Contenu :

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-4883eda6beb8437182bcc82bb58fae41" format="dita" scope="local"> Conditions </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-d18af2b903f248e18ae8108aaf0a8ebb" format="dita" scope="local"> Cas d’utilisation </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-952f56724a2b4d349340e26fbaf33ddd" format="dita" scope="local"> Syntaxe et exemple de code </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-fcd441933506493faefaa6b51f194a17" format="dita" scope="local"> Paramètres POST de l’appel d’événement </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-9281c39c8b6249d7864100b5cbca7dc6" format="dita" scope="local"> API post-instanciation </a> </li> 
</ul>

## Conditions requises {#section-4883eda6beb8437182bcc82bb58fae41}

Pour utiliser `isCoopSafe`, vous devez :

* Utiliser le code du service d’ID version 2.4 ou ultérieure.
* Participez à l’opération [Experience Cloud Device Co-op](https://experienceleague.adobe.com/docs/device-co-op/using/about/overview.html). Les membres potentiels de Co-op doivent également consulter cette documentation pour déterminer si `isCoopSafe` peut répondre à des préoccupations concernant la manière dont les données sont utilisées pour créer la coopérative Device Graph.

* Collaborer avec votre conseiller [!DNL Adobe] afin de définir un indicateur de liste blanche ou de liste noire pour votre compte Device Co-op. Il n’existe pas de chemin d’accès en libre-service pour activer ces drapeaux.

## Cas d’utilisation {#section-d18af2b903f248e18ae8108aaf0a8ebb}

`isCoopSafe` permet de résoudre 2 cas d’utilisation liés à la collecte de données par des membres actuels ou potentiels de Device Co-op. Ces cas d’utilisation concernent la manière dont les données des visiteurs du site sont transmises à Device Co-op pour permettre de créer la coopérative Device Graph. Le tableau suivant décrit comment `isCoopSafe` fonctionne avec ces cas d’utilisation pour bloquer ou envoyer des données à la coopérative Device Graph.

<table id="table_A24C63D2A21F47EDBAC8FA5E7BE888D8"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Exemple d’utilisation </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Visiteurs authentifiés</b> </p> </td> 
   <td colname="col2"> <p>Ajoutez <span class="codeph">isCoopSafe</span> au code de votre service d’ID afin de contrôler la manière dont les données relatives aux visiteurs authentifiés, qui ont ou n’ont pas accepté les conditions d’utilisation, sont utilisées par Device Co-op pour créer la coopérative Device Graph. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>DIL sur des sites tiers</b> </p> </td> 
   <td colname="col2"> <p>Ajoutez <span class="codeph">isCoopSafe</span> au code de votre service d’ID pour l’utiliser sur des sites tiers sur lesquels vous : </p> <p> 
     <ul id="ul_C27BB26510314834A2A7CD99D46DA4AC"> 
      <li id="li_4E6AE574F18646F09C0CF4553EEA1A9E">Impossible de vérifier si les visiteurs authentifiés ont ou n’ont pas accepté les conditions d’utilisation. </li> 
      <li id="li_26D0561BF32B4278B0A6B5082C17FED8">Vous devez contrôler comment ces données sont utilisées par Device Co-op pour créer le graphique de l’appareil. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Syntaxe et exemple de code {#section-952f56724a2b4d349340e26fbaf33ddd}

**Syntaxe :** `isCoopSafe: true | false`

Les options booléennes déterminent la manière dont les données des clients sont ou ne sont pas utilisées par Device Co-op.

* `isCoopSafe: true` : les données du visiteur collectées par un SDK mobile ou un site web *peuvent* être utilisées pour créer la coopérative Device Graph.

* `isCoopSafe: false` : les données du visiteur collectées par un SDK mobile ou un site web *ne peuvent pas* être utilisées pour créer la coopérative Device Graph.

**Exemple de code**

Définissez cette variable lorsque votre code de service d’ID instancie :

```js
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here",{ 
     ... 
     isCoopSafe: true 
});
```

## Paramètres POST de l’appel d’événement  {#section-fcd441933506493faefaa6b51f194a17}

En fonction de l’indicateur que vous définissez (`true` ou `false`), le service d’ID convertit `isCoopSafe` en les paramètres POST suivants et les envoie à [!DNL Adobe] dans un appel d’événement :

* `d_coop_safe=1`
* `d_coop_unsafe=1`

Les paramètres POST indiquent à [!DNL Experience Cloud] Device Co-op si cette application peut ou non inclure des données utilisateur dans la coopérative Device Graph. Le tableau ci-dessous définit la relation entre les indicateurs booléens `isCoopSafe` et les paramètres POST transmis dans un appel d’événement. Si vous n’utilisez pas `isCoopSafe`, aucun paramètre n’est transmis dans un appel d’événement.

<table id="table_0A544534CA904F4D9836A34B8C1EACBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> État de la configuration </th> 
   <th colname="col2" class="entry"> Paramètre POST </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe: true </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> d_coop_safe=1 </span> </p> <p>Device Co-op peut utiliser les données du visiteur pour créer la coopérative Device Graph. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe: false </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> d_coop_unsafe=1 </span> </p> <p>Device Co-op ne peut pas utiliser les données du visiteur pour créer la coopérative Device Graph. </p> </td> 
  </tr> 
 </tbody> 
</table>

## API post-instanciation   {#section-9281c39c8b6249d7864100b5cbca7dc6}

Ces API permettent de remplacer l’état `isCoopSafe`. Elles sont nécessaires car elles vous permettent de modifier l’état post-instanciation/post-connexion d’un visiteur sur un site ou dans une application monopage où la page n’est pas actualisée. Par exemple, vous devez appeler ces API si un utilisateur s’authentifie sur votre site ou application et accepte ultérieurement une stratégie de conditions d’utilisation qui permet à Device Co-op d’utiliser ses données.

<table id="table_BAA96B1F82BE48C3A61A1AF1367BA45C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> API </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> visitor.setAsCoopSafe(); </span> </p> </td> 
   <td colname="col2"> <p>Définit le paramètre POST <span class="codeph">d_coop_safe=1</span> dans tous les appels d’événement suivants. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> visitor.setAsCoopUnsafe(); </span> </p> </td> 
   <td colname="col2"> <p>Définit le paramètre POST <span class="codeph">d_coop_unsafe=1</span> dans tous les appels d’événement suivants. </p> </td> 
  </tr> 
 </tbody> 
</table>

<!--
Wiki page https://wiki.corp.adobe.com/x/RCfFTg
-->

>[!MORELIKETHIS]
>
>* [Code DIL isCoopSafe](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/class-level-dil-methods/dil-coopsafe.html)

