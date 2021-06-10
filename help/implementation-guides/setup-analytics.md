---
description: Ces instructions concernent les clients d’Analytics qui souhaitent utiliser le service Experience Cloud Identity et n’utilisent pas Dynamic Tag Management (DTM). Cependant, il est vivement recommandé d’utiliser DTM pour implémenter le service d’ID. DTM simplifie le processus d’implémentation et assure automatiquement un placement et un séquencement du code adéquats.
keywords: Service d’ID
title: Mise en œuvre du service Experience Cloud Identity pour Analytics
exl-id: c0271e49-32e5-49ee-bb11-548751ccafad
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '1025'
ht-degree: 98%

---

# Mise en œuvre du service Experience Cloud Identity pour Analytics {#implement-the-experience-cloud-id-service-for-analytics}

Ces instructions concernent les clients d’Analytics qui souhaitent utiliser le service Experience Cloud Identity et n’utilisent pas Dynamic Tag Management (DTM). Cependant, il est vivement recommandé d’utiliser DTM pour implémenter le service d’ID. DTM simplifie le processus d’implémentation et assure automatiquement un placement et un séquencement du code adéquats.

>[!IMPORTANT]
>
>* [Lisez les conditions requises](../reference/requirements.md) avant de commencer.
>* Configurez ce code et testez-le dans un environnement de développement avant de le mettre en œuvre en production.


Pour mettre en œuvre le service d’ID pour Adobe Analytics, procédez comme suit :

1. [Téléchargez le code du service d’ID](../implementation-guides/setup-analytics.md#section-ead9403a6b7e45b887f9ac959ef89f7f)
1. [Ajoutez la fonction Visitor.getInstance au code du service d’ID](../implementation-guides/setup-analytics.md#section-6053a6b7c16c466a9f9fdbf9cb9db3df)
1. [Ajoutez l’ID d’organisation Experience Cloud à Visitor.getInstance](../implementation-guides/setup-analytics.md#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e)
1. [Ajoutez des serveurs de suivi à Visitor.getInstance](../implementation-guides/setup-analytics.md#section-70ec9ebff47940d8ab520be5ec4728c5)
1. [Mettez à jour le fichier AppMeasurement.js ou s_code.js](../implementation-guides/setup-analytics.md#section-b53113aea1bd4de896e0e4e9a7edee19)
1. [Ajoutez du code de l’API visiteur à la page](../implementation-guides/setup-analytics.md#section-d46d6aa324c842f2931d901e38d6db1d)
1. [Configurez une période de grâce (facultatif)](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3)
1. [Testez et déployez le code du service d’ID](../implementation-guides/setup-analytics.md#section-e9c1764ac21a4ec5be1ff338c0e2e01b)

## Étape 1 : Téléchargement du code du service d’ID {#section-ead9403a6b7e45b887f9ac959ef89f7f}

Le [!UICONTROL service d’ID] requiert la bibliothèque de code `VisitorAPI.js`. Pour télécharger cette bibliothèque de code :

1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Gestionnaire de code]**.
1. Dans [!UICONTROL Gestionnaire de code], cliquez sur **[!UICONTROL JavaScript (nouveau)]** ou **[!UICONTROL JavaScript (hérité)]**.

   Les bibliothèques de code compressées sont alors téléchargées.

1. Décompressez le fichier de code, puis ouvrez le `VisitorAPI.js` fichier.

## Étape 2 : Ajout de la fonction Visitor.getInstance au code du service d’ID {#section-6053a6b7c16c466a9f9fdbf9cb9db3df}

>[!IMPORTANT]
>
>* Les versions précédentes de l’API du service d’ID plaçaient cette fonction à un autre emplacement et nécessitaient une syntaxe différente. Si vous effectuez une migration à partir d’une version antérieure à la [version 1.4](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572), notez le nouvel emplacement et la nouvelle syntaxe documentés ici.
>* Le code en MAJUSCULES est un espace réservé pour des valeurs réelles. Remplacez ce texte par votre ID d’organisation, l’URL du serveur de suivi ou toute autre valeur nommée.


**Partie 1 : Copiez la fonction Visiteur.getInstance ci-dessous**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

**Partie 2 : Ajoutez le code de la fonction au fichier VisitorAPI.js**

Placez la `Visitor.getInstance` fonction à la fin du fichier, après le bloc de code. Le fichier modifié doit ressembler à celui-ci :

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library

var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

## Étape 3 : Ajout de l’ID d’organisation Experience Cloud à Visitor.getInstance {#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e}

Dans la `Visitor.getInstance` fonction, remplacez `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` par [!DNL Experience Cloud] l’ID d’organisation. Si vous ne connaissez pas votre ID d’organisation, vous pouvez le trouver dans la page [!DNL Experience Cloud] d’administration. Voir aussi [Administration - Services principaux](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html?lang=fr). La fonction modifiée peut ressembler à l’exemple ci-après.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*Ne modifiez pas* la casse des caractères de l’ID d’organisation. L’ID est sensible à la casse et doit être utilisé tel quel.

## Étape 4 : Ajout des serveurs de suivi à Visitor.getInstance {#section-70ec9ebff47940d8ab520be5ec4728c5}

Les serveurs de suivi sont utilisés pour la [!DNL Analytics] collecte des données.

**Partie 1 : Recherchez les URL de serveur de suivi**

Dans le fichier `s_code.js` ou `AppMeasurement.js`, recherchez les URL de serveur de suivi. Les URL doivent être spécifiées par les variables suivantes :

* `s.trackingServer`
* `s.trackingServerSecure`

**Partie 2 : Définissez les variables de serveur de suivi**

Pour déterminer les variables de serveur de suivi à utiliser :

1. Répondez aux questions présentées dans le tableau ci-après. Utilisez les variables qui correspondent à vos réponses.
1. Remplacez les espaces réservés au serveur de suivi par les URL du serveur de suivi.
1. Supprimez les variables de serveur de suivi et de [!DNL Experience Cloud] serveur inutilisées du code.

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>Lorsqu’elles sont utilisées, faites correspondre les URL du serveur [!DNL Experience Cloud] aux URL du serveur de suivi correspondant de la façon suivante :
>
>* [!DNL Experience Cloud] URL du serveur = URL du serveur de suivi
>* [!DNL Experience Cloud] URL du serveur sécurisé = URL du serveur sécurisé de suivi


Si vous ne savez pas comment trouver votre serveur de suivi, consultez la [FAQ](../faq-intro/faq.md) et la [Collecte correcte des variables trackingServer et trackingServerSecure](https://helpx.adobe.com/fr/analytics/kb/determining-data-center.html#).

## Étape 5 : Mise à jour du fichier AppMeasurement.js ou s_code.js {#section-b53113aea1bd4de896e0e4e9a7edee19}

Ajoutez la fonction suivante au fichier `AppMeasurement.js` ou `s_code.js` :

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

Placez le code dans la section qui contient des configurations telles que `linkInternalFilters`, `charSet`, `trackDownloads`, etc.

***(Étape facultative mais recommandée)* Créez une prop personnalisée.**

Définissez une prop personnalisée dans le fichier `AppMeasurement.js` ou `s_code.js` pour mesurer la couverture. Ajoutez la prop personnalisée suivante à la `doPlugins`fonction du fichier `AppMeasurement.js` ou `s_code.js` :

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## Étape 6 : Ajout du code de l’API visiteur à la page {#section-d46d6aa324c842f2931d901e38d6db1d}

Placez le fichier `VisitorAPI.js` à l’intérieur des balises `<head>` sur chaque page. Lorsque vous placez le `VisitorAPI.js` fichier sur votre page :

* Insérez-le au début de la `<head>` section afin qu’il s’affiche avant les balises d’autres solutions.
* Il doit s’exécuter avant AppMeasurement et le code d’autres [!DNL Experience Cloud] solutions.

Placez ce code en production après les tests et la vérification.

## Étape 7 : (facultative) Configuration d’une période de grâce {#section-7bbb2f72c26e4abeb8881e18366797a3}

Si l’un de ces cas d’utilisation s’applique à votre situation, demandez à [l’Assistance clientèle](https://helpx.adobe.com/fr/marketing-cloud/contact-support.html) de mettre en place une [période de grâce](../reference/analytics-reference/grace-period.md) temporaire. Les périodes de grâce peuvent durer jusqu’à 180 jours. Vous pouvez renouveler une période de grâce si nécessaire.

**Mise en œuvre partielle**

Vous avez besoin d’une période de grâce si certaines pages utilisent le service d’ID et d’autres pas et si elles signalent des informations dans la même suite de [!DNL Analytics] rapports. Cela est courant si vous disposez d’une suite de rapports globale qui crée des rapports entre domaines.

Arrêtez la période de grâce après le déploiement du service d’ID sur toutes les pages Web qui génèrent des rapports dans la même suite de rapports.

**Conditions requises pour le cookie s_vi**

Vous avez besoin d’une période de grâce si vous souhaitez que les nouveaux visiteurs disposent d’un cookie s_vi après la migration vers le service d’ID. Cela est courant si votre implémentation lit le cookie s_vi et le stocke dans une variable.

Arrêtez la période de grâce une fois que votre implémentation peut capturer le MID au lieu de lire le cookie s_vi.

Voir [Cookies et service Experience Cloud Identity](../introduction/cookies.md).

Vous avez besoin d’une période de grâce si vous envoyez les données à un système interne à partir d’un flux de données de parcours de navigation et si ce processus utilise les colonnes `visid_high` et `visid_low`.

Interrompez la période de grâce une fois que le processus d’ingestion des données peut utiliser les colonnes `post_visid_high` et `post_visid_low`.

Voir [Référence des colonnes de données du parcours de navigation](https://experienceleague.adobe.com/docs/analytics/export/analytics-data-feed/data-feed-overview.html).

**Ingestion des données du parcours de navigation**

## Étape 8 : Test et déploiement du code du service d’ID {#section-e9c1764ac21a4ec5be1ff338c0e2e01b}

Vous pouvez tester et déployer les éléments comme suit.

**Tests et vérification**

Pour tester la mise en œuvre du service d’ID, recherchez les éléments suivants :

* Le [cookie AMCV](../introduction/cookies.md) dans le domaine où est hébergée votre page ;
* La valeur du MID dans la demande d’image [!DNL Analytics] à l’aide de l’[outil de débogage Adobe](https://experienceleague.adobe.com/docs/analytics/implementation/validate/debugger.html).

Voir [Test et vérification du service Experience Cloud Identity](../implementation-guides/test-verify.md).

**Déploiement du code**

Déployez votre code une fois qu’il a réussi le test.

Si vous avez activé une période de grâce à l’[étape 7](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3) :

* Vérifiez que l’ID [!DNL Analytics] (AID) et le MID figurent dans la demande d’image.
* Souvenez-vous de désactiver la période de grâce lorsque les critères d’interruption sont remplis.
