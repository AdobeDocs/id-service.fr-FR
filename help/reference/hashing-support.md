---
description: Le service ECID (Experience Cloud ID Service) prend en charge l'algorithme de hachage SHA -256 qui permet de transmettre des ID de client ou des adresses électroniques, et transmet des identifiants hachés. Il s'agit d'une méthode Javascript facultative pour envoyer des identifiants hachés à Experience Cloud. Vous pouvez continuer à utiliser vos propres méthodes de hachage avant d'envoyer les ID de client.
keywords: Service d’identification
seo-description: Le service ECID (Experience Cloud ID Service) prend en charge l'algorithme de hachage SHA -256 qui permet de transmettre des ID de client ou des adresses électroniques, et transmet des identifiants hachés. Il s'agit d'une méthode Javascript facultative pour envoyer des identifiants hachés à Experience Cloud. Vous pouvez continuer à utiliser vos propres méthodes de hachage avant d'envoyer les ID de client.
seo-title: Prise en charge de hachage SHA 256 pour setcustomerids
title: Prise en charge de hachage SHA 256 pour setcustomerids
translation-type: tm+mt
source-git-commit: ac1131be75fd04b51cd1d646086e1802a43afb18

---


# SHA256 Hashing Support for `setCustomerIDs` {#hashing-support}

Le service ECID (Experience Cloud ID Service) prend en charge l'algorithme de hachage SHA -256 qui permet de transmettre des ID de client ou des adresses électroniques, et transmet des identifiants hachés. Il s'agit d'une méthode Javascript facultative pour envoyer des identifiants hachés à Experience Cloud. Vous pouvez continuer à utiliser vos propres méthodes de hachage avant d'envoyer les ID de client.
Il existe deux façons d'implémenter la prise en charge de hachage avec setcustomerids, comme décrit dans les sections ci-dessous :

* [Utilisation de la méthode setcustomerids dans ECID](/help/reference/hashing-support.md#use-setcustomerids-method)
* [Ajout d'une action dans le lancement d'Adobe Experience Platform](/help/reference/hashing-support.md#add-action-launch)

## Use the `setCustomerIDs` method in ECID {#use-setcustomerids-method}

The first method leverages using the [`setCustomerIDs`](/help/library/get-set/setcustomerids.md) (`customerIDs<object>`, `hashType<string>`) method.

Avant de procéder au hachage, la bibliothèque ECID effectue la normalisation des données sur les customerids. Ce processus supprime les espaces des customerids sur les deux extrémités et convertit tous les caractères en minuscules. Par exemple, en cas d'adresses électroniques : « ecid@adobe.com » devient « ecid@adobe.com »

Reportez-vous à un exemple de code de la façon dont vous définissez un identifiant client unique (l'adresse électronique mentionnée ci-dessus) avec un hachage SHA -256.

```
// Set single customerID with SHA-256 hashing
visitor.setCustomerIDs({email: {id: "ecid@adobe.com", authState: 1}}, "SHA-256");
```

<br> 

Avec l'identifiant visiteur Experience Cloud, vous pouvez associer d'autres ID de client, état d'authentification et type de hachage (SHA -256) à chaque visiteur. Si vous ne fournissez aucun type de hachage, il est considéré comme sans hachage.

La `setCustomerIDs` méthode accepte plusieurs ID de client pour un même visiteur. Vous pouvez ainsi identifier ou cibler un utilisateur sur différents appareils. Vous pouvez par exemple télécharger ces ID en tant qu’[attributs du client](https://docs.adobe.com/content/help/en/core-services/interface/customer-attributes/attributes.html) vers Experience Cloud et accéder à ces données à partir de différentes solutions.

Customer IDs, authenticated states and hash type *are not* stored in a cookie to be used later. Instead, Customer IDs, authenticated states and hash type should be stored in an instance variable, to be retrieved using [`getCustomerIDs`](/help/library/get-set/getcustomerids.md), as shown below:

```
> visitor.getCustomerIDs();
< {email: {…}}
    email: {id: "a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097", authState: 1, hashType: "SHA-256"}
    __proto__: Object
```

<br> 

Using the `setCustomerIDs` method results in a call to the Experience Cloud ID Service, to `dpm.demdex.net`, with the addition of the `d_cid_ic` query parameter, which contains the hashed customer ID. Un exemple d'appel pourrait ressembler à celui-ci. Des sauts de ligne ont été ajoutés pour plus de clarté.

```
http://dpm.demdex.net/id?d_visid_ver=4.4.0&d_fieldgroup=AAM&d_rtbd=json&d_ver=2&
d_orgid=12A3F3F459CE0AD80A495CBE%40AdobeOrg&d_nsid=0&d_mid=12349850857640731290890207735189050123&
d_blob=6G1ynYcLPuiQxYZrsz_pkqfLG9yMXBpb2zX5dvJdYQJzPXImdj0y&
d_cid_ic=email%a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097%011&
ts=1563299964843
```

<br> 

See the table below for a description of the `d_cid_ic` parameter and authentication state.

| Paramètre | Description |
|------------|----------|
| `d_cid_ic` | Transmet le code d'intégration, l'ID unique - ID (DPUUID) et un ID d'état authentifié au service d'ID. Separate the Integration Code and DPUUID with the non-printing control character, <code>%01</code>: <br> Example: <code>d_cid_ic=Integration_code%01DPUUID%01Authentication_state</code> <br> <b>État d’authentification</b> <br> Il s'agit d'un ID facultatif dans le paramètre d_ cid_ ic. Expressed as an integer, it identifies users according to their authentication status as shown below: <br> <ul><li>0 (Inconnu ou jamais authentifié)</li><li>1 (actuellement authentifié pour cette instance/contexte/application/application)</li><li>2 (Déconnecté)</li></ul> <br>Exemples :<br> <ul><li>Inconnu : ...d_cid=123%01456%01<b>0</b></li><li>Authentifié : ...d_cid=123%01456%01<b>1</b></li><li>Déconnecté : ...d_cid=123%01456%01<b>2</b></li></ul> |

## Add an Action in Adobe Experience Platform Launch {#add-action-launch}

Launch Platform Launch est la nouvelle génération de fonctionnalités de gestion des balises d'Adobe. Read more about Launch in the [Launch product documentation](https://docs.adobe.com/content/help/en/launch/using/overview.html).

To add an action in Launch, read the [rules documentation](https://docs.adobe.com/help/en/launch/using/reference/manage-resources/rules.html) in Adobe Launch and see the screen capture below:

![](/help/reference/assets/hashing-support.png)

<br> 

Après avoir confirmé votre configuration, Launch place les données dans un objet, comme ci-dessous :

```
{
    integration_code: {
        id: "value",
        authState: auth_state,
        hashType: "hash_algorithm"
    }
}
```

Voici un exemple de code :

```
// Set single customer ID with hash type
setCustomerIDs(Ingeration code: {
    id: "string_value",
    authState: auth_state,
    hashType: "hash_algorithm"
});
```

Similarly to the `setCustomerIDs` method described in the first section, this results in a call to the Experience Cloud ID Service, with the addition of the `d_cid_ic` query parameter.