---
description: Cette implémentation permet aux clients d’utiliser le service d’ID sur les périphériques qui ne peuvent pas accepter ou utiliser notre code JavaScript ou SDK. Cela inclut les périphériques tels que les consoles de jeux, les téléviseurs intelligents ou d’autres appareils compatibles avec Internet. Reportez-vous à cette section pour connaître la syntaxe, voir des exemples de code et les définitions.
keywords: ID Service
seo-description: Cette implémentation permet aux clients d’utiliser le service d’ID sur les périphériques qui ne peuvent pas accepter ou utiliser notre code JavaScript ou SDK. Cela inclut les périphériques tels que les consoles de jeux, les téléviseurs intelligents ou d’autres appareils compatibles avec Internet. Reportez-vous à cette section pour connaître la syntaxe, voir des exemples de code et les définitions.
seo-title: Intégration directe avec le service Experience Cloud Identity
title: Intégration directe avec le service Experience Cloud Identity
uuid: de502f7e-cffd-4130-b3ca-7d6b9a9caae9
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 100%

---


# Intégration directe avec le service Experience Cloud Identity {#direct-integration-with-the-experience-cloud-id-service}

Cette implémentation permet aux clients d’utiliser le service d’ID sur les périphériques qui ne peuvent pas accepter ou utiliser notre code JavaScript ou SDK. Cela inclut les périphériques tels que les consoles de jeux, les téléviseurs intelligents ou d’autres appareils compatibles avec Internet. Reportez-vous à cette section pour connaître la syntaxe, voir des exemples de code et les définitions.

## Syntaxe {#section-a4754afec5ad40b6be00d6f1011d68bb}

Les appareils qui ne peuvent pas utiliser les bibliothèques de code VisitorAPI.js ou du SDK peuvent appeler directement les serveurs de collecte de données (DCS) utilisés par le service d’ID. Pour ce faire, appelez `dpm.demdex.net` et formatez votre requête comme indiqué ci-dessous. Le format *italique* indique un espace réservé variable.

![](assets/directSyntax.png)

Dans cet exemple de syntaxe, le `d_` préfixe identifie les paires clé-valeur de l’appel en tant que variable de niveau système. Vous pouvez transmettre plusieurs `d_` paramètres au service d’ID, mais restez concentré sur les paires clé-valeur comme indiqué dans le code ci-dessus. Pour plus d’informations sur les autres variables, voir [Attributs pris en charge pour les appels d’API DCS](https://docs.adobe.com/content/help/fr-FR/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-keys.html).

Le service d’ID prend en charge les appels HTTP et HTTPS. Utilisez HTTPS pour transmettre des données à partir d’une page sécurisée.

## Exemple de requête {#section-26302b8851704888b6f8e6b2071bcdb0}

Votre demande peut ressembler à l’exemple ci-dessous. De longues variables ont été raccourcies.

![](assets/directExample.png)

## Exemple de réponse {#section-89bc103b3e9e4a8b98e74c32897b1200}

Le service d’ID renvoie des données dans un objet JSON, comme illustré ci-dessous. Votre réponse peut être différente.

```js
{
     "d_mid":"12345",
     "dcs_region":"6",
     "id_sync_ttl":"604800",
     "d_blob":"wxyz5432"
}
```

## Paramètres de requête et de réponse définis {#section-4a9912b545364dc4acad4f1ea5ec641d}

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
   <td colname="col2"> <p>Domaine hérité contrôlé par <span class="keyword">Adobe</span>. Voir <a href="https://docs.adobe.com/content/help/fr-FR/audience-manager/user-guide/reference/demdex-calls.html" format="https" scope="external">Signification des appels vers le domaine Demdex</a> (Understanding Calls to the Demdex Domain). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_mid</span> </p> </td> 
   <td colname="col2"> <p>ID de visiteur Experience Cloud. Voir <a href="../introduction/cookies.md" format="dita" scope="local">Cookies et service Experience Cloud Identity</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_orgid</span> </p> </td> 
   <td colname="col2"> <p>ID d’organisation Experience Cloud. Pour obtenir de l’aide sur la recherche de cet ID, voir <a href="../reference/requirements.md" format="dita" scope="local"> Conditions requises pour le service Experience Cloud Identity</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_cid</span> </p> </td> 
   <td colname="col2"> <p>Paramètre facultatif qui transmet l’ID du fournisseur de données (DPID), l’ID de l’utilisateur unique (DPUUID) et un <a href="../reference/authenticated-state.md" format="dita" scope="local"> ID d’état authentifié</a> au service d’ID. Comme indiqué dans l’exemple de code, séparez le DPID et le DPUUID par le caractère de contrôle non imprimable <span class="codeph">%01</span>. </p> <p> <b>DPID et DPUUID</b> </p> <p>Dans le paramètre <span class="codeph">d_cid</span>, affectez chaque combinaison DPID et DPUUID associée au même paramètre <span class="codeph">d_cid</span>. Vous pouvez ainsi renvoyer plusieurs jeux d’ID dans une même requête. En outre, séparez le DPID, le DPUUID et l’indicateur d’authentification facultatif par le caractère de contrôle non imprimable <span class="codeph">%01</span>. Dans les exemples ci-dessous, les ID de fournisseur et d’utilisateur sont mis en évidence en <b>gras</b> dans la syntaxe. </p> 
    <ul id="ul_2E19D837296B40E9ACD096495CF711C5"> 
     <li id="li_5B94B057654440B99B989BA60E4ED053">Syntaxe : <span class="codeph">...d_cid=DPID%01DPUUID%01état d’authentification...</span> </li> 
     <li id="li_B07833EF51D54F088574B7B7F9FB841A">Exemple : <span class="codeph">...d_cid=123%01456%011...</span> </li> 
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
   <td colname="col2"> <p>Le service d’ID est un système géographiquement réparti et dont la charge est équilibrée. L’identifiant identifie la région du centre de données qui gère l’appel. Voir <a href="https://docs.adobe.com/content/help/fr-FR/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html" format="https" scope="external">ID de zone géographique, emplacements et noms d’hôte du serveur de collecte de données</a> (DCS Region IDs, Locations, and Host Names). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_cb</span> </p> </td> 
   <td colname="col2"> <p> <i>(Facultatif)</i> Paramètre de rappel permettant d’exécuter une fonction JavaScript dans le corps de la requête. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_blob</span> </p> </td> 
   <td colname="col2"> <p>Bloc chiffré de métadonnées JavaScript. Les contraintes de taille limitent l’objet blob à 512 octets ou moins. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_ver</span> </p> </td> 
   <td colname="col2"> <p>Obligatoire. Cette opération définit le numéro de version de l’API. Laissez ce paramètre défini sur <span class="codeph">d_ver=2</span>. </p> </td> 
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
   <td colname="col2"> <p>Intervalle de resynchronisation, défini en secondes. L’intervalle par défaut est de 604 800 secondes (7 jours). </p> </td> 
  </tr> 
 </tbody> 
</table>

