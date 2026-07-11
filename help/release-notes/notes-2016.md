---
description: Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service d’identification des visiteurs en 2016.
keywords: Service d’identification des visiteurs
title: Notes de mise à jour 2016
feature-set: Experience Cloud Services
feature: TK421
exl-id: f96b9869-6282-4090-b392-797608e25a51
TQID: https://experienceleague.adobe.com/u91aLAt-ycKk1U1A1yhAVUAonGhV6fHWNRVTZB0QAXI
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: c1579802-ddd4-4214-8a91-97b2066abe11id: c2be0313-b3ae-45e0-b454-d20bf54b23f2id: d095671a-1355-40aa-8b5f-06c33c68080bid: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 1114
ht-degree: 47%

---

# Notes de mise à jour 2016 {#release-notes}

Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service d’identification des visiteurs en 2016.

Ces modifications sont également consignées dans les notes de mise à jour d’[CX Enterprise](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=fr).

## Version 1.10 {#section-7d719b3213344a46858835042e0214ed}

Novembre 2016

>[!IMPORTANT]
>
>* La version 1.10 requiert [!UICONTROL AppMeasurement] 1.8.0.
>* À l’aide de la bibliothèque du service d’identification des visiteurs version 2.0.0 ou ultérieure, la synchronisation des identifiants commencera par défaut pour Adobe Media Optimizer. Voir [Comprendre la synchronisation des identifiants et les taux de correspondance](/help/introduction/match-rates.md).

**Correctifs et améliorations**

* Ajout d’instructions sur la mise en œuvre du service d’identification des visiteurs dans un environnement côté serveur.
* Ajout de `Visitor.overwriteCrossDomainMCIDAndAID`, une fonction booléenne qui vous permet de remplacer les identifiants ECID et Analytics sur d’autres domaines que vous possédez. Voir [Remplacement d’un identifiant visiteur](../library/function-vars/overwrite-visitor-id.md#reference-9db13d637ce44fb6a8d519de5743ccde).

* Ajout d’un `TS = UTC`horodatage en tant que propriété de la fonction `visitor.appendVisitorIDsTo`. Le service d’identification des visiteurs utilise la date et l’heure pour déterminer s’il doit utiliser les identifiants dans l’URL de redirection selon un intervalle de vieillissement de 5 minutes. Voir [Fonction d’ajout d’identifiant visiteur](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce).

* Ajout de la nouvelle fonction `Visitor.getLocationHint,` qui renvoie un identifiant de région. Voir [Obtention des identifiants de région (indicateur de location)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).

* Ajout de deux fonctions, `idSyncByURL` et `idSyncByDataSource`, qui permettent d’implémenter manuellement une synchronisation des identifiants dans l’iFrame de publication de destination. Voir [Synchronisation des ID par URL ou source de données](../library/get-set/idsync.md#reference-b01b88c083434cf8abbeabd3c6956c48).

* Résolution d’un bogue qui bloquait l’appel du suivi AppMeasurement si `disableThirdPartyCalls:true`.
* Correction d’un bug en raison duquel le service d’identification des visiteurs ne pouvait pas transmettre l’ECID sur différents domaines.

## Version 1.9.0 {#section-04e1b4d4b10d40468f2116b8119998e7}

Octobre 2016

**Correctifs et améliorations**

* Correction d’un bug qui transmettait les ID d’utilisateur uniques Audience Manager (AAMUUID) en tant qu’ECID au service d’identification des visiteurs.
* Si la durée de vie (TTL) d’un cookie AMCV a expiré, le service d’identification des visiteurs renvoie toujours ces informations au serveur tant que le cookie contient un ECID. Après cet appel, le service d’identification des visiteurs effectue un appel asynchrone pour mettre à jour le cookie. Cela permet d’améliorer les performances, car le service d’identification des visiteurs n’a pas besoin d’attendre une réponse du serveur. Il peut utiliser les valeurs d’un cookie AMCV existant, puis demander une mise à jour.
* Le service d’identification des visiteurs synchronise automatiquement les ECID (MID) avec Adobe Media Optimizer et d’autres domaines Adobe internes directement sur la page. La synchronisation automatique est activée pour tous les comptes nouveaux et existants. Cela permet d’améliorer les taux de correspondance pour Media Optimizer. S’applique à `VisitorAPI.js` version 1.8 ou ultérieure. Voir la documentation [Comprendre la synchronisation des identifiants et les taux de correspondance](../introduction/match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab).

**Documentation nouvelle et révisée**

**Nouveau :** [Obtention des identifiants de région et d’utilisateur à partir du cookie AMCV](../reference/regions.md#concept-15b2c8c894b846a48f1f61a353cfdf4e)

## Version 1.8.0 {#section-69f2eb5b246b4c7aafe116b7a2a5448a}

Septembre 2016

**Correctifs et améliorations**

Ajout de `disableThirdPartyCalls` comme indicateur booléen optionnel que vous pouvez définir dans la fonction `Visitor.getInstance`. Lorsqu’il est `disableThirdPartyCalls= true`, le service d’identification des visiteurs n’effectuera pas d’appels vers d’autres domaines. Par défaut, `disableThirdPartyCalls= false`. Voir [disableThirdPartyCalls](../library/function-vars/disablethirdpartycalls.md#reference-fba90b095e9746daad46e3abb790d18b).

## Version 1.7.0 {#section-f7d59104de6644fca3691480383d4644}

Août 2016

**Correctifs et améliorations**

* Ajout de `idSyncAttachIframeOnWindowLoad` comme indicateur booléen optionnel que vous pouvez définir dans la fonction `Visitor.getInstance`. Lorsqu’il est `idSyncAttachIframeOnWindowLoad= true`, le service d’identification des visiteurs charge l’iFrame de synchronisation des identifiants au chargement de la fenêtre. Par défaut, le service d’identification des visiteurs charge l’iFrame aussi rapidement que possible. Cet indicateur *remplace* `idSyncAttachIframeASAP`, qui est obsolète. Voir [Variables de fonction Visitor.getInstance](../library/function-vars/function-vars.md).

* Ajout de fonctionnalités pour la prise en charge du suivi des ECID sur les domaines, les applications natives et les applications hybrides aux transitions web. Voir [Fonction auxiliaire d’ajout d’identifiant visiteur](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce).

* Ajout de fonctions à `VisitorAPI.js` code qui déterminent si le service d’identification des visiteurs a généré l’ECID des visiteurs côté client ou côté serveur ou si les appels d’ID ont expiré. Voir les sections relatives aux [fonctions de tracking de délai d’expiration](../library/get-set/timeout-functions.md#reference-912bae0f116540df8c5dc1c008656c23) et au [suivi de la génération d’identifiants de visiteurs côté client](../library/get-set/client-side-id.md#reference-8244dc6d832c4bbaaa97528096bcc2a6).

**Documentation nouvelle et révisée**

Révisé : [Conditions requises pour le service d’identification des visiteurs](../reference/requirements.md)

**Problèmes connus**

Les clients et clientes qui utilisent le code Audience Manager DIL et le code `VisitorAPI.js` sur la même page doivent définir la variable DIL `secureDataCollection= false`. Voir [secureDataCollection](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-overview.html?lang=fr).

## Version 1.6.0 {#section-3faaa14bf3934c6a99b8f79ee06fc0d2}

Juillet 2016

>[!IMPORTANT]
>
>La version 1.6.0 du service d’identification des visiteurs *nécessite* AppMeasurement pour JavaScript version 1.6.2. Si vous effectuez une mise à niveau vers le service d’identification des visiteurs version 1.6.0, veillez à utiliser la version de code AppMeasurement appropriée.

<table id="table_5472AAFA0DD2495DB8D92DEBE44A07A9"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Fonctionnalité </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Partage des ressources cross-origin (CORS) </p> </td> 
   <td colname="col2"> <p>Grâce au partage des ressources cross-origin (CORS), les navigateurs peuvent demander des ressources auprès d’un domaine autre que le domaine actuel. Le service d’identification des visiteurs prend en charge les normes CORS pour activer les demandes de ressources cross-origin côté client. Le service d’identification des visiteurs revient aux requêtes JSONP sur les navigateurs qui ne prennent pas en charge CORS. </p> <p>Voir : </p> 
    <ul id="ul_15386385108F4E07824041DD6F2DC11E"> 
     <li id="li_DB8D5AA4A7004DE4AE9CBC31A389F5BD"> Prise en charge de la norme CORS <a href="../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758" format="dita" scope="local"> dans l’</a> du service d’identification des visiteurs </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**Correctifs et améliorations**

* Ajout d’un paramètre `d_fieldgroup` aux appels de synchronisation des identifiants vers `dpm.demdex.net`. Ce nouveau paramètre est utilisé à des fins de dépannage et de débogage internes.

* Ajout d’un attribut de titre à l’iFrame du service d’identification des visiteurs. Avec un titre d’iFrame, les lecteurs d’écran peuvent plus facilement fournir des informations sur la page aux utilisateurs qui ont besoin d’aide lors de leur interaction avec du contenu en ligne. L’attribut du titre d’iFrame est défini sur `Adobe ID Syncing iFrame`.
* Ajout de `idSyncAttachIframeASAP: true` comme indicateur en option que vous pouvez définir dans la fonction `Visitor.getInstance`. Lorsqu’il est `true`, le service d’identification des visiteurs charge l’iFrame de synchronisation des identifiants aussi vite que possible. Cette modification vise à améliorer les taux de correspondance de la synchronisation des identifiants. Par défaut, le service d’identification des visiteurs charge l’iFrame au chargement de la fenêtre. Voir [Variables de fonction Visitor.getInstance](../library/function-vars/function-vars.md).

* Correction d’un bogue d’une fonction de rappel en raison duquel AppMeasurement était bloqué dans une boucle infinie.
* Valeur par défaut de l’intervalle `loadTimeout` modifiée et définie sur 30 000 millisecondes au lieu de 500 millisecondes. Voir [Variables de fonction Visitor.getInstance](../library/function-vars/function-vars.md).

**Documentation nouvelle et révisée**

**Nouveau**

* [Mise en œuvre du service d’identification des visiteurs pour Analytics, Audience Manager et Target](../implementation-guides/setup-aam-analytics-target.md#concept-e7e2dc0d0bbe481db93328b5604b4673)

**Révision**

* [ Conditions requises pour le service d’identification des visiteurs ](../reference/requirements.md)
* [Test et vérification du service d’identification des visiteurs](../implementation-guides/test-verify.md)

## Version 1.5.7 {#section-735b4989a5744a42aeb2d97602dbda62}

Juin 2016

<table id="table_5D604D0820C84EC996ACB99126C8A3DF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Fonctionnalité </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Modifications de l’attribut <span class="codeph">iframe.sandbox</span> </p> </td> 
   <td colname="col2"> <p>L’attribut iFrame est désormais défini de sorte que <span class="codeph">iframe.sandbox=’allow-scripts allow-same-origin’;</span>. </p> <p>L’autorisation de ces deux jetons uniquement contribue à améliorer la sécurité et fournit au service d’identification des visiteurs les fonctionnalités de base requises pour la synchronisation des identifiants. </p> <p>L’attribut sandbox n’est pas pris en charge dans Internet Explorer version 9 ou antérieure. Pour en savoir plus, voir la section sur les attributs de cette <a href="https://developer.mozilla.org/fr-FR/docs/Web/HTML/Element/iframe" format="https" scope="external">documentation sur les iFrames</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Encodage de l’ECID </p> </td> 
   <td colname="col2"> <p>Le service d’identification des visiteurs code la valeur MID renvoyée par le serveur ou lorsqu’elle est définie par la fonction de </span> visitor.setMarketingCloudVisitorID() <span class="codeph">. Pour plus d’informations sur le MID, voir Cookies <a href="../introduction/cookies.md" format="dita" scope="local"> et </a> ECID . </p> </td> 
  </tr> 
 </tbody> 
</table>

**Correctifs**

L’API visiteur n’impose plus un autre appel de resynchronisation avec Audience Manager lorsqu’il n’existe pas d’identifiant visiteur Analytics hérité.

## Version 1.5.x {#section-a62ae48275324058b57edf66ee5a579f}

Mai 2016

**Mises à jour de la documentation**

* [Versions minimales des SDK pour Android et iOS](../reference/requirements.md#section-73b2446fba8e463888642c7d7dfd94f1)
* [Test et vérification du service d’identification des visiteurs](../implementation-guides/test-verify.md)

## Version 1.5.x {#section-0cfeef085cff4cbc8dff6cbc6fc32920}

Avril 2016

**Mises à jour de la documentation**

[Mise en œuvre du service d’identification des visiteurs pour Target](../implementation-guides/setup-target.md#concept-9b5a802132574e1181927ddd00e5c5af)

## Version 1.5.4 {#section-1a44ba147fb3440ea7dec551faee3528}

Mars 2016

<table id="table_F4ED1F88709E4D3BA69C747879A4E18F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Fonctionnalité </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Prise en charge du droit d’opposition </p> </td> 
   <td colname="col2"> <p>Le service d’identification des visiteurs prend en charge les demandes de désinscription des visiteurs. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> Modification de l’intervalle de synchronisation d’ID </p> </td> 
   <td colname="col2"> <p>Le service d’identification des visiteurs effectue désormais des appels de synchronisation des identifiants à chaque appel aux serveurs de collecte de données. Auparavant, le service d’identification des visiteurs n’effectuait qu’une seule requête lors du premier appel pour obtenir un ECID. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Version 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

Janvier 2016

**Mises à jour de la documentation**

<table id="table_C1A5DBED6B104C0FBA54EC663D3B0E86"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Rubrique </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../reference/authenticated-state.md" format="dita" scope="local"> ID de client et états d’authentification </a> </p> </td> 
   <td colname="col2"> <p>Révision du texte. Les ID de client doivent être transmis uniquement en tant que valeurs non codées. Les identifiants de codage créent des identifiants codés par doublon. </p> </td> 
  </tr> 
 </tbody> 
</table>


