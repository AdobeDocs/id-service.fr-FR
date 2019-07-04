---
description: Exemples de cas d’utilisation et de solutions pour gérer le service Opt-in.
seo-description: Exemples de cas d’utilisation et de solutions pour gérer le service Opt-in.
seo-title: Cas d’utilisation d’Opt-in
title: Cas d’utilisation d’Opt-in
uuid: d75a44d5-b713-43d1-b5b6-95d1d0d213a7
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Cas d’utilisation d’Opt-in {#opt-in-use-cases}

Exemples de cas d’utilisation et de solutions pour gérer le service Opt-in.

## Conseils et dépannage {#section-5c566366410f4a8f89eca0d3f556d99f}

* Le fichier JavaScript Visiteur initialisé est synchrone et s’exécute lors du chargement de la page. Si vous faites face à la latence élevée d’une persistance de la CMP ou des autorisations, il peut être préférable d’utiliser les fonctions asynchrones décrites dans [Configuration d’Opt-in](../../mcvid-implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047).
* Opt-in est une mise en œuvre par domaine. Les mises en œuvre interdomaines ne sont pas gérées.
* Afin de désactiver les appels de tiers pour une bibliothèque spécifique, vous devez configurer cette préférence séparément dans chacune des bibliothèques.

## Scénarios d’Opt-in {#section-1178053c065c430bba26f82ef383a71c}

Ces cas d’utilisation sont des exemples d’utilisation du service Opt-in.

<table id="table_83C85343611344D8A8315157C1B4240F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Condition </th> 
   <th colname="col2" class="entry"> Solutions </th> 
   <th colname="col3" class="entry"> Impact </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Il est possible de collecter Analytics dans un état de consentement préalable, mais le reste des bibliothèques ne peut pas être chargé avant d’avoir le consentement. </p> </td> 
   <td colname="col2"> <p>Utilisez Opt-in pour autoriser la catégorie Analytics dans un état de consentement préalable. </p> </td> 
   <td colname="col3"> <p>Analytics utilise l’identifiant Analytics plutôt qu’ECID pour collecter le consentement préalable. Une fois ECID approuvé, un nouvel identifiant est utilisé et le visiteur reçoit un identifiant Experience Cloud pouvant être utilisé pour l’activation et les mises en œuvre. </p> <p>La fragmentation des visiteurs dans un état de consentement préalable /postérieur est à prévoir. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Il est possible de collecter les mesures propriétaires dans un état de consentement préalable. Tout autre type d’utilisation des données est bloqué jusqu’à réception du consentement. </p> </td> 
   <td colname="col2"> <p>Utilisez Opt-in pour autoriser les bibliothèques Analytics et ECID dans un état de consentement préalable. </p> <p>Ajoutez la configuration disablethirdpartycookies à la bibliothèque ECID afin de bloquer les cookies tiers et la synchronisation d’ID dans un état de consentement préalable. </p> </td> 
   <td colname="col3"> <p>L’appel d’Adobe Demdex se déclenche pour l’extraction d’ECID mais aucun cookie Demdex, cookie tiers ou synchronisations d’ID ne se présente. </p> <p>Garde les visiteurs cohérents dans un état de consentement préalable /postérieur pour Analytics. La collecte dans un état de consentement préalable est liée à la collecte des données postérieure au consentement. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Les mesures tierces et le ciblage sont acceptés dans un état de consentement préalable. Tout autre type d’utilisation des données est bloqué jusqu’à réception du consentement. </p> </td> 
   <td colname="col2"> <p>Utilisez Opt-in pour autoriser les bibliothèques Analytics, ECID et Target dans un état de consentement préalable. </p> <p>Ajoutez la configuration <span class="codeph">disablethirdpartycookies</span> à la bibliothèque ECID afin de bloquer les cookies tiers et la synchronisation d’ID dans un état de consentement préalable. Supprimez le drapeau dans un état de consentement préalable. </p> </td> 
   <td colname="col3"> <p>L’appel d’Adobe Demdex se déclenche pour l’extraction d’ECID mais aucun cookie Demdex, cookie tiers ou synchronisations d’ID ne se présente. </p> <p>Garde les visiteurs cohérents dans un état de consentement préalable /postérieur pour les solutions tiers. La collecte dans un état de consentement préalable est liée à la collecte des données postérieure au consentement. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Aucun cookie ne peut être défini dans un état de consentement préalable </p> </td> 
   <td colname="col2"> <p>Utilisez Opt-in afin d’empêcher l’ensemble des bibliothèques de charger, jusqu’à réception du consentement. </p> </td> 
   <td colname="col3"> <p>La mise en œuvre se passe comme prévu et toutes les bibliothèques, la bibliothèque ECID incluse, chargent des séquences correctes dans un état de consentement postérieur. </p> <p>Les clients n’ayant jamais donné leur consentement à être suivis, ils subissent une perte de données. </p> </td> 
  </tr> 
 </tbody> 
</table>

