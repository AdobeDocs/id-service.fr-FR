---
description: Les fonctions du service d’ID idSyncByURL et idSyncByDataSource vous permettent de mettre en œuvre manuellement la synchronisation d’un identifiant dans l’iFrame de publication de destination. Elles sont disponibles dans VisitorAPI.js 1.10 ou version ultérieure.
keywords: Service d’identification
seo-description: Les fonctions du service d’ID idSyncByURL et idSyncByDataSource vous permettent de mettre en œuvre manuellement la synchronisation d’un identifiant dans l’iFrame de publication de destination. Elles sont disponibles dans VisitorAPI.js 1.10 ou version ultérieure.
seo-title: Synchronisation des ID par URL ou source de données
title: Synchronisation des ID par URL ou source de données
uuid: ff 83 d 910-8375-4295-9 f 2 a-e 14 c 15 eee 09 a
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# Synchronisation des ID par URL ou source de données{#id-synchronization-by-url-or-data-source}

Les fonctions du service d’ID idSyncByURL et idSyncByDataSource vous permettent de mettre en œuvre manuellement la synchronisation d’un identifiant dans l’iFrame de publication de destination. Elles sont disponibles dans VisitorAPI.js 1.10 ou version ultérieure.

Contenu :

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/idsync.md#section-90ac61617482463aaf4c57009b830332" format="dita" scope="local"> Syntaxe, propriétés et macros </a> </li> 
 <li> <a href="../../library/get-set/idsync.md#section-0115615c37584a19a2ab11e917c4e7e9" format="dita" scope="local"> Exemple de code et de résultat </a> </li> 
</ul>

## Syntaxe, propriétés et macros {#section-90ac61617482463aaf4c57009b830332}

**Syntaxe**

<table id="table_ADC7501511914805A6A6B24B2DFEBA51"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Code </th> 
   <th colname="col2" class="entry"> Synchronise les identifiants des utilisateurs </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByURL(); </span> </p> </td> 
   <td colname="col2"> <p>Entre différents partenaires de données et <span class="keyword">Audience Manager</span> en utilisant une URL de synchronisation d’identifiant personnalisé. </p> <p> 
     <draft-comment>
       Entre différents partenaires de données et Audience Manager. Par exemple, le partenaire x l'utilise pour synchroniser un utilisateur - id avec le partenaire y, puis l'envoyer à Audience Manager. 
     </draft-comment> </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByDataSource(); </span> </p> </td> 
   <td colname="col2"> <p>Si vous connaissez déjà le DPID et DPUUID et si vous voulez l’envoyer à <span class="keyword">Audience Manager</span> dans le format d’URL de synchronisation d’identifiant standard. </p> <p> 
     <draft-comment>
       Lorsque vous connaissez déjà l'utilisateur - id et souhaitez l'envoyer à Audience Manager. 
     </draft-comment> </p> </td> 
  </tr> 
 </tbody> 
</table>

**Propriétés**

Le tableau suivant répertorie et définit les propriétés disponibles pour les deux fonctions.

<table id="table_5343BE784E694C67B09A0A8878CF8001"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Nom </th> 
   <th colname="col2" class="entry"> Type </th> 
   <th colname="col3" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> dpid </span> </td> 
   <td colname="col2"> Chaîne </td> 
   <td colname="col3"> <p>Identifiant de fournisseur de données attribué par Audience Manager. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> dpuuid </span> </td> 
   <td colname="col2"> Chaîne </td> 
   <td colname="col3"> <p>L’identifiant unique du fournisseur de données pour l’utilisateur. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> minutesToLive </span> </td> 
   <td colname="col2"> Nombre </td> 
   <td colname="col3"> <p> <i>(Optionnel)</i> Définit le délai d’expiration du cookie. Doit être un nombre entier. Sa valeur par défaut est de 20 160 minutes (14 jours). </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> url </span> </td> 
   <td colname="col2"> Chaîne </td> 
   <td colname="col3"> <p>URL de destination. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Macros**

Les deux fonctions acceptent les macros suivantes :

* ** `%TIMESTAMP%`: ** Génère un horodatage (en millisecondes). Utilisé pour la mise en cache.
* ** `%DID%`: ** Insère l&#39;identifiant Audience Manager pour l&#39;utilisateur.
* ** `%HTTP_PROTO%`: ** Définit le protocole de communication ( `http` ou `https`).

## Exemple de code et résultat {#section-0115615c37584a19a2ab11e917c4e7e9}

Les deux fonctions reviennent `Successfully queued` en cas de réussite. Autrement, elles renvoient une chaîne contenant un message d’erreur.

**visitor.idSyncByURL**

<table id="table_56AD8291DF9445C69CC2BF50435E1626"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Exemple de code </th> 
   <th colname="col2" class="entry"> Exemple de résultat </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <code class="syntax javascript"> //instatiate visiteur 
 var visitor = Visitor. getinstance (« MARKETING-CLOUD-ORG-ID-HERE », {}) ;

    // &amp; amp ; nbsp ; Feu &amp; amp ; nbsp ; url &amp; amp ; nbsp ; avec &amp; amp ; nbsp ; macros &amp; amp ; nbsp ; replacedvisitor
    . idsyncbyurl ({
    &amp; amp ; nbsp ; dpid : &amp; amp ; nbsp ; &#39; 24 &#39;, &amp; amp ; nbsp ; // &amp; amp ; nbsp ; must &amp; amp ; nbsp ; be &amp; amp ; nbsp ; a &amp; amp ; nbsp ; string
    &amp; amp ; nbsp ; url : &amp; amp ; nbsp ; &#39;//su.addthis.com/red/usync?pid=16&amp;amp;puid=%DID%&amp;amp;url=%HTTP_PROTO%%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D&#39;,&amp;nbsp;minutesToLive:&amp;nbsp;20160&amp;nbsp;//&amp;nbsp;optional,&amp;nbsp;defaults&amp;nbsp;to&amp;nbsp;20160&amp;nbsp;minutes&amp;nbsp;(14&amp;nbsp;days)&amp;nbsp
    ;
    }) ; &lt;/code &gt; &lt;/p &gt; &lt;/td &gt;
<td colname="col2"> <p> <span class="codeph"> http://su.addthis.com/red/usync?pid=16&amp;puid=28777806459181003670799219185178493848&amp;url=http%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D </span> </p> </td> 
  </tr> 
 </tbody> 
</table>

**visitor.idSyncByDataSource**

<table id="table_90D61A7E715D47238AAFF2808B33C2F0"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Exemple de code </th> 
   <th colname="col2" class="entry"> Exemple de résultat </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <code class="syntax javascript"> //instantiate visiteur 
 var visitor = Visitor. getinstance (« MARKETING-CLOUD-ORG-ID-HERE », {}) ;

    // &amp; amp ; nbsp ; Feu &amp; amp ; nbsp ; &#39; http:/https:&#39;&amp;nbsp;+&amp;nbsp;&#39;//dpm.demdex.net/ibs:dpid=&amp;lt;dpid&amp;gt;&amp;amp;dpuuid=&amp;lt;dpuuid&amp;gt;&#39;visitor.idSyncByDataSource(
    {
    &amp; amp ; nbsp ; dpid : &amp; amp ; nbsp ; &#39; 24 &#39;, &amp; amp ; nbsp ; // &amp; amp ; nbsp ; must &amp; amp ; nbsp ; be &amp; amp ; nbsp ; a &amp; amp ; nbsp ; string
    &amp; amp ; nbsp ; dpuuid : &amp; amp ; nbsp ; &#39; 98765 &#39;, &amp; amp ; nbsp ; // &amp; amp ; nbsp ; must &amp; amp ; nbsp ; be &amp; amp ; nbsp ; a &amp; amp ; nbsp ; string
    &amp; amp ; nbsp ; Minutestolive : &amp; amp ; nbsp ; 20160 &amp; amp ; nbsp ; // &amp; amp ; nbsp ; optional, &amp; amp ; nbsp ; valeurs par défaut et amp ; nbsp ; to &amp; amp ; nbsp ; 20160 &amp; amp ; nbsp ; minutes &amp; amp ; nbsp ; (14 &amp; amp ; nbsp ; days) &amp; amp ; nbsp ;
    }) ; &lt;/code &gt; &lt;/p &gt; &lt;/td &gt;
<td colname="col2"> <p> <span class="codeph"> http://dpm.demdex.net/ibs:dpid=24&amp;dpuuid=98765 </span> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!MORE_ LIKE_ THIS]
>
>* [DIL idSync](https://marketing.adobe.com/resources/help/en_US/aam/r_dil_idsync.html)

