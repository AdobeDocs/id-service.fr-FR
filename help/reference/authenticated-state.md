---
description: Avec l’identifiant visiteur Experience Cloud, vous pouvez associer d’autres ID de client et un état d’authentification à chaque visiteur.
keywords: Service d’identification
seo-description: Avec l’identifiant visiteur Experience Cloud, vous pouvez associer d’autres ID de client et un état d’authentification à chaque visiteur.
seo-title: ID de client et états d’authentification
title: ID de client et états d’authentification
uuid: 643df363-224a-463e-a332-be59926b47e7
translation-type: ht
source-git-commit: ee07ec0fd83932ab5006dcdbece61608f4e4606e

---


# ID de client et états d’authentification {#customer-ids-and-authentication-states}

Avec l’identifiant visiteur Experience Cloud, vous pouvez associer d’autres ID de client et un état d’authentification à chaque visiteur.

## États d’authentification {#section-68ad4065dfaa437d9070832d6e2bf85c}

La `setCustomerIDs` méthode accepte plusieurs ID de client pour un même visiteur. Vous pouvez ainsi identifier ou cibler un utilisateur sur différents appareils. Vous pouvez par exemple télécharger ces ID en tant qu’[attributs du client](https://docs.adobe.com/content/help/fr-FR/core-services/interface/customer-attributes/attributes.html) vers [!DNL Experience Cloud] et accéder à ces données à partir de différentes solutions.

>[!IMPORTANT]
>
>`setCustomerIDs` (synchronisation des ID de client) est requis pour les fonctionnalités d’attributs du client et des services principaux. La synchronisation des ID de client est une méthode d’identification facultative pour [!DNL Analytics]. [!DNL Target] nécessite `Visitor.AuthState.AUTHENTICATED` pour que les attributs du client fonctionnent. Pour obtenir des exemples, voir [Services principaux – Comment activer vos solutions](https://docs.adobe.com/content/help/fr-FR/core-services/interface/about-core-services/core-services.html).

À partir de la version 1.5 du service Experience Cloud Identity, `setCustomerIDs` comprend l’objet `AuthState` facultatif. `AuthState` identifie les visiteurs selon leur état d’authentification (connecté ou déconnecté, par exemple). Vous définissez l’état d’authentification avec une valeur d’état répertoriée dans le tableau. L’état d’authentification est renvoyé sous la forme d’un entier.

<table id="table_8547671CC97145529981FBF6C302BEC5"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> État d’authentification </th> 
   <th colname="col2" class="entry"> Entier d’état </th> 
   <th colname="col3" class="entry"> État d’utilisateur </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.UNKNOWN </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 0 </span> </p> </td> 
   <td colname="col3"> <p>Inconnu ou jamais authentifié. </p> <p> L’état inconnu est appliqué par défaut lorsque <span class="codeph">AuthState</span> n’est pas utilisé avec un ID de visiteur ou qu’il n’est pas défini explicitement sur chaque page ou contexte d’application. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 1 </span> </p> </td> 
   <td colname="col3"> <p>Authentifié pour une instance, une page ou une application spécifique. </p> <p> <p>Attention : Pour bien fonctionner, les attributs du client pour <span class="keyword">Target</span> nécessitent cet état. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 2 </span> </p> </td> 
   <td colname="col3"> <p>Déconnecté. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Cas d’utilisation des états d’authentification {#section-fe9560cc490943b29dac2c4fb6efd72c}

Vous pouvez affecter des états d’authentification à vos utilisateurs selon les actions qu’ils effectuent sur vos propriétés web et selon s’ils sont authentifiés. Voir les exemples dans le tableau ci-dessous :

<table id="table_3769E79304014C4F87094B87A8ACE4E0"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> État d’authentification </th> 
   <th colname="col2" class="entry"> Exemple d’utilisation </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.UNKNOWN </span> </p> </td> 
   <td colname="col2"> <p>Cet état peut être utilisé pour des scénarios tels que : </p> <p> 
     <ul id="ul_086C7446D258443DA7AF5BB96A6AAEC7"> 
      <li id="li_7845BBD62D7B4362AD3FE33DEDA8FBA1">La lecture d’un email (cette action signifie probablement que le lecteur est le destinataire d’origine, mais il se peut également que l’email ait été transféré). </li> 
      <li id="li_FAB7ACFC69624631BD01FC0ED84B23C5">Le fait de se rendre sur une page de destination en cliquant sur un lien contenu dans un email. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p>L’utilisateur est actuellement authentifié dans une session active sur votre site web ou votre application. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p>L’utilisateur était authentifié, mais actuellement déconnecté. Celui-ci a eu l’intention de se déconnecter de l’état d’authentification. Il ne souhaite plus être considéré comme authentifié. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Définition des ID de client et des états authentifiés {#section-ec4b367d16ad4ac1a1baca9b01f4ee98}

Les ID de client peuvent contenir des combinaisons d’ID et d’états authentifiés comme l’illustrent les exemples ci-après.

>[!IMPORTANT]
>
>* Les identifiants sont sensibles à la casse.
>* Utilisez uniquement des valeurs non codées pour les identifiants.
>* Les ID de client et les états d’authentification ne sont pas stockés dans le cookie Identifiant visiteur. Ils doivent être définis pour chaque page ou contexte d’application.
>* N’incluez aucune information d’identification personnelle dans les identifiants client. Si vous utilisez des informations d’identification personnelle pour identifier un visiteur (par exemple, une adresse électronique), il est recommandé de stocker plutôt une version hachée ou chiffrée de l’information. La bibliothèque ECID prend en charge le hachage des identifiants utilisateur. Reportez-vous à la section [Prise en charge du hachage SHA-256 pour setCustomerIDs](/help/reference/hashing-support.md).
>



```js
// Single ID with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
/* 
Multiple IDs with only the first ID explicitly assigned an authentication state. 
The second ID is not explicitly assigned an authentication state and is implicitly 
assigned Visitor.AuthState.Unknown by default. 
*/ 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":"550e8400-e29b-41d4-a716-446655440000" 
}); 
 
// Multiple IDs with identical authentication states 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
// Multiple IDs with different authentication states 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":Visitor.AuthState.LOGGED_OUT 
    } 
}); 
```

## Renvoi des ID de client et des états authentifiés {#section-71a610546188478fa9a3185a01d6e83b}

Utilisez `getCustomerIDs` pour renvoyer les ID de client et les états authentifiés associés. Cette méthode renvoie l’état authentifié d’un visiteur sous la forme d’un entier.

**Syntaxe**

`getCustomerIDs` renvoie les données avec la syntaxe ci-après.

```js
{ 
    [customerIDType1]:{ 
        "id":[customerID1], 
        "authState":[authState1] 
    }, 
    [customerIDType2]:{ 
        "id":[customerID2], 
        "authState":[authState2] 
    } 
    ... 
}
```

**Exemples**

Les ID de client et les données sur l’état d’authentification renvoyés doivent ressembler à ceux des exemples ci-après.

```js
Object customerIDs = visitor.getCustomerIDs(); 
  
// No setCustomerIDs call on this instance 
{} 
  
// setCustomerIDs call on this instance with {"userid":{"id":"67312378756723456"}} 
{ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":0 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"id":"67312378756723456","authState":Visitor.AuthState.AUTHENTICATED}} 
{ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":1 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"authState":Visitor.AuthState.LOGGED_OUT}} 
{ 
    "userid":{ 
        "authState":2 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"authState":Visitor.AuthState.LOGGED_OUT},"dpuuid":{"id":"550e8400-e29b-41d4-a716-446655440000"}} 
{ 
    "userid":{ 
        "authState":2 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":0 
    } 
 }
```

## Prise en charge du SDK {#section-861c6b3b1ba645dda133dccb22ec7bb0}

Le service [!DNL Experience Cloud] ID prend en charge les identifiants et les états d’authentification du client dans le code de nos SDK Android et iOS. Voir les bibliothèques de code suivantes :

* [Méthodes du SDK Android](https://docs.adobe.com/content/help/fr-FR/mobile-services/android/overview.html)
* [Méthodes du SDK iOS](https://docs.adobe.com/content/help/fr-FR/mobile-services/ios/overview.html)

## Remarque destinée aux clients Analytics et Audience Manager {#section-3a8e9d51e71c4c6e865184b81ed9d99b}

Si vous transmettez des ID déclarés à [!DNL Audience Manager], l’objet `userid` doit correspondre au code d’intégration associé à une source de données. Pour plus d’informations, reportez-vous à la section relative au [!UICONTROL service d’identification des visiteurs] de la documentation sur la [configuration du code des règles de fusion](https://docs.adobe.com/help/fr-FR/audience-manager/user-guide/features/profile-merge-rules/merge-rules-start.html#configure-merge-rule-code).
