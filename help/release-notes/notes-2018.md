---
description: Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service d’identités d’Experience Cloud en 2018.
keywords: Service d’ID
title: Notes de mise à jour 2018
exl-id: ad3cccf1-2753-4ac9-a68c-15b2d62bbc1a
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 100%

---

# Notes de mise à jour 2018 {#release-notes}

Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service d’identités d’Experience Cloud en 2018.

## Version 3.3 {#section-3202c8d5457a45a5b5f4b4c838d44de3}

<table id="table_201417BD540E4EE69911AABE9BF77509"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Description de l’élément </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Sécurité accrue des cookies AMCV </p> </td> 
   <td colname="col2"> <p>Pendant une analyse de sécurité interne, il a été déterminé que lors de l’utilisation de la bibliothèque de DTM, les cookies utilisés pour la gestion des sessions échouent à définir les attributs appropriés. Cela peut entraîner le partage inopportun des informations des cookies. Afin de résoudre ce problème, nous avons introduit une configuration permettant au client de définir le cookie AMCV comme étant sécurisé. Voir <a href="/help/library/function-vars/securecookie.md" format="https" scope="external">secureCookie</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Version 3.2 {#section-ae2fee1c152e405faa4eb395f960e2f6}

<table id="table_6546F5C74E4742E4B5E9793BCEAB66FA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Description de l’élément </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Sécurité accrue des cookies AMCV </p> </td> 
   <td colname="col2"> <p>Pendant une analyse de sécurité interne, il a été déterminé que lors de l’utilisation de la bibliothèque de DTM, les cookies utilisés pour la gestion des sessions échouent à définir les attributs appropriés. Cela peut entraîner le partage inopportun des informations des cookies. Afin de résoudre ce problème, nous avons introduit une configuration permettant au client de définir le cookie AMCV comme étant sécurisé. Voir secureCookie. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>L’ID et le code d’intégration doivent être des nombres ou des chaînes non vides. </p> </td> 
   <td colname="col2"> <p>Correction d’un problème survenant lors de la validation de « setCustomerIDs » lorsque les données contiennent un « id » ou « code » d’intégration qui n’est ni un nombre ni une chaîne non vide. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Les fichiers JavaScript ECID sont disponibles dans un référentiel Git public. </td> 
   <td colname="col2"> Les fichiers JavaScript ECID sont désormais disponibles dans un référentiel Git public accessible à tous les clients Experience Cloud à l’adresse https://github.com/Adobe-Marketing-Cloud/id-service/releases. </td> 
  </tr> 
 </tbody> 
</table>

## Version 3.1.2 {#section-3cba186f74fe4f2186a9ca2e5e0a2514}

<table id="table_9FA4E20C996746A2A4219C9A0F759AD1"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Description de l’élément </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Pic irréaliste au niveau du nombre de visiteurs uniques </p> </td> 
   <td colname="col2"> <p>Avec le lancement du service d’identités d’Experience Cloud 3.1.0, nous avons détecté une erreur qui créait un pic irréaliste du nombre de visiteurs uniques lorsque cette version était mise en œuvre. Ce comportement apparaît uniquement avec la dernière version d’ECID, la version 3.1.0, et si un utilisateur a sélectionné l’option « Autoriser à partir du site web actuel uniquement » dans les paramètres de confidentialité d’un navigateur Safari. La version 3.1.2 corrige ce problème. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Version 3.1.0 {#section-a20c8278bf9643018965330415091e53}

>[!NOTE]
>
>Nous vous recommandons de procéder à la mise à niveau de la version 3.1.0 vers la dernière version dès que possible. Voir la description de la version 3.1.2. Le dernier bundle est disponible dans Adobe Experience Platform Launch, Dynamic Tag Management et AppMeasurement.

<table id="table_512039AFC4D34038B8F116B71EEEE7F6"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Description de l’élément </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Cookie défini sur un domaine incorrect </p> </td> 
   <td colname="col2"> <p>Nous avons corrigé un bug en raison duquel le cookie Visiteur temporaire définissait un cookie dans le domaine de cookie « par défaut » au lieu de le définir dans le domaine fourni dans la configuration (initConfig). </p> </td> 
  </tr> 
 </tbody> 
</table>

## Version 3.0 {#section-5fcaef66e8b343238abeb10048dc5747}

<table id="table_7E9224D6CC924A2DB5119171C9DC5443"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Description de l’élément </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Suspension des threads pour les demandes multiples de synchronisation des ID </p> </td> 
   <td colname="col2"> <p><b>Iframe</b> </p> <p>En raison des calculs incessants de l’UC survenant lors de synchronisations d’ID multiples, il arrive que l’IU se bloque. Nous introduisons la suspension des threads pour séparer les demandes de synchronisation d’ID de 100 millisecondes chacune. </p> <p>Cette modification améliore les performances des clients utilisant Visitor 2.3.0+ et DIL 6.10+. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Ajout de la capacité à désactiver les appels tiers </td> 
   <td colname="col2"> <p><b>JavaScript – 3.0.0</b> </p> <p>Adobe a renommé les configurations suivantes afin qu’il soit possible de désactiver les appels de synchronisation tiers. </p> <p>idSyncDisableSyncs a été renommé disableIdSyncs </p> <p>idSyncDisable3rdPartySyncing a été renommé disableThirdPartyCookies </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Prise en charge d’Internet Explorer </p> </td> 
   <td colname="col2"> <p>Le service d’ID ne prend plus en charge Internet Explorer 6, 7, 8 et 9. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Mise à jour de la documentation getInstance </p> </td> 
   <td colname="col2"> <p>Ajout d’un avertissement à la fonction Visitor rappelant de ne pas instancier cette fonction avec var visitor = new Visitor. </p> </td> 
  </tr> 
 </tbody> 
</table>
