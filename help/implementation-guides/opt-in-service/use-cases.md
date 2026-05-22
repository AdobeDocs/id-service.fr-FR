---
description: Exemples de cas d’utilisation et de solutions pour gérer le service Opt-in.
title: Cas d’utilisation d’Opt-in
exl-id: 4c57685f-40b7-4af4-8527-3c2795586f0f
TQID: https://experienceleague.adobe.com/ssSKMn1pEhduempV4zjCqi4Pol1U0oEBU6l36SkUTH4
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 460
ht-degree: 91%

---

# Cas d’utilisation d’Opt-in {#opt-in-use-cases}

Exemples de cas d’utilisation et de solutions pour gérer le service Opt-in.

## Conseils et dépannage {#section-5c566366410f4a8f89eca0d3f556d99f}

* Le fichier JavaScript Visiteur initialisé est synchrone et s’exécute lors du chargement de la page. Si vous interagissez avec une plateforme de gestion du consentement ou si la persistance des autorisations présente une latence élevée, il peut être préférable d’utiliser les fonctions asynchrones décrites dans [Configuration de l’Opt-in](../../implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047).
* L’Opt-in correspond à une implémentation par domaine. Cela ne permet pas de gérer les implémentations sur plusieurs domaines.
* Afin de désactiver les appels tiers pour une bibliothèque spécifique, vous devez configurer cette préférence dans chaque bibliothèque de manière distincte.

## Scénarios d’Opt-in {#section-1178053c065c430bba26f82ef383a71c}

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
   <td colname="col1"> <p>Analytics peut être collecté en statut de consentement préalable, mais toutes les autres bibliothèques ne peuvent pas être chargées tant que le consentement n’a pas été reçu </p> </td> 
   <td colname="col2"> <p>Utilisez l’Opt-in pour activer la catégorie Analytics à l’état de consentement préalable. </p> </td> 
   <td colname="col3"> <p>Analytics utilise l’identifiant Analytics plutôt qu’ECID pour collecter le consentement préalable. Une fois l’ECID approuvé, un nouvel identifiant est utilisé et le visiteur reçoit un ECID qui peut être utilisé pour l’activation et les intégrations. </p> <p>La fragmentation du visiteur à l’état de consentement préalable ou postérieur est attendue. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Il est possible de collecter les mesures propriétaires dans un état de consentement préalable. Tous les autres types d’utilisation des données sont empêchés jusqu’à réception du consentement. </p> </td> 
   <td colname="col2"> <p>Utilisez l’Opt-in pour activer les bibliothèques Analytics et ECID à l’état de consentement préalable. </p> <p>Ajoutez la configuration « disablethirdpartycookies » à la bibliothèque ECID pour bloquer les synchronisations des cookies + identifiants tiers à l’état de pré-consentement </p> </td> 
   <td colname="col3"> <p>L’appel Demdex d’Adobe déclenche la récupération de l’ECID, mais aucun cookie Demdex, autre cookie tiers ou synchronisation d’ID n’est présent. </p> <p>Garde les visiteurs cohérents dans un état de consentement préalable /postérieur pour Analytics. La collecte à l’état de consentement préalable sera liée à la collecte de données à l’état de consentement postérieur. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Les mesures tierces et le ciblage sont acceptés dans un état de consentement préalable. Tous les autres types d’utilisation des données sont empêchés jusqu’à réception du consentement. </p> </td> 
   <td colname="col2"> <p>Utilisez l’Opt-in pour activer les bibliothèques Analytics, ECID et Target à l’état de consentement préalable. </p> <p>Ajoutez la configuration <span class="codeph">disablethirdpartycookies</span> à la bibliothèque ECID afin de bloquer les cookies tiers et la synchronisation d’ID dans un état de consentement préalable. Supprimez l’indicateur à l’état de consentement postérieur. </p> </td> 
   <td colname="col3"> <p>L’appel Demdex d’Adobe déclenche la récupération de l’ECID, mais aucun cookie Demdex, autre cookie tiers ou synchronisation d’ID n’est présent. </p> <p>Garde les visiteurs cohérents dans un état de consentement préalable /postérieur pour les solutions tiers. La collecte à l’état de consentement préalable sera liée à la collecte de données à l’état de consentement postérieur. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Aucun cookie n’est autorisé à être défini à l’état de consentement préalable. </p> </td> 
   <td colname="col2"> <p>Utilisez l’Opt-in pour bloquer le chargement de toutes les bibliothèques jusqu’à réception du consentement. </p> </td> 
   <td colname="col3"> <p>L’implémentation est effectuée comme prévu et toutes les bibliothèques, y compris l’ECID, se chargent dans l’ordre approprié lorsque l’état de consentement postérieur est appliqué. </p> <p>Perte de données pour les clients qui ne consentent jamais à être suivis. </p> </td> 
  </tr> 
 </tbody> 
</table>

