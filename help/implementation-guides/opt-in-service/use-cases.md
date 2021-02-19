---
description: Exemples de cas d’utilisation et de solutions pour gérer le service Opt-in.
seo-description: Exemples de cas d’utilisation et de solutions pour gérer le service Opt-in.
seo-title: Cas d’utilisation d’Opt-in
title: Cas d’utilisation d’Opt-in
uuid: d75a44d5-b713-43d1-b5b6-95d1d0d213a7
translation-type: tm+mt
source-git-commit: 0c300aa92991c0dec2ccdeeb34f9d886dcac7671
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 30%

---


# Cas d’utilisation d’Opt-in {#opt-in-use-cases}

Exemples de cas d’utilisation et de solutions pour gérer le service Opt-in.

## Conseils et dépannage {#section-5c566366410f4a8f89eca0d3f556d99f}

* Le fichier JavaScript Visiteur initialisé est synchrone et s’exécute lors du chargement de la page. Si vous interagissez avec un CMP ou si la persistance des autorisations présente une latence élevée, il peut être préférable d&#39;utiliser les fonctions asynchrones décrites dans [Configuration de l&#39;inclusion](../../implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047).
* L’inclusion est une implémentation par domaine. Il ne traitera pas les implémentations interdomaines.
* Pour désactiver les appels tiers pour une bibliothèque spécifique, vous devez configurer cette préférence dans chaque bibliothèque séparément.

## Scénarios d’Opt-in  {#section-1178053c065c430bba26f82ef383a71c}

Ces cas d’utilisation sont des exemples d’utilisation du service Opt-in.

<table id="table_83C85343611344D8A8315157C1B4240F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Exigence </th> 
   <th colname="col2" class="entry"> Solutions </th> 
   <th colname="col3" class="entry"> Impact </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Analytics peut collecter des données dans l’état de préconsentement, mais toutes les autres bibliothèques ne peuvent pas être chargées tant que le consentement n’a pas été reçu. </p> </td> 
   <td colname="col2"> <p>Utilisation de l’inclusion pour activer la catégorie Analytics dans l’état de préconsentement </p> </td> 
   <td colname="col3"> <p>Analytics utilise l’identifiant Analytics plutôt qu’ECID pour collecter le consentement préalable. Une fois l'ECID approuvé, un nouvel identifiant est utilisé et le visiteur reçoit un ECID qui peut être utilisé pour l'activation et les intégrations. </p> <p>On s'attend à ce que le visiteur se fragmente dans l'état avant/après le consentement. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Il est possible de collecter les mesures propriétaires dans un état de consentement préalable. Tous les autres types d’utilisation des données empêchés jusqu’à ce que le consentement soit reçu. </p> </td> 
   <td colname="col2"> <p>Utilisez l’inclusion pour activer les bibliothèques Analytics + ECID dans l’état de préconsentement. </p> <p>Ajouter la configuration "disablethirdpartycookies" dans la bibliothèque ECID afin de bloquer les synchronisations de cookies tiers + identifiants dans l’état de pré-consentement </p> </td> 
   <td colname="col3"> <p>L'appel Demdex d'Adobe déclenche la récupération de l'ECID, mais aucun cookie Demdex, autre cookie tiers ou synchronisation d'identifiants ne sera présent. </p> <p>Garde les visiteurs cohérents dans un état de consentement préalable /postérieur pour Analytics. La collecte dans l'état de pré-consentement sera liée à la collecte de données post-consentement. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Les mesures tierces et le ciblage sont acceptés dans un état de consentement préalable. Tous les autres types d’utilisation des données empêchés jusqu’à ce que le consentement soit reçu. </p> </td> 
   <td colname="col2"> <p>Utilisez l’inclusion pour activer les bibliothèques Analytics + ECID + Cible dans l’état de préconsentement. </p> <p>Ajoutez la configuration <span class="codeph">disablethirdpartycookies</span> à la bibliothèque ECID afin de bloquer les cookies tiers et la synchronisation d’ID dans un état de consentement préalable. Supprimez l’indicateur à l’état post-consentement. </p> </td> 
   <td colname="col3"> <p>L'appel Demdex d'Adobe déclenche la récupération de l'ECID, mais aucun cookie Demdex, autre cookie tiers ou synchronisation d'identifiants ne sera présent. </p> <p>Garde les visiteurs cohérents dans un état de consentement préalable /postérieur pour les solutions tiers. La collecte dans l'état de pré-consentement sera liée à la collecte de données post-consentement. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Aucun cookie n'est autorisé à être défini dans un état de préconsentement. </p> </td> 
   <td colname="col2"> <p>Utilisez l’inclusion pour bloquer le chargement de toutes les bibliothèques jusqu’à ce que le consentement soit reçu. </p> </td> 
   <td colname="col3"> <p>La mise en oeuvre est effectuée comme prévu et toutes les bibliothèques, y compris l’ECID, se chargeront dans l’ordre approprié dans l’état post-consentement. </p> <p>Perte de données pour les clients qui ne donnent jamais leur consentement à être suivis. </p> </td> 
  </tr> 
 </tbody> 
</table>

