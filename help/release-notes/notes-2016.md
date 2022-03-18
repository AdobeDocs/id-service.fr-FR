---
description: Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service Experience Cloud Identity en 2016.
keywords: Service d’ID
title: Notes de mise à jour 2016
exl-id: f96b9869-6282-4090-b392-797608e25a51
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: ht
source-wordcount: '1146'
ht-degree: 100%

---

# Notes de mise à jour 2016 {#release-notes}

Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service Experience Cloud Identity en 2016.

Ces modifications sont également consignées dans les [notes de mise à jour d’Experience Cloud](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=fr).

## Version 1.10 {#section-7d719b3213344a46858835042e0214ed}

Novembre 2016

>[!IMPORTANT]
>
>* La version 1.10 requiert [!UICONTROL AppMeasurement] version 1.8.0.
>* Si vous utilisez la bibliothèque version 2.0.0 ou ultérieure du service Experience Cloud Identity, la synchronisation des identifiants commencera par défaut pour Adobe Media Optimizer. Voir [Comprendre la synchronisation des identifiants et les taux de correspondance](/help/introduction/match-rates.md).


**Correctifs et améliorations**

* Instructions supplémentaires sur la manière de mettre en œuvre le service d’ID dans un environnement côté serveur.
* Ajout de la fonction booléenne `Visitor.overwriteCrossDomainMCIDAndAID` qui permet de remplacer les Experience Cloud ID et Analytics ID sur d’autres domaines dont vous êtes propriétaire. Voir [Remplacement d’un identifiant visiteur](../library/function-vars/overwrite-visitor-id.md#reference-9db13d637ce44fb6a8d519de5743ccde).

* Ajout d’un `TS = UTC`horodatage en tant que propriété de la fonction `visitor.appendVisitorIDsTo`. Le service d’ID utilise l’horodatage pour déterminer si les identifiants doivent être utilisés dans l’URL de redirection selon un intervalle d’âge de 5 minutes. Voir [Fonction d’ajout d’identifiant visiteur](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce).

* Ajout de la nouvelle fonction `Visitor.getLocationHint,` qui renvoie un identifiant de région. Voir [Obtention des identifiants de région (indicateur de location)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).

* Ajout de deux fonctions, `idSyncByURL` et `idSyncByDataSource`, qui permettent d’implémenter manuellement une synchronisation des identifiants dans l’iFrame de publication de destination. Voir [Synchronisation des ID par URL ou source de données](../library/get-set/idsync.md#reference-b01b88c083434cf8abbeabd3c6956c48).

* Résolution d’un bogue qui bloquait l’appel du suivi AppMeasurement si `disableThirdPartyCalls:true`.
* Résolution d’un bogue qui empêchait le service d’ID de transmettre l’Experience Cloud ID (MID) à différents domaines.

## Version 1.9.0 {#section-04e1b4d4b10d40468f2116b8119998e7}

Octobre 2016

**Correctifs et améliorations**

* Correction d’un bug qui transmettait des ID d’utilisateur Audience Manager uniques (AAMUUID) en tant qu’Experience Cloud ID au service ID.
* Si la durée de vue d’un cookie AMCV expire, le service d’ID renvoie tout de même cette information au serveur, tant que le cookie contient un Experience Cloud ID. Après cet appel, le service d’ID effectue un appel asynchrone pour mettre à jour le cookie. Cela contribue à améliorer les performances, car le service d’ID n’a pas besoin d’attendre une réponse du serveur. Il peut utiliser les valeurs d’un cookie AMCV existant, puis demander une mise à jour.
* Le service d’ID synchronise automatiquement les Experience Cloud ID (MID) avec Adobe Media Optimizer et d’autres domaines Adobe internes directement sur la page. La synchronisation automatique est activée pour tous les comptes nouveaux et existants. Cela permet d’améliorer les taux de correspondance pour Media Optimizer. Cela s’applique à VisitorAPI.js 1.8 ou version ultérieure. Voir la documentation [Comprendre la synchronisation des identifiants et les taux de correspondance](../introduction/match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab).

**Documentation nouvelle et révisée**

**Nouveau :** [Obtention des identifiants de région et d’utilisateur à partir du cookie AMCV](../reference/regions.md#concept-15b2c8c894b846a48f1f61a353cfdf4e)

## Version 1.8.0 {#section-69f2eb5b246b4c7aafe116b7a2a5448a}

Septembre 2016

**Correctifs et améliorations**

Ajout de `disableThirdPartyCalls` comme indicateur booléen optionnel que vous pouvez définir dans la fonction `Visitor.getInstance`. Lorsque `disableThirdPartyCalls= true`, le service d’ID ne lancera pas d’appel vers d’autres domaines. Par défaut, `disableThirdPartyCalls= false`. Voir [disableThirdPartyCalls](../library/function-vars/disablethirdpartycalls.md#reference-fba90b095e9746daad46e3abb790d18b).

## Version 1.7.0 {#section-f7d59104de6644fca3691480383d4644}

Août 2016

**Correctifs et améliorations**

* Ajout de `idSyncAttachIframeOnWindowLoad` comme indicateur booléen optionnel que vous pouvez définir dans la fonction `Visitor.getInstance`. Si `idSyncAttachIframeOnWindowLoad= true`, le service d’ID charge l’iFrame de synchronisation des identifiants au chargement de la fenêtre. Par défaut, le service d’ID charge l’iFrame aussi vite que possible. Cet indicateur *remplace* `idSyncAttachIframeASAP`, qui est obsolète. Voir [Variables de fonction Visitor.getInstance](../library/function-vars/function-vars.md).

* Ajout d’une fonctionnalité permettant la prise en charge du suivi des [!DNL Experience Cloud] ID à l’échelle de tous les domaines, applications natives et applications hybrides jusqu’aux transitions web. Voir [Fonction auxiliaire d’ajout d’identifiant visiteur](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce).

* Ajout de fonctions au code visitorAPI.js qui déterminent si le service d’ID a généré l’[!DNL Experience Cloud] ID du visiteur côté client ou côté serveur ou si les appels d’identifiants sont expirés. Voir les sections relatives aux [fonctions de suivi de dépassement de délai](../library/get-set/timeout-functions.md#reference-912bae0f116540df8c5dc1c008656c23) et au [suivi de la génération d’identifiants de visiteurs côté client](../library/get-set/client-side-id.md#reference-8244dc6d832c4bbaaa97528096bcc2a6).

**Documentation nouvelle et révisée**

Révision : [Conditions requises du service Experience Cloud Identity](../reference/requirements.md)

**Problèmes connus**

Les clients qui utilisent le code DIL [!DNL Audience Manager] et le code visitorAPI.js sur la même page doivent définir la variable DIL `secureDataCollection= false`. Voir [secureDataCollection](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-overview.html?lang=fr).

## Version 1.6.0 {#section-3faaa14bf3934c6a99b8f79ee06fc0d2}

Juillet 2016

>[!IMPORTANT]
>
>La version 1.6.0 du service [!DNL Experience Cloud] ID *nécessite* AppMeasurement pour JavaScript version 1.6.2. Si vous passez à la version 1.6.0 du service d’ID, assurez-vous d’utiliser la bonne version du code AppMeasurement.

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
   <td colname="col2"> <p>Grâce au partage des ressources cross-origin (CORS), les navigateurs peuvent demander des ressources auprès d’un domaine autre que le domaine actuel. Le service Experience Cloud Identity prend en charge les normes CORS afin de permettre les requêtes de ressources cross-origin côté client. Dans les navigateurs non compatibles avec la norme CORS, les demandes JSONP sont restaurées par le service ID. </p> <p>Voir : </p> 
    <ul id="ul_15386385108F4E07824041DD6F2DC11E"> 
     <li id="li_DB8D5AA4A7004DE4AE9CBC31A389F5BD"> <a href="../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758" format="dita" scope="local"> Prise en charge de la norme CORS dans le service Experience Cloud Identity </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**Correctifs et améliorations**

* Ajout d’un paramètre `d_fieldgroup` aux appels de synchronisation des identifiants vers `dpm.demdex.net`. Ce nouveau paramètre est utilisé à des fins de dépannage et de débogage internes.

* Ajout d’un attribut de titre à l’iFrame du service d’ID. Avec un titre d’iFrame, les lecteurs d’écran peuvent plus facilement fournir des informations sur la page aux utilisateurs qui ont besoin d’aide lors de leur interaction avec du contenu en ligne. L’attribut du titre d’iFrame est défini sur `Adobe ID Syncing iFrame`.
* Ajout de `idSyncAttachIframeASAP: true` comme indicateur en option que vous pouvez définir dans la fonction `Visitor.getInstance`. S’il est défini sur `true`, le service d’ID charge l’iFrame de synchronisation des identifiants aussi vite que possible. Cette modification vise à améliorer les taux de correspondance de la synchronisation des identifiants. Par défaut, le service d’ID charge l’iFrame au chargement de la fenêtre. Voir [Variables de fonction Visitor.getInstance](../library/function-vars/function-vars.md).

* Correction d’un bogue d’une fonction de rappel en raison duquel AppMeasurement était bloqué dans une boucle infinie.
* Valeur par défaut de l’intervalle `loadTimeout` modifiée et définie sur 30 000 millisecondes au lieu de 500 millisecondes. Voir [Variables de fonction Visitor.getInstance](../library/function-vars/function-vars.md).

**Documentation nouvelle et révisée**

**Nouveau**

* [Mise en œuvre du service Experience Cloud Identity pour Analytics](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd)
* [Mise en œuvre du service Experience Cloud Identity pour Analytics, Audience Manager et Target](../implementation-guides/setup-aam-analytics-target.md#concept-e7e2dc0d0bbe481db93328b5604b4673)

**Révision**

* [Conditions requises pour le service Experience Cloud Identity](../reference/requirements.md)
* [Test et vérification du service Experience Cloud Identity](../implementation-guides/test-verify.md)

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
   <td colname="col2"> <p>L’attribut iFrame est désormais défini de sorte que <span class="codeph">iframe.sandbox=’allow-scripts allow-same-origin’;</span>. </p> <p>Le fait d’autoriser seulement ces 2 jetons permet de renforcer la sécurité et d’offrir au service d’ID les fonctionnalités de base requises pour la synchronisation des ID. </p> <p>L’attribut sandbox n’est pas pris en charge dans Internet Explorer version 9 ou antérieure. Pour en savoir plus, voir la section sur les attributs de cette <a href="https://developer.mozilla.org/fr-FR/docs/Web/HTML/Element/iframe" format="https" scope="external">documentation sur les iFrames</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Codage de l’Experience Cloud ID (MID) </p> </td> 
   <td colname="col2"> <p>Le service d’ID code la valeur MID qui est renvoyée du serveur ou lorsqu’elle est définie par la fonction <span class="codeph">visitor.setMarketingCloudVisitorID()</span>. Pour plus d’informations sur le MID, voir <a href="../introduction/cookies.md" format="dita" scope="local"> Cookies et service Experience Cloud ID</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Correctifs**

L’API visiteur n’impose plus un autre appel de resynchronisation avec Audience Manager lorsqu’il n’existe pas d’identifiant visiteur Analytics hérité.

## Version 1.5.x {#section-a62ae48275324058b57edf66ee5a579f}

Mai 2016

**Mises à jour de la documentation**

* [Versions minimales des SDK pour Android et iOS](../reference/requirements.md#section-73b2446fba8e463888642c7d7dfd94f1)
* [Data Workbench et service Experience Cloud Identity](../reference/dwb.md#task-72df50a051944a47b01b0c0bc3d1e1d8)
* [Test et vérification du service Experience Cloud Identity](../implementation-guides/test-verify.md)

## Version 1.5.x {#section-0cfeef085cff4cbc8dff6cbc6fc32920}

Avril 2016

**Mises à jour de la documentation**

[Mise en œuvre du service Experience Cloud Identity pour Target](../implementation-guides/setup-target.md#concept-9b5a802132574e1181927ddd00e5c5af)

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
   <td colname="col2"> <p>Le service <span class="keyword">Experience Cloud</span> ID prend en charge les requêtes de droit d’opposition des visiteurs. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> Modification de l’intervalle de synchronisation d’ID </p> </td> 
   <td colname="col2"> <p>Le service <span class="keyword">Experience Cloud ID</span> effectue désormais des appels de synchronisation des identifiants à chaque appel aux serveurs de collecte de données. Le service d’ID n’effectuait auparavant qu’une seule requête lors du premier appel pour obtenir un <span class="keyword">Experience Cloud</span> ID. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Mises à jour de la documentation**

* [Mise en œuvre du service Experience Cloud Identity pour Analytics](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd) : nouvelle procédure qui décrit comment configurer le service d’ID avec [!DNL Analytics].

* [Points de prise de décision concernant la migration vers le service Experience Cloud Identity](../reference/analytics-reference/migration-decisions.md#concept-ba44803eea3c4cc185232a510cec0257) : révision du texte pour le clarifier. L’utilisation d’un seul domaine vous permet de migrer hors d’un CNAME de collecte de données si vous ne souhaitez plus le gérer. Toutefois, il n’est pas nécessaire de modifier votre CNAME si celui-ci fonctionne.

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
