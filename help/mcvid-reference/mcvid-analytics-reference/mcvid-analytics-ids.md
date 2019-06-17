---
description: Le service Experience Cloud ID remplace les anciennes méthodes d’identification des visiteurs d’Analytics.
keywords: Service d’identification
seo-description: Le service Experience Cloud ID remplace les anciennes méthodes d’identification des visiteurs d’Analytics.
seo-title: Définition des Analytics ID et Experience Cloud ID
title: Définition des Analytics ID et Experience Cloud ID
uuid: 421 cf 597-a 3 e 0-4 ca 3-8 ce 8-d 0 c 80 cbb 6 aca
translation-type: tm+mt
source-git-commit: ab9290769cd5fd6d5da7e664bac8ad467cb95166

---


# Définition des Analytics ID et Experience Cloud ID{#setting-analytics-and-experience-cloud-ids}

Le service Experience Cloud ID remplace les anciennes méthodes d’identification des visiteurs d’Analytics.

Une fois le service d’ID mis en œuvre, son code s’exécute avant AppMeasurement. Le service d’ID récupère les Experience Cloud et Analytics ID afin que ces valeurs soient prêtes au chargement d’AppMeasurement.

Au chargement d’AppMeasurement, les valeurs des Experience Cloud et Analytics ID sont demandées par le service d’ID et sont envoyées à la collecte de données avec chaque appel au serveur. Dans la mesure où le service d’ID détermine l’identifiant du visiteur et le transmet simplement à AppMeasurement, il doit être inclus et implémenté sur chaque page avant votre fichier JavaScript AppMeasurement.

## Modifications du processus d’Analytics ID {#section-79bb86ae63f546419bb1a7ef5e710462}

Le principal changement lors de la migration vers le service [!DNL Experience Cloud] ID concerne la définition du cookie ID. Désormais, il est défini à l’aide de JavaScript, plutôt que dans l’en-tête HTTP renvoyé par le serveur web de collecte de données. Pour vous permettre de bien comprendre ce changement, vous trouverez une description de ces deux méthodes dans les sections suivantes.

**En-tête HTTP**

Une réponse HTTP d’un serveur Web définit les cookies dans un navigateur. Il s&#39;agit de la manière dont `s_vi` le cookie est défini. `s_vi` Le cookie identifie les visiteurs Analytics. Une fois défini, le cookie est envoyé à ce serveur avec toutes les demandes HTTP ultérieures.

Lors de l’envoi d’une demande au serveur de collecte de données Adobe, le cookie `s_vi` est recherché dans l’en-tête. S’il est présent dans la demande, il est utilisé pour identifier le visiteur. Dans le cas contraire, le serveur génère un [!DNL Experience Cloud] ID unique, le définit comme cookie dans l’en-tête de réponse HTTP, puis le renvoie avec la requête. Le cookie est stocké dans le navigateur et renvoyé au serveur de collecte de données au cours des visites suivantes du site. Le visiteur peut être ainsi identifié lors d’autres visites.

Certains navigateurs, comme Apple Safari, n’acceptent toutefois pas de cookies tiers. Il s’agit de cookies définis dans le navigateur à partir des domaines autres que le site Web actuel. En outre, Safari bloque les cookies des domaines tiers si un visiteur ne s’est pas rendu auparavant sur celui-ci. Supposons que vous visitiez le site `mysite.com` et que votre serveur de collecte de données soit `mysite.omtrdc.net`. Dans ce cas, le cookie renvoyé dans l’en-tête HTTP en provenance de `mysite.omtrdc.net` risque d’être rejeté par le navigateur.

Pour éviter ce cas de figure, de nombreux clients ont implémenté des enregistrements CNAME pour leurs serveurs de collecte de données dans le cadre d’une stratégie de [mise en œuvre de cookies propriétaires](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/). Si un enregistrement CNAME est configuré pour mapper un nom d’hôte sur le domaine du client au serveur de collecte de données (mappage de `metrics.mysite.com` à `mysite.omtrdc.net`, par exemple), le cookie [!DNL Experience Cloud] ID est stocké, étant donné que le domaine de collecte de données correspond désormais à celui du site web. Cela a pour effet d’augmenter la probabilité de stockage du cookie du service d’ID. Toutefois, cette méthode s’accompagne d’une surcharge de travail, dans la mesure où vous devez configurer des enregistrements CNAME et gérer des certificats SSL pour les serveurs de collecte de données.

**JavaScript **

JavaScript peut lire et écrire des cookies définis sur le domaine propriétaire (domaine du site Web actuel). Le service [!DNL Experience Cloud] ID applique cette méthode pour définir le cookie `AMCV_###@AdobeOrg` qui contient tous les identifiants visiteur. De cette manière, le domaine du serveur de suivi ne doit plus nécessairement correspondre à celui du site web pour que le cookie Identifiant visiteur soit stocké. Dans la plupart des cas, il s’agit de la méthode privilégiée pour définir le cookie du service d’ID puisque cette méthode élimine les frais liés aux enregistrements CNAME et aux certificats SSL.

Dans certains cas, cependant, la définition du cookie dans l’en-tête HTTP s’avère bénéfique dans le cadre du suivi inter-domaines. C’est ce qui est décrit dans la section [CNAME de collecte de données et suivi inter-domaines](../../mcvid-reference/mcvid-analytics-reference/mcvid-cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d).

## Analytics ID personnalisés {#section-b6a7bd19e9ff432390010062450808f6}

La définition d’un ID de client à l’aide de `s.visitorID` permet d’identifier les utilisateurs dans Analytics. Cependant, les intégrations dans lesquelles des données Analytics sont exportées ou importées à l’aide du service d’identification ne fonctionneront pas lorsqu’un visiteur est identifié à l’aide de `s.visitorID`.

Cela comprend, sans s’y limiter, les audiences partagées, Analytics for Target (A4T) et les attributs du client. Pour ces intégrations, la définition d’un Analytics ID personnalisé n’est pas prise en charge.

## Classement des identifiants visiteur Analytics {#section-de1dc9fc9b6d4388995b70e35b8bcddf}

Après avoir déployé le service d’identification des visiteurs, il existe cinq façons d’identifier un visiteur dans Analytics (répertoriées dans le tableau ci-dessous par ordre de préférence) :

<table id="table_D267D36451F643D1BB68AF6FEAA6AD1A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Ordre utilisé </th> 
   <th colname="col2" class="entry"> Paramètre de requête (méthode de collecte) </th> 
   <th colname="col3" class="entry"> Présent quand </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <img id="image_9F3E58898A1B4F40BBDEF5ADE362E55C" src="assets/step1_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_custom" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p>s.visitorID est défini. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_77A06981672745B6AEA8BB4D55911CCA" src="assets/step2_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_analytics" format="http" scope="external"> aid (cookie s_vi)</a> </p> </td> 
   <td colname="col3"> <p>Le visiteur avait un cookie s_ vi existant avant le déploiement du service <span class="keyword"> Experience Cloud</span> ID ou vous avez configuré une <a href="../../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md" format="dita" scope="local"> période</a> de grâce. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_0A950B1A6B004387AFEE8EED882739CB" src="assets/step3_icon.png" /> </p> </td> 
   <td colname="col2"> <p>mid (cookie AMCV_ défini par le service d’identification des visiteurs d’Experience Cloud) </p> </td> 
   <td colname="col3"> <p>Le navigateur du visiteur accepte les cookies propriétaires. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_6F0ED8FE3EF846CA8E6ECCC3C0070D85" src="assets/step4_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> fid (cookie de secours sur H.25.3 ou plus récent ou AppMeasurement pour JavaScript)</a> </p> </td> 
   <td colname="col3"> <p>Un navigateur n’accepte pas les cookies tiers. Or, le serveur de suivi Analytics est configuré en tant que serveur de suivi tiers. </p> <p> <p>Remarque : Le <span class="codeph">fid</span> est un identifiant hérité. Il n’est pas utilisé si vous avez implémenté le service d’ID sur votre site. Dans ce cas, <span class="codeph"> le fid n'</span> est pas nécessaire, car le cookie <a href="../../mcvid-introduction/mcvid-cookies.md" format="dita" scope="local"> AMCV propriétaire</a> le rend obsolète. Il a été conservé pour prendre en charge le code hérité et pour des raisons historiques. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_23D8C0EB69EC4084BC237B5B98C036F4" src="assets/step5_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> Adresse IP, Agent utilisateur, Adresse IP de passerelle</a> </p> </td> 
   <td colname="col3"> <p>Le navigateur du visiteur n’accepte pas les cookies. </p> </td> 
  </tr> 
 </tbody> 
</table>

Dans de nombreux scénarios, il se peut qu’il y ait 2 ou 3 ID distincts pour un appel. Analytics utilisera comme [!DNL Experience Cloud] ID officiel le premier ID présent dans cette liste. Par exemple, si vous définissez un identifiant visiteur personnalisé (y compris dans le paramètre de requête « vid »), cet identifiant sera utilisé avant les autres identifiants susceptibles d’être présents pour ce même accès.

>[!MORE_ LIKE_ THIS]
>
>* [Ordre des opérations pour les Analytics ID](../../mcvid-reference/mcvid-analytics-reference/mcvid-analytics-order-of-operations.md#concept-b92935b4fff545adb4773f3728bc15ef)
