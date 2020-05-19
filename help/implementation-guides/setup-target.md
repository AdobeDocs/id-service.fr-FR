---
description: Ces instructions concernent les clients de Target qui souhaitent utiliser le service Experience Cloud Identity et n’utilisent pas Dynamic Tag Management (DTM). Cependant, il est vivement recommandé d’utiliser DTM pour implémenter le service d’ID. DTM simplifie le processus d’implémentation et assure automatiquement un placement et un séquencement du code adéquats.
keywords: ID Service
seo-description: Ces instructions concernent les clients de Target qui souhaitent utiliser le service Experience Cloud Identity et n’utilisent pas Dynamic Tag Management (DTM). Cependant, il est vivement recommandé d’utiliser DTM pour implémenter le service d’ID. DTM simplifie le processus d’implémentation et assure automatiquement un placement et un séquencement du code adéquats.
seo-title: Mise en œuvre du service Experience Cloud Identity pour Target
title: Mise en œuvre du service Experience Cloud Identity pour Target
uuid: cb3581fa-4c4b-43aa-bb8e-8db85a6a1ef2
translation-type: ht
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: ht
source-wordcount: '459'
ht-degree: 100%

---


# Mise en œuvre du service Experience Cloud Identity pour Target {#implement-the-experience-cloud-id-service-for-target}

Ces instructions concernent les clients de Target qui souhaitent utiliser le service Experience Cloud Identity et n’utilisent pas Dynamic Tag Management (DTM). Cependant, il est vivement recommandé d’utiliser DTM pour implémenter le service d’ID. DTM simplifie le processus d’implémentation et assure automatiquement un placement et un séquencement du code adéquats.

>[!IMPORTANT]
>
>* [Lisez les conditions requises](../reference/requirements.md) avant de commencer.
>* Configurez ce code et testez-le dans un environnement de développement avant de le mettre en œuvre en production.
>



## Étape 1 : Obtention du code du service d’ID {#section-b32ba0548aa546a79dd38be59832a53e}

Le [!UICONTROL service d’ID] requiert la bibliothèque de code `VisitorAPI.js`. Contactez l’[assistance clientèle](https://helpx.adobe.com/fr/marketing-cloud/contact-support.html) pour obtenir ce code.

## Étape 2 : Ajout de la fonction Visitor.getInstance au code du service d’ID {#section-287ef2958e9f43858fe9d630ae519e22}

**Partie 1 : Copiez la fonction Visiteur.getInstance ci-dessous**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE"); 
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
 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");
```

## Étape 3 : Ajout de l’ID d’organisation Experience Cloud à Visitor.getInstance {#section-522b1877be9243c39b222859b821f0ce}

Dans la `Visitor.getInstance` fonction, remplacez `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` par [!DNL Experience Cloud] l’ID d’organisation. Si vous ne connaissez pas votre ID d’organisation, vous pouvez le trouver dans la page [!DNL Experience Cloud] d’administration. Voir aussi [Administration - Services principaux](https://docs.adobe.com/content/help/fr-FR/core-services/interface/manage-users-and-products/admin-getting-started.html). La fonction modifiée peut ressembler à l’exemple ci-après.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*Ne modifiez pas* la casse des caractères de l’ID d’organisation. L’ID est sensible à la casse et doit être utilisé tel quel.

## Étape 4 : Ajout du code de l’API visiteur à la page {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

Déployez le fichier `VisitorAPI.js` sur votre site dans les balises `<head>` situées avant la référence au fichier `mbox.js`. Le service [!DNL Experience Cloud] ID doit s’exécuter avant la génération du premier appel réseau [!DNL Target]. Placez ce code en production après les tests et la vérification.

## Étape 5 : Test et déploiement du code du service d’ID {#section-e81ee439bb8a4c2abea43d76f3112e9c}

Vous pouvez tester et déployer les éléments comme suit.

**Tests et vérification**

Pour tester votre mise en œuvre du service d’ID :

* Recherchez le cookie AMCV dans le domaine où est hébergée votre page.
* Vérifiez que `mboxMCGVID` apparaît dans la requête [!DNL Target] et qu’il contient l’[!DNL Experience Cloud] ID (MID).

Voir [Cookies et service Experience Cloud Identity](../introduction/cookies.md) pour obtenir des informations sur le cookie AMCV et le MID.

**Déploiement**

Déployez votre code une fois qu’il a réussi le test.
