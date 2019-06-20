---
description: Cette mise en œuvre permet aux clients d’utiliser le service d’ID sur des appareils qui ne peuvent pas accepter ou utiliser notre code JavaScript ou SDK. Cela inclut les appareils tels que les consoles de jeu, les téléviseurs intelligents ou d’autres appareils compatibles avec Internet. Reportez-vous à cette section pour la syntaxe, des exemples de code et des définitions.
keywords: Service d’identification
seo-description: Cette mise en œuvre permet aux clients d’utiliser le service d’ID sur des appareils qui ne peuvent pas accepter ou utiliser notre code JavaScript ou SDK. Cela inclut les appareils tels que les consoles de jeu, les téléviseurs intelligents ou d’autres appareils compatibles avec Internet. Reportez-vous à cette section pour la syntaxe, des exemples de code et des définitions.
seo-title: Intégration directe au service d'identité de Platform Platform
title: Intégration directe au service d'identité de Platform Platform
uuid: de 502 f 7 e-cffd -4130-b 3 ca -7 d 6 b 9 a 9 caae 9
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Intégration directe au service d&#39;identité de Platform Platform {#direct-integration-with-the-experience-cloud-id-service}

Cette mise en œuvre permet aux clients d’utiliser le service d’ID sur des appareils qui ne peuvent pas accepter ou utiliser notre code JavaScript ou SDK. Cela inclut les appareils tels que les consoles de jeu, les téléviseurs intelligents ou d’autres appareils compatibles avec Internet. Reportez-vous à cette section pour la syntaxe, des exemples de code et des définitions.

## du lien personnalisé{#section-a4754afec5ad40b6be00d6f1011d68bb}

Les appareils qui ne peuvent pas utiliser les bibliothèques de code VisitorAPI.js ou du SDK peuvent appeler directement les serveurs de collecte de données (DCS) utilisés par le service d’ID. Pour ce faire, appelez `dpm.demdex.net` et formatez votre requête comme indiqué ci-dessous. Le format *italique* indique un espace réservé variable.

![](assets/directSyntax.png)

Dans cet exemple de syntaxe, le `d_` préfixe identifie les paires clé-valeur de l&#39;appel comme variable de niveau système. Vous pouvez transmettre plusieurs `d_` paramètres au service d&#39;ID, mais rester concentré sur les paires clé-valeur comme indiqué dans le code ci-dessus. Pour plus d’informations sur les autres variables, voir [Attributs pris en charge pour les appels d’API DCS](https://marketing.adobe.com/resources/help/en_US/aam/dcs-keys.html) (Supported Attributes for DCS API Calls).

Le service d’ID prend en charge les appels HTTP et HTTPS. Utilisez HTTPS pour transmettre des données à partir d’une page sécurisée.

## Exemple de requête {#section-26302b8851704888b6f8e6b2071bcdb0}

Votre requête pourrait ressembler à l’exemple ci-dessous. Les variables longues ont été raccourcies.

![](assets/directExample.png)

## Exemple de réponse {#section-89bc103b3e9e4a8b98e74c32897b1200}

Le service d’ID renvoie les données dans un objet JSON comme indiqué ci-dessous. Votre réponse peut être différente.

```js
{
     "d_mid":"12345",
     "dcs_region":"6",
     "id_sync_ttl":"604800",
     "d_blob":"wxyz5432"
}
```

## Paramètres de demande et de réponse définis {#section-4a9912b545364dc4acad4f1ea5ec641d}

**Paramètres de requête**

<table id="table_C8FFA89AB74E4E31A6926CDE5CD54217"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Paramètre </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> dpm.demdex.net</span> </p> </td> 
   <td colname="col2"> <p>Domaine hérité contrôlé par <span class="keyword">Adobe</span>. Voir <a href="https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html" format="https" scope="external">Signification des appels vers le domaine Demdex</a> (Understanding Calls to the Demdex Domain). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_mid</span> </p> </td> 
   <td colname="col2"> <p>Identifiant visiteur Experience Cloud. Voir <a href="../introduction/cookies.md" format="dita" scope="local"> Cookies et service d'identité de Platform Platform</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_orgid</span> </p> </td> 
   <td colname="col2"> <p>ID d’organisation Experience Cloud. Pour obtenir de l’aide sur la recherche de cet ID, voir <a href="../reference/requirements.md" format="dita" scope="local"> Conditions requises pour le service d'identité de Platform Platform</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_cid</span> </p> </td> 
   <td colname="col2"> <p>Paramètre facultatif qui transmet le DPID (Data Provider ID), l'ID unique - ID (DPUUID) et un <a href="../reference/authenticated-state.md" format="dita" scope="local"> ID d'état authentifié</a> au service d'ID. Comme indiqué dans l’exemple de code, séparez le DPID et le DPUUID par le caractère de contrôle non imprimable <span class="codeph">%01</span>. </p> <p> <b>DPID et DPUUID</b> </p> <p>Dans le paramètre <span class="codeph">d_cid</span>, affectez chaque combinaison DPID et DPUUID associée au même paramètre <span class="codeph">d_cid</span>. Vous pouvez ainsi renvoyer plusieurs jeux d’ID dans une même requête. En outre, séparez le DPID, le DPUUID et l’indicateur d’authentification facultatif par le caractère de contrôle non imprimable <span class="codeph">%01</span>. Dans les exemples ci-dessous, les ID de fournisseur et d’utilisateur sont mis en évidence en <b>gras</b> dans la syntaxe. </p> 
    <ul id="ul_2E19D837296B40E9ACD096495CF711C5"> 
     <li id="li_5B94B057654440B99B989BA60E4ED053">Syntaxe : <span class="codeph">...d_cid=DPID%01DPUUID%01état d’authentification...</span> </li> 
     <li id="li_B07833EF51D54F088574B7B7F9FB841A">Exemple : <span class="codeph">… d_ cid = 123 % 01456011…</span> </li> 
    </ul> <p> <b>État d’authentification</b> </p> <p>Il s’agit d’un ID facultatif dans le paramètre <span class="codeph">d_cid</span>. Exprimé sous la forme d’un entier, il identifie les utilisateurs en fonction de leur état d’authentification comme indiqué ci-dessous : </p> 
    <ul id="ul_E2B36922B11C4AA2A9016B6E2DC9EDAA"> 
     <li id="li_31C018E3F9514B938C73EF40C436715F"> <span class="codeph"> 0</span> (Inconnu) </li> 
     <li id="li_1F125C3879324C2F8EF4613C0ECB5F02"> <span class="codeph"> 1</span> (Authentifié) </li> 
     <li id="li_EF6792D0115D407485079D5D7480D965"> <span class="codeph"> 2</span> (Déconnecté) </li> 
    </ul> <p>Pour indiquer un état d’authentification, vous devez définir cet indicateur après la variable ID d’utilisateur (UUID). Séparez l’UUID et l’indicateur d’authentification par le caractère de contrôle non imprimable <span class="codeph">%01</span>. Dans les exemples ci-dessous, les ID d’authentification sont mis en évidence en <b>gras</b> dans la syntaxe. </p> <p>Syntaxe : <span class="codeph">...d_cid=DPID%01DPUUID%01état d’authentification</span> </p> <p>Exemples : </p> 
    <ul id="ul_4C1054CE860A4D9C8DD85C2A8020C47F"> 
     <li id="li_AD4000BF3E0146C0BD37B1EC513EC314">Inconnu : <span class="codeph">...d_cid=123%01456%010...</span> </li> 
     <li id="li_B037D424AADA4D41BF29381A9602AE61">Authentifié : <span class="codeph">...d_cid=123%01456%011...</span> </li> 
     <li id="li_0410FCB9E60D4DD08E7898D814E1C3C9">Déconnecté : <span class="codeph">...d_cid=123%01456%012...</span> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> dcs_region</span> </p> </td> 
   <td colname="col2"> <p>Le service d’ID est un système réparti géographiquement et équilibré en charge. L’ID identifie la zone géographique du centre de données traitant l’appel. Voir <a href="https://marketing.adobe.com/resources/help/en_US/aam/dcs-regions.html" format="https" scope="external">ID de zone géographique, emplacements et noms d’hôte du serveur de collecte de données</a> (DCS Region IDs, Locations, and Host Names). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_cb</span> </p> </td> 
   <td colname="col2"> <p> <i>(Facultatif)</i> Paramètre de rappel permettant d’exécuter une fonction JavaScript dans le corps de la requête. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_blob</span> </p> </td> 
   <td colname="col2"> <p>Bloc chiffré de métadonnées JavaScript. Les restrictions de taille limitent le blob à 512 octets ou moins. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_ver</span> </p> </td> 
   <td colname="col2"> <p>Requis. Définit le numéro de version de l’API. Laissez ce paramètre défini sur <span class="codeph">d_ver=2</span>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Paramètres de réponse**

Certains paramètres de réponse font partie de la requête et ont été définis dans la section ci-dessus.

<table id="table_58D0E8876DDC4A81B1F24F845E87EC18"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Paramètre </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> id_sync_ttl</span> </p> </td> 
   <td colname="col2"> <p>Intervalle de resynchronisation, indiqué en secondes. L’intervalle par défaut est de 604 800 secondes (7 jours). </p> </td> 
  </tr> 
 </tbody> 
</table>
