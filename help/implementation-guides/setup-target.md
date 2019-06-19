---
description: Ces instructions concernent les clients Target qui souhaitent utiliser le service d'identité Experience Platform et qui n'utilisent pas la gestion dynamique des balises (DTM). Cependant, nous vous recommandons vivement d’utiliser DTM pour mettre en œuvre le service d’ID. DTM facilite le workflow de mise en œuvre et assure automatiquement le placement et le séquencement adéquats du code.
keywords: Service d’identification
seo-description: Ces instructions concernent les clients Target qui souhaitent utiliser le service d'identité Experience Platform et qui n'utilisent pas la gestion dynamique des balises (DTM). Cependant, nous vous recommandons vivement d’utiliser DTM pour mettre en œuvre le service d’ID. DTM facilite le workflow de mise en œuvre et assure automatiquement le placement et le séquencement adéquats du code.
seo-title: Mise en œuvre du service d'identité d'Experience Platform pour Target
title: Mise en œuvre du service d'identité d'Experience Platform pour Target
uuid: cb 3581 fa -4 c 4 b -43 aa-bb 8 e -8 db 85 a 6 a 1 ef 2
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Mise en œuvre du service d&#39;identité d&#39;Experience Platform pour Target{#implement-the-experience-cloud-id-service-for-target}

Ces instructions concernent les clients Target qui souhaitent utiliser le service d&#39;identité Experience Platform et qui n&#39;utilisent pas la gestion dynamique des balises (DTM). Cependant, nous vous recommandons vivement d’utiliser DTM pour mettre en œuvre le service d’ID. DTM facilite le workflow de mise en œuvre et assure automatiquement le placement et le séquencement adéquats du code.

>[!IMPORTANT]
>
>* [Lisez les conditions requises](../reference/requirements.md) avant de commencer.
>* Configurez ce code et testez-le dans un environnement de développement avant de le mettre en œuvre en production.
>



## Étape 1 : Obtention du code du service d&#39;ID {#section-b32ba0548aa546a79dd38be59832a53e}

La [!DNL ID Service] bibliothèque `VisitorAPI.js` de code est requise. Pour obtenir ce code, contactez le [service à la clientèle](https://helpx.adobe.com/marketing-cloud/contact-support.html).

## Étape 2 : Ajout de la fonction Visitor. getinstance au code du service d&#39;ID {#section-287ef2958e9f43858fe9d630ae519e22}

**Partie 1 : Copiez la fonction Visitor.getInstance ci-dessous**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE"); 
```

**Partie 2 : Ajoutez le code de la fonction au fichier VisitorAPI.js**

Placez la fonction `Visitor.getInstance` à la fin du fichier, après le bloc de code. Le fichier modifié doit ressembler à celui-ci :

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library 
 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");
```

## Étape 3 : Ajout de votre ID d&#39;organisation Experience Cloud à Visitor. getinstance {#section-522b1877be9243c39b222859b821f0ce}

Dans `Visitor.getInstance` la fonction, remplacez `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` par l&#39;ID [!DNL Experience Cloud] d&#39;organisation. Si vous ne connaissez pas votre ID d’organisation, vous pouvez le trouver dans la page d’administration [!DNL Experience Cloud]. Voir également [Administration – Services principaux](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html). La fonction modifiée peut ressembler à l’exemple ci-après.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*Ne* modifiez pas la casse des caractères de votre ID d&#39;organisation. L’ID est sensible à la casse et doit être utilisé tel quel.

## Étape 4 : Ajout du code de l&#39;API visiteur à la page {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

Déployez `VisitorAPI.js` le fichier sur votre site dans `<head>` les balises avant la référence au `mbox.js` fichier. Le service [!DNL Experience Cloud] d&#39;ID doit s&#39;exécuter avant la génération du premier [!DNL Target] appel réseau. Placez ce code en production après les tests et la vérification.

## Étape 5 : Test et déploiement du code du service d&#39;ID {#section-e81ee439bb8a4c2abea43d76f3112e9c}

Vous pouvez tester et déployer les éléments suivants.

**Tester et vérifier**

Pour tester la mise en œuvre du service d’ID :

* Recherchez le cookie AMCV dans le domaine où est hébergée votre page.
* Vérifier `mboxMCGVID` s&#39;affiche dans [!DNL Target] votre requête et contient l&#39; [!DNL Experience Cloud] identifiant (MID).

Voir [Cookies et service d&#39;identité d&#39;Experience Platform](../introduction/cookies.md) pour en savoir plus sur le cookie AMCV et le MID.

**Déploiement**

Déployez votre code une fois qu’il a réussi les tests.
