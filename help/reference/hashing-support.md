---
description: Le service Experience Cloud ID (ECID) prend en charge l’algorithme de hachage SHA-256 qui vous permet de transmettre des ID de client ou des adresses électroniques, et transmet des identifiants hachés. Il s’agit d’une méthode JavaScript facultative pour envoyer des identifiants hachés à Experience Cloud. Vous pouvez continuer à utiliser vos propres méthodes de hachage avant d’envoyer les ID de client.
keywords: Service d’identification
seo-description: Le service Experience Cloud ID (ECID) prend en charge l’algorithme de hachage SHA-256 qui vous permet de transmettre des ID de client ou des adresses électroniques, et transmet des identifiants hachés. Il s’agit d’une méthode JavaScript facultative pour envoyer des identifiants hachés à Experience Cloud. Vous pouvez continuer à utiliser vos propres méthodes de hachage avant d’envoyer les ID de client.
seo-title: Prise en charge du hachage SHA-256 pour setCustomerIDs
title: Prise en charge du hachage SHA-256 pour setCustomerIDs
translation-type: tm+mt
source-git-commit: ac1131be75fd04b51cd1d646086e1802a43afb18

---


# Prise en charge du hachage SHA-256 pour `setCustomerIDs` {#hashing-support}

Le service Experience Cloud ID (ECID) prend en charge l’algorithme de hachage SHA-256 qui vous permet de transmettre des ID de client ou des adresses électroniques, et transmet des identifiants hachés. Il s’agit d’une méthode JavaScript facultative pour envoyer des identifiants hachés à Experience Cloud. Vous pouvez continuer à utiliser vos propres méthodes de hachage avant d’envoyer les ID de client.
Il existe deux façons de mettre en œuvre la prise en charge du hachage avec setCustomerIDs, comme décrit dans les sections ci-dessous :

* [Utiliser la méthode setCustomerIDs dans ECID](/help/reference/hashing-support.md#use-setcustomerids-method)
* [Ajout d’une Action dans Adobe Experience Platform Launch](/help/reference/hashing-support.md#add-action-launch)

## Utilisation de la méthode `setCustomerIDs` dans ECID {#use-setcustomerids-method}

La première méthode utilise la méthode [`setCustomerIDs`](/help/library/get-set/setcustomerids.md) (`customerIDs<object>`, `hashType<string>`).

Avant de procéder au hachage, la bibliothèque ECID effectue une normalisation des données sur les customerIDs. Ce processus supprime les espaces des customerIDs à chaque extrémité et convertit tous les caractères en minuscules. Par exemple, l’adresse électronique «  ecid@adobe.com  » devient «&nbsp;ecid@adobe.com&nbsp;»

Vous trouverez ci-dessous un exemple de code illustrant comment définir un identifiant client unique (l’adresse électronique mentionnée ci-dessus) avec un hachage SHA-256.

```
// Set single customerID with SHA-256 hashing
visitor.setCustomerIDs({email: {id: "ecid@adobe.com", authState: 1}}, "SHA-256");
```

<br> 

Avec l’identifiant visiteur Experience Cloud, vous pouvez associer d’autres ID de client, un état d’authentification et un type de hachage (SHA-256) à chaque visiteur. Si vous ne spécifiez aucun type de hachage, ce dernier n’aura pas lieu.

La `setCustomerIDs` méthode accepte plusieurs ID de client pour un même visiteur. Vous pouvez ainsi identifier ou cibler un utilisateur sur différents appareils. Vous pouvez par exemple télécharger ces ID en tant qu’[attributs du client](https://docs.adobe.com/content/help/en/core-services/interface/customer-attributes/attributes.html) vers Experience Cloud et accéder à ces données à partir de différentes solutions.

Les ID de client, les états authentifiés et le type de hachage *ne sont pas* stockés dans un cookie à utiliser ultérieurement. Au lieu de cela, les ID de client, les états authentifiés et le type de hachage doivent être stockés dans une variable d’instance, qui peut être récupérée en utilisant [`getCustomerIDs`](/help/library/get-set/getcustomerids.md), comme illustré ci-dessous :

```
> visitor.getCustomerIDs();
< {email: {…}}
    email: {id: "a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097", authState: 1, hashType: "SHA-256"}
    __proto__: Object
```

<br> 

L’utilisation de la méthode `setCustomerIDs` génère un appel au service Experience Cloud ID, à `dpm.demdex.net`, auquel est ajouté le paramètre de requête `d_cid_ic` qui contient l’ID de client haché. Un appel type pourrait ressembler à ce qui suit. Des sauts de ligne ont été ajoutés pour plus de clarté.

```
http://dpm.demdex.net/id?d_visid_ver=4.4.0&d_fieldgroup=AAM&d_rtbd=json&d_ver=2&
d_orgid=12A3F3F459CE0AD80A495CBE%40AdobeOrg&d_nsid=0&d_mid=12349850857640731290890207735189050123&
d_blob=6G1ynYcLPuiQxYZrsz_pkqfLG9yMXBpb2zX5dvJdYQJzPXImdj0y&
d_cid_ic=email%a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097%011&
ts=1563299964843
```

<br> 

Reportez-vous au tableau ci-dessous pour obtenir une description du paramètre `d_cid_ic` et de l’état d’authentification.

| Paramètre | Description |
|------------|----------|
| `d_cid_ic` | Transmet le code d’intégration, l’ID de l’utilisateur unique (DPUUID) et un ID d’état authentifié au service d’ID. Séparez le code d’intégration et le DPUUID par le caractère de contrôle non imprimable <code>%01</code> : <br> Exemple : <code>d_cid_ic=Integration_code%01DPUUID%01Authentication_state</code> <br> <b>État d’authentification</b> <br> Il s’agit d’un ID facultatif dans le paramètre d_cid_ic. Exprimé sous la forme d’un entier, il identifie les utilisateurs en fonction de leur état d’authentification comme indiqué ci-dessous : <br> <ul><li>0 (inconnu ou jamais authentifié)</li><li>1 (actuellement authentifié pour cette instance, cette page ou ce contexte d’application)</li><li>2 (déconnecté)</li></ul> <br>Exemples :<br> <ul><li>Inconnu : ...d_cid=123%01456%01<b>0</b></li><li>Authentifié : ...d_cid=123%01456%01<b>1</b></li><li>Déconnecté : ...d_cid=123%01456%01<b>2</b></li></ul> |

## Ajout d’une Action dans Adobe Experience Platform Launch {#add-action-launch}

Experience Platform Launch représente la nouvelle génération des fonctionnalités de gestion des balises d’Adobe. Read more about Launch in the [Launch product documentation](https://docs.adobe.com/content/help/en/launch/using/overview.html).

To add an action in Launch, read the [rules documentation](https://docs.adobe.com/help/en/launch/using/reference/manage-resources/rules.html) in Adobe Launch and see the screen capture below:

![](/help/reference/assets/hashing-support.png)

<br> 

Après avoir confirmé votre configuration, Launch place les données dans un objet, comme ci-dessous :

```
{
    integration_code: {
        id: "value",
        authState: auth_state,
        hashType: "hash_algorithm"
    }
}
```

Voici un exemple de code :

```
// Set single customer ID with hash type
setCustomerIDs(Ingeration code: {
    id: "string_value",
    authState: auth_state,
    hashType: "hash_algorithm"
});
```

Comme pour la méthode `setCustomerIDs` décrite dans la première section, il en découle un appel au service Experience Cloud ID, auquel est ajouté le paramètre de requête `d_cid_ic`.
