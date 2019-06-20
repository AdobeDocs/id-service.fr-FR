---
description: Ces instructions concernent les clients Target qui souhaitent utiliser le service Experience Cloud ID et qui n'utilisent pas la gestion dynamique des balises (DTM). Cependant, nous vous recommandons vivement d’utiliser DTM pour mettre en œuvre le service d’ID. DTM facilite le workflow de mise en œuvre et assure automatiquement le placement et le séquencement adéquats du code.
keywords: Service d’identification
seo-description: Ces instructions concernent les clients Target qui souhaitent utiliser le service Experience Cloud ID et qui n'utilisent pas la gestion dynamique des balises (DTM). Cependant, nous vous recommandons vivement d’utiliser DTM pour mettre en œuvre le service d’ID. DTM facilite le workflow de mise en œuvre et assure automatiquement le placement et le séquencement adéquats du code.
seo-title: Mise en œuvre du service Experience Cloud ID pour Target
title: Mise en œuvre du service Experience Cloud ID pour Target
uuid: cb 3581 fa -4 c 4 b -43 aa-bb 8 e -8 db 85 a 6 a 1 ef 2
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Mise en œuvre du service Experience Cloud ID pour Target{#implement-the-experience-cloud-id-service-for-target}

Ces instructions concernent les clients Target qui souhaitent utiliser le service Experience Cloud ID et qui n&#39;utilisent pas la gestion dynamique des balises (DTM). Cependant, nous vous recommandons vivement d’utiliser DTM pour mettre en œuvre le service d’ID. DTM facilite le workflow de mise en œuvre et assure automatiquement le placement et le séquencement adéquats du code.

>[!IMPORTANT]
>
>* [Lisez les conditions requises](../reference/requirements.md) avant de commencer.
>* Configurez ce code et testez-le dans un environnement de développement avant de le mettre en œuvre en production.
>



## Step 1: Get the ID Service code {#section-b32ba0548aa546a79dd38be59832a53e}

The [!DNL ID Service] requires the `VisitorAPI.js` code library. Pour obtenir ce code, contactez le [service à la clientèle](https://helpx.adobe.com/marketing-cloud/contact-support.html).

## Step 2: Add the Visitor.getInstance function to the ID Service code {#section-287ef2958e9f43858fe9d630ae519e22}

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

## Step 3: Add your Experience Cloud Organization ID to Visitor.getInstance {#section-522b1877be9243c39b222859b821f0ce}

In the `Visitor.getInstance` function, replace `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` with your [!DNL Experience Cloud] organization ID. Si vous ne connaissez pas votre ID d’organisation, vous pouvez le trouver dans la page d’administration [!DNL Experience Cloud]. Voir également [Administration – Services principaux](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html). La fonction modifiée peut ressembler à l’exemple ci-après.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*Ne* modifiez pas la casse des caractères de votre ID d&#39;organisation. L’ID est sensible à la casse et doit être utilisé tel quel.

## Step 4: Add Visitor API code to the page {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

Deploy the `VisitorAPI.js` file to your site in the `<head>` tags before the reference to the `mbox.js` file. The [!DNL Experience Cloud] ID service must execute before the first [!DNL Target] network call is generated. Placez ce code en production après les tests et la vérification.

## Step 5: Test and deploy ID Service code {#section-e81ee439bb8a4c2abea43d76f3112e9c}

Vous pouvez tester et déployer les éléments suivants.

**Tester et vérifier**

Pour tester la mise en œuvre du service d’ID :

* Recherchez le cookie AMCV dans le domaine où est hébergée votre page.
* Verify `mboxMCGVID` appears in your [!DNL Target] request and that it contains the [!DNL Experience Cloud] ID (MID).

See [Cookies and the Experience Cloud ID Service](../introduction/cookies.md) for information about the AMCV cookie and the MID.

**Déploiement**

Déployez votre code une fois qu’il a réussi les tests.
