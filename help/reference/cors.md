---
description: Les navigateurs utilisent la norme CORS (Cross Origin Resource Sharing) pour demander des ressources auprès d’un domaine autre que le domaine actuel. Le service Experience Cloud Identity prend en charge les normes CORS qui permettent d’envoyer des requêtes de ressources cross-origin côté client. Dans les navigateurs plus anciens ou non compatibles avec la norme CORS, les demandes JSONP sont restaurées.
keywords: ID Service
seo-description: Les navigateurs utilisent la norme CORS (Cross Origin Resource Sharing) pour demander des ressources auprès d’un domaine autre que le domaine actuel. Le service Experience Cloud Identity prend en charge les normes CORS qui permettent d’envoyer des requêtes de ressources cross-origin côté client. Dans les navigateurs plus anciens ou non compatibles avec la norme CORS, les demandes JSONP sont restaurées.
seo-title: Prise en charge de la norme CORS dans le service Experience Cloud Identity
title: Prise en charge de la norme CORS dans le service Experience Cloud Identity
uuid: e656b573-72a8-4312-a7d5-5cc3818f0a9e
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 55%

---


# Prise en charge de la norme CORS dans le service Experience Cloud Identity {#cors-support-in-the-experience-cloud-id-service}

Les navigateurs utilisent la norme CORS (Cross Origin Resource Sharing) pour demander des ressources auprès d’un domaine autre que le domaine actuel. Le service Experience Cloud Identity prend en charge les normes CORS qui permettent d’envoyer des requêtes de ressources cross-origin côté client. Dans les navigateurs plus anciens ou non compatibles avec la norme CORS, les demandes JSONP sont restaurées.

## Problèmes liés aux règles sur la même origine et aux demandes de service d’ID {#section-6608cf46d27143eeaeabacaa6aa14e8e}

Les règles de même origine sont des contrôles de sécurité ou des restrictions appliqués par un navigateur Web. Lorsqu’elles sont appliquées à ce niveau, le navigateur Web lui-même détermine si une requête de ressources effectuée d’une page à une autre sera autorisée ou bloquée. Pour déterminer si une requête est une requête de même origine, le navigateur compare :

* URI (Uniform Resource Identifiers)
* Noms d’hôtes (par exemple, http://www.my-webpage-example.com)
* Numéros de port (par exemple, port 80 et 440 pour les requêtes HTTP et HTTPS)

Le navigateur permet à une requête de réussir si les deux pages partagent ces caractéristiques et bloque les requêtes de ressources dans le cas contraire.

## La norme CORS résout les problèmes liés aux règles de même origine {#section-76c87ec3295d447bab220c84f138c235}

CORS offre un moyen sécurisé et efficace de demander des ressources entre différents domaines. La spécification CORS comprend un ensemble d’en-têtes HTTP que les navigateurs utilisent pour envoyer, recevoir et évaluer les demandes de ressources. L’évaluation d’une demande de ressource s’appelle une *`preflight check`*. Cette vérification permet aux navigateurs et aux serveurs de déterminer quelles requêtes sont autorisées ou bloquées. La vérification en amont est transparente pour l’application, l’API ou le script qui demande une ressource. Deux en-têtes importants dans le processus de demande de ressources sont les suivants :

* `Origin` : un en-tête de demande qui identifie la source de la requête.
* `Access-Control-Allow-Origin` : un en-tête de réponse qui indique si une ressource peut être partagée avec le demandeur.

Observons le fonctionnement de ces en-têtes : Dans cet exemple, imaginons une entreprise de services financiers ayant mis en œuvre le service [!DNL Experience Cloud] ID sur son site, www.finance-website.com. Le tableau suivant définit comment les en-têtes de demande et de réponse CORS vérifient l&#39;accès à une ressource.

<table id="table_B004ACF52B5A4D33B1DCF7EA77BE4E6D"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Action </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Requête</b> </p> </td> 
   <td colname="col2"> <p>Alors que la page de l’entreprise financière se charge, le navigateur envoie une demande à <span class="codeph">dpm.demdex.net</span>. Il s’agit d’un appel au domaine des serveurs de collecte de données (DCS) utilisés par le service d’ID. Cette demande interdomaines comprend l’en-tête : </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Origin: https://www.finance-website.com</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Réponse</b> </p> </td> 
   <td colname="col2"> <p>La réponse du domaine du serveur de collecte de données comprend ces en-têtes qui donnent à la société financière l'accès aux ressources requises : </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Access-Control-Allow-Origin: https://www.finance-website.com</span> </li> 
      <li> <span class="codeph"> Access-Control-Allow-Credentials: true</span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

Voir aussi [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa).

## Autres avantages liés à l’utilisation des normes CORS {#section-6f44f30694c44f95bf9854b8a2af8449}

Le tableau ci-dessous décrit certains des avantages offerts par CORS aux clients qui utilisent le service d’ID.

<table id="table_AEB51A263D454F90B66E8C8D0513CF79"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Avantage </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><b>Sécurité renforcée</b> </p> </td> 
   <td colname="col2"> <p>CORS utilise <a href="https://developer.mozilla.org/fr-FR/docs/Web/API/XMLHttpRequest" format="https" scope="external"> XMLHttpRequest</a> pour demander et transférer des données. Cette méthode est plus sécurisée qu’une requête JSONP. Elle fait en sorte qu’il n’existe aucune façon d’exécuter du JavaScript aléatoire, qui peut être compris dans la réponse du DCS. La charge utile de réponse CORS XMLHttpRequest est analysée par le code JavaScript du service d’ID et n’est pas simplement exécutée dans une fonction de rappel. </p> <p> <p>Remarque : Pour accepter les cookies, la propriété <span class="codeph">withCredentials</span> de l’objet <span class="codeph">XMLHttpRequest</span> doit être définie sur <span class="codeph">true</span>. Cette propriété est prise en charge dans Chrome, Firefox, Internet Explorer (v10+), Opera et Safari. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>Amélioration des performances</b> </p> </td> 
   <td colname="col2"> <p>CORS aide à améliorer les performances car : </p> 
    <ul id="ul_EC3A178003A94D70883B914050D7C464"> 
     <li id="li_F8B44352BFBB46CDBD07AE40B9F2D0EC">Le navigateur gère les requêtes de ressources. Le processus de demande est transparent pour le service d’ID. </li> 
     <li id="li_C63E43A4CAB84210AB6A39100E5864BE">Contrairement aux requêtes JSONP asynchrones, le navigateur ne déclasse pas la priorité des requêtes CORS et ne les met pas en file d’attente. </li> 
     <li id="li_1A2A15F591B84D1BAED3CFAB391EEBEC">Le service d’ID répond de manière autorisée. Cela signifie que lorsqu’une URL est transmise en tant qu’<span class="codeph">origine</span>, le service d’ID lui donne accès aux ressources requises. </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

