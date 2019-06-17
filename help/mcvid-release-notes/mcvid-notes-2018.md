---
description: Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service Experience Cloud ID en 2018.
keywords: Service d’identification
seo-description: Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service Experience Cloud ID en 2018.
seo-title: Notes de mise à jour 2018
title: Notes de mise à jour 2018
uuid: 771 b 5 b 11-a 8 e 3-464 c-b 65 e-b 15135584 ACE
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Notes de mise à jour 2018 {#release-notes}

Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service Experience Cloud ID en 2018.

## Version 3.3 {#section-3202c8d5457a45a5b5f4b4c838d44de3}

<table id="table_201417BD540E4EE69911AABE9BF77509"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Description des éléments </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Renforcement de la sécurité pour les cookies AMCV </p> </td> 
   <td colname="col2"> <p>Pendant une analyse de sécurité interne, il a été déterminé que lors de l’utilisation de la bibliothèque de DTM, les cookies utilisés pour la gestion des sessions échouent à définir les attributs appropriés. Cela peut entraîner le partage inopportun des informations des cookies. Afin de résoudre ce problème, nous avons introduit une configuration permettant au client de définir le cookie AMCV comme étant sécurisé. Voir <a href="https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-securecookie.html" format="https" scope="external">secureCookie</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Version 3.2 {#section-ae2fee1c152e405faa4eb395f960e2f6}

<table id="table_6546F5C74E4742E4B5E9793BCEAB66FA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Description des éléments </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Renforcement de la sécurité pour les cookies AMCV </p> </td> 
   <td colname="col2"> <p>Pendant une analyse de sécurité interne, il a été déterminé que lors de l’utilisation de la bibliothèque de DTM, les cookies utilisés pour la gestion des sessions échouent à définir les attributs appropriés. Cela peut entraîner le partage inopportun des informations des cookies. Afin de résoudre ce problème, nous avons introduit une configuration permettant au client de définir le cookie AMCV comme étant sécurisé. Voir secureCookie. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Les codes et ID d’intégration doivent être des nombres ou des chaînes non vides </p> </td> 
   <td colname="col2"> <p>Correction d’un problème survenant lors de la validation de setCustomerIDs lorsque les données contiennent un code ou ID d’intégration qui n’est pas un nombre ni une chaîne non vide. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Le JavaScript d’Experience Cloud ID est disponible dans le référentiel Git public </td> 
   <td colname="col2"> Le JavaScript d’Experience Cloud ID est disponible pour l’ensemble des clients d’Experience Cloud dans le référentiel Git public à l’adresse : https://github.com/Adobe-Marketing-Cloud/id-service/releases. </td> 
  </tr> 
 </tbody> 
</table>

## Version 3.1.2 {#section-3cba186f74fe4f2186a9ca2e5e0a2514}

<table id="table_9FA4E20C996746A2A4219C9A0F759AD1"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Description des éléments </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Pic irréaliste au niveau du nombre de visiteurs uniques </p> </td> 
   <td colname="col2"> <p>Avec le lancement du service Experience Cloud ID 3.1.0, nous avons détecté une erreur qui créait un pic irréaliste du nombre de visiteurs uniques lorsque cette version était mise en œuvre. Ce comportement se produit uniquement avec la dernière version d’ECID (v3.1.0) et si un utilisateur a sélectionné l’option « Autoriser à partir du site web actif uniquement » dans les paramètres de confidentialité du navigateur Safari. La version 3.1.2 corrige ce problème. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Version 3.1.0 {#section-a20c8278bf9643018965330415091e53}

>[!NOTE]
>
>Il est recommandé de mettre à niveau la version 3.1.0 vers la dernière version au moment opportun. Voir la description de la version 3.1.2. Le dernier bundle est disponible dans l’Adobe Launch, la Dynamic Tag Management et AppMeasurement.

<table id="table_512039AFC4D34038B8F116B71EEEE7F6"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Description des éléments </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Cookie défini sur le mauvais domaine </p> </td> 
   <td colname="col2"> <p>Nous avons résolu un bogue où un cookie visiteur temporaire définissait un cookie dans le domaine du cookie par défaut plutôt que de le définir dans le domaine fourni dans la configuration (initConfig). </p> </td> 
  </tr> 
 </tbody> 
</table>

## Version 3.0 {#section-5fcaef66e8b343238abeb10048dc5747}

<table id="table_7E9224D6CC924A2DB5119171C9DC5443"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Description des éléments </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Suspension des threads pour les demandes multiples de synchronisation des ID </p> </td> 
   <td colname="col2"> <p><b>Iframe</b> </p> <p>En raison des calculs incessants de l’UC survenant lors de synchronisations d’ID multiples, il arrive que l’IU se bloque. La suspension des threads a été introduite afin de regrouper les demandes de synchronisation des ID par groupes de 100 ms. </p> <p>Il en résultera de meilleures performances pour les utilisateurs utilisant Visitor 2.3.0+ et DIL 6.10+. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ajout de la capacité à désactiver les appels tiers </td> 
   <td colname="col2"> <p><b>JavaScript – 3.0.0</b> </p> <p>Adobe a renommé les configurations suivantes afin qu’il soit possible de désactiver les appels de synchronisation tiers. </p> <p>idSyncDisableSyncs a été renommé disableIdSyncs </p> <p>idSyncDisable3rdPartySyncing a été renommé disableThirdPartyCookies </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Prise en charge d’Internet Explorer </p> </td> 
   <td colname="col2"> <p>Le service d’identification ne prend plus en charge Internet Explorer 6, 7, 8 et 9. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Mise à jour de la documentation getInstance </p> </td> 
   <td colname="col2"> <p>Ajout d’un avertissement à la fonction Visitor rappelant de ne pas instancier cette fonction avec var visitor = new Visitor. </p> </td> 
  </tr> 
 </tbody> 
</table>

