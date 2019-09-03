---
description: Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service Experience Cloud Identity en 2017.
keywords: Service d’identification
seo-description: Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service Experience Cloud Identity en 2017.
seo-title: Notes de mise à jour 2017
title: Notes de mise à jour 2017
uuid: 79452df0-49db-42b8-96fe-01aa7629fbb5
translation-type: ht
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Notes de mise à jour 2017 {#release-notes}

Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service Experience Cloud Identity en 2017.

Ces modifications sont également reprises dans les [notes de mise à jour Experience Cloud](https://marketing.adobe.com/resources/help/fr_FR/whatsnew/). Pour obtenir des notes de mise à jour antérieures sur le service d’ID, reportez-vous aux [précédentes notes de mise à jour](https://marketing.adobe.com/resources/help/fr_FR/whatsnew/?f=c_legacy_releases) ou aux liens situés au bas de cette page.

>[!NOTE]
>
>Il n’existe pas de notes de mise à jour destinées au client ni de modifications du code pour les mois de mars, avril, mai et octobre 2017. Pour ces mois, le code du service d’ID est resté inchangé à la version 2.1.

## Version 2.5 {#section-27b441509124493f80984ed09bd9e88b}

Septembre 2017

<!--
<p>
<note type="important">
ID service support for Internet Explorer 6, 7, and 8 is deprecated and will be discontinued in a future release.
</note> </p>
-->

<table id="table_FD24C06C7B3547C3A7673C46B1852A35"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Fonction </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> getVisitorValues</span> </p> </td> 
   <td colname="col2"> <p>Il s’agit d’une API asynchrone qui renvoie les identifiants pour Analytics, le service d’ID, le droit d’opposition à la collecte de données, l’emplacement géographique et le contenu d’objet blob de métadonnées par défaut. Vous pouvez également contrôler les ID que vous souhaitez renvoyer à l’aide de l’énumération facultative <span class="codeph">visitor.FIELDS</span>. Voir <a href="../library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Correctifs et autres modifications**

* Correction d’un bogue lié à Chrome en raison duquel le service d’ID générait une erreur en cliquant sur le bouton Retour de ce navigateur.
* Le service d’ID relance désormais les synchronisations des identifiants lorsque l’ID de zone géographique de la réponse à l’appel d’événement change.
* Ajout d’une nouvelle documentation, [Stratégies de sécurité du contenu et service Experience Cloud Identity](/help/reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3), qui explique comment placer sur liste blanche les appels vers les domaines Adobe utilisés par le service d’ID.

## Version 2.4 {#section-f4d1608dd8894f558a92b82e83321200}

Août 2017

<table id="table_D9623D34F4444B038F7835750932C8AA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Fonction </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe</span> </p> </td> 
   <td colname="col2"> <p>Une configuration booléenne facultative permet de déterminer si le service d’ID envoie (ou n’envoie pas) des données à Adobe Experience Cloud Device Co-op. Voir <a href="../library/function-vars/coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local">isCoopSafe</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Documentation révisée**

Mise à jour et révision des [Questions fréquentes](/help/faq-intro/faq-intro.md) afin d’inclure des questions distinctes pour chaque solution [!DNL Experience Cloud].

## Version 2.3 {#section-ae7b1cb1e52e4ca5a46b453a3ba1f571}

Juillet 2017

<table id="table_1448040D09B94A74883A694FCF91EB33"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Fonction </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> sdidParamExpiry</span> </p> </td> 
   <td colname="col2"> <p>Ajoutée à la fonction <span class="codeph">Visitor.getInstance</span>, cette configuration vous permet de remplacer l’intervalle d’expiration de l’ID de données supplémentaire (SDID) par défaut lors du transfert de cet ID d’une page à une autre. Vous utiliserez <span class="codeph">sdidParamExpiry</span> avec la fonction auxiliaire <span class="codeph">appendSupplimentalDataTo</span>. Voir <a href="../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458" format="dita" scope="local">sdidParamExpiry</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> resetState</span> </p> </td> 
   <td colname="col2"> <p>Cette fonction s’adresse principalement aux utilisateurs d’A4T, pour les aider à résoudre des problèmes liés à l’utilisation d’identifiants sur des sites, écrans ou applications d’une seule page. Voir <a href="../library/get-set/resetstate.md#reference-47fc00ae139042d795d78244d9970139" format="dita" scope="local">resetState</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Correctifs et autres modifications**

* Correction d’un bogue dans VisitorAPI.js version 2.2 qui empêchait le service d’ID et Target de fonctionner ensemble dans Internet Explorer.
* Révision du code afin d’améliorer la façon dont le service d’ID envoie les données à l’iFrame de publication de destination. Cette modification réduit l’utilisation du processeur.

## Version 2.2 {#section-b7dee2495c29470e9b3a3132ec1fd951}

Date de publication : Juin 2017

<table id="table_7E412383E89D46759B00FE7328C9946F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Fonction </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/whitelistdomain.md#reference-999899ff7b5b429a8824c9db7a379808" format="dita" scope="local"> whitelistParentDomain et whitelistIframeDomains </a> </p> </td> 
   <td colname="col2"> <p>Ces configurations permettent à différentes instances du code du service d’ID mises en œuvre dans un iFrame et sur la page parente de communiquer les unes avec les autres. Elles visent à résoudre des problèmes survenant dans 2 cas d’utilisation : vous pouvez (ou non) contrôler la page ou le domaine parent et le code du service d’ID se charge dans l’iFrame d’un domaine que vous ne contrôlez pas. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Mises à jour de la documentation en mai {#section-1d36b91bb7a140ce8a145251ffac9f2f}

<table id="table_CD031A716A694E8FA89695C9B614BC91"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Rubrique </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../faq-intro/faq.md" format="dita" scope="local"> FAQ </a> </p> </td> 
   <td colname="col2"> <p>Mise à jour de la section <span class="keyword">Analytics</span> relative à la recherche d’informations sur le serveur de suivi. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Mises à jour de la documentation en avril {#section-df3e5a85448c4001a6791517520ae06e}

<table id="table_ADC2636240654C69B8B6A45849024540"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Rubrique </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/subdomain-config.md#reference-8ad017b3e5d24d34b3da25e8f8a56196" format="dita" scope="local"> audienceManagerServer et audienceManagerServerSecure </a> </p> </td> 
   <td colname="col2"> <p>Ajout de liens vers la documentation <span class="keyword">Audience Manager</span> qui décrit les appels au domaine <span class="codeph">demdex.net</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/subdomain-config.md" format="dita" scope="local"> Comprendre la synchronisation des identifiants et les taux de correspondance </a> </p> </td> 
   <td colname="col2"> <p>Modification de la section <span class="keyword">Media Optimizer</span> afin de décrire l’appel à <span class="codeph">cm.eversttech.net</span>. Il s’agit de la synchronisation automatique des identifiants effectuée par le service d’ID avec <span class="keyword">Media Optimizer</span>. Cette fonctionnalité a été publiée en janvier 2017. Voir <a href="../release-notes/notes-2017.md#section-0ceac6007c1241b58ad607e2b76b2b7e" format="dita" scope="local">Version 2.0</a> ci-dessous. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Version 2.1 {#section-5e666dc47c2f4f92999e92697d75799e}

Date de publication : février 2017

**Fonctionnalités**

<table id="table_1F7E1CF091604D22B1D9F3F1AE4DB2D7"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Fonction </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> Propriété de l’API de service d’identification, <span class="codeph">idSyncContainerID</span></p> </td> 
   <td colname="col2"> <p>Cette propriété définit l’identifiant du conteneur utilisé par <span class="keyword">Audience Manager</span> pour la synchronisation des identifiants. Voir <a href="/help/library/function-vars/idsyncontainerid.md" format="https" scope="external"> idSyncContainerID</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Méthode d’API de service d’identification, <span class="codeph">appendSupplementalDataIDTo(<span class="varname"> URL</span>,<span class="varname"> SDID</span>)</span></p> </td> 
   <td colname="col2"> <p>Cette méthode publique ajoute le <span class="wintitle">SDID (Supplemental Data ID)</span> comme paramètre de chaîne de requête à une URL de redirection. Voir <a href="../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d" format="dita" scope="local"> appendSupplementalDataIDTo</a>. (MCID-285) </p> </td> 
  </tr> 
 </tbody> 
</table>

**Correctifs**

Correction d’un bogue en raison duquel le service d’identification envoyait des appels redondants au serveur pour un identifiant plutôt que d’utiliser celui qui était stocké dans le cookie AMCV. (MCID-296)

**Nouvelle documentation**

[Utilisation de la prérécupération DNS avec différentes solutions et services Experience Cloud`Learn how to use DNS prefetch to help reduce page load times.`](
https://marketing.adobe.com/resources/help/fr_FR/mcloud/dns-prefetch.html)

## Version 2.0 {#section-0ceac6007c1241b58ad607e2b76b2b7e}

Janvier 2017

>[!IMPORTANT]
>
>Le code du service d’ID de la version 2.0 synchronise automatiquement les identifiants avec Adobe Media Optimizer, par défaut. Cela signifie que vous verrez un appel depuis la page à `cm.eversttech.net`, qui est un domaine hérité de [!DNL Media Optimizer] contrôlé par [!DNL Adobe]. Voir la documentation [Comprendre la synchronisation des identifiants et les taux de correspondance](../introduction/match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab).

**Correctifs et améliorations**

* Résolution d’un bogue empêchant AppMeasurement d’effectuer des appels de suivi vers Analytics. (MCID-254, MCID-256, MCID-286)
* Résolution d’un bogue qui empêchait la fermeture immédiate du service d’ID juste après qu’un visiteur a activé un bloqueur d’annonces publicitaires configuré pour exclure le domaine demdex.net. Ce bogue reste rare et inhabituel car la plupart des bloqueurs d’annonces publicitaires ne bloquent pas le domaine demdex.net. (MCID-233)
* Résolution d’un bogue généré par des interactions entre le code de service ID et un script personnalisé sur un site Web client. Ce problème empêche Internet Explorer 9 de charger les pages Web. (MCID-206)

## Années précédentes {#section-aaabe2b7b0f04641b24acffc11cd7d2e}

Notes de mise à jour précédentes relatives au service d’ID.
