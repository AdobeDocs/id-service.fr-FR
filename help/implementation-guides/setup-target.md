---
description: Ces instructions s’adressent aux clients Target qui souhaitent utiliser le service d’identification des visiteurs et n’utilisent pas de balises. Cependant, nous vous recommandons vivement d’utiliser les balises pour implémenter le service d’identification des visiteurs. Les balises optimisent le workflow d’implémentation et assurent automatiquement le placement et le séquencement adéquats du code.
keywords: Service d’identification des visiteurs
title: Mise en œuvre du service d’identification des visiteurs Adobe pour Target
exl-id: 7a387e98-c8fc-4904-942a-be5e527eada2
TQID: https://experienceleague.adobe.com/1994Y39yotvpJkcYazVnG0w-GupHiZZipnLWSTbgle8
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 430
ht-degree: 47%

---

# Mise en œuvre du service d’identification des visiteurs Adobe pour Target{#implement-the-experience-cloud-id-service-for-target}

Ces instructions s’adressent aux clients Target qui souhaitent utiliser le service d’identification des visiteurs et n’utilisent pas [&#x200B; balises](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=fr). Cependant, nous vous recommandons vivement d’utiliser les balises pour implémenter le service d’identification des visiteurs. Les balises optimisent le workflow d’implémentation et assurent automatiquement le placement et le séquencement adéquats du code.

>[!IMPORTANT]
>
>* [Lisez les conditions requises](../reference/requirements.md) avant de commencer.
>* Configurez ce code et testez-le dans un environnement de développement avant de le mettre en œuvre en production.

## Étape 1 : obtenir le code du service d’identification des visiteurs {#section-b32ba0548aa546a79dd38be59832a53e}

Le service d’identification des visiteurs nécessite la bibliothèque de code `VisitorAPI.js`. Contactez l’[assistance clientèle](https://helpx.adobe.com/fr/marketing-cloud/contact-support.html) pour obtenir ce code.

## Étape 2 : ajouter la fonction Visitor.getInstance au code du service d’identification des visiteurs {#section-287ef2958e9f43858fe9d630ae519e22}

**Partie 1 : Copiez la fonction Visiteur.getInstance ci-dessous**

```js
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE"); 
```

**Partie 2 : ajoutez le code de fonction au fichier `VisitorAPI.js`**

Placez la `Visitor.getInstance` fonction à la fin du fichier, après le bloc de code. Le fichier modifié doit ressembler à celui-ci :

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library 
 
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE");
```

## Étape 3 : ajouter votre ID d’organisation IMS à Visitor.getInstance {#section-522b1877be9243c39b222859b821f0ce}

Dans la fonction `Visitor.getInstance` , remplacez `INSERT-IMS-ORG-ID-HERE` par votre ID d’organisation IMS. Si vous ne connaissez pas votre identifiant de l’organisation IMS, vous pouvez le trouver sur la page d’administration de l’entreprise CX. Voir aussi [Administration - Services principaux](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html?lang=fr). La fonction modifiée peut ressembler à l’exemple ci-après.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*Ne modifiez pas* la casse des caractères de votre identifiant de l’organisation IMS. L’ID est sensible à la casse et doit être utilisé tel quel.

## Étape 4 : ajouter le code de l’API visiteur à la page {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

Déployez le fichier `VisitorAPI.js` sur votre site dans les balises `<head>` situées avant la référence au fichier `mbox.js`. Le service d’identification des visiteurs doit s’exécuter avant la génération du premier appel réseau Target. Placez ce code en production après les tests et la vérification.

## Étape 5 : tester et déployer le code du service d’identification des visiteurs {#section-e81ee439bb8a4c2abea43d76f3112e9c}

Vous pouvez tester et déployer les éléments comme suit.

**Tests et vérification**

Pour tester la mise en œuvre du service d’identification des visiteurs :

* Recherchez le cookie AMCV dans le domaine où est hébergée votre page.
* Vérifiez `mboxMCGVID` apparaît dans votre requête Target et qu’elle contient l’ECID.

Voir [&#x200B; Cookies et service d’identification des visiteurs &#x200B;](../introduction/cookies.md) pour plus d’informations sur le cookie AMCV et le MID.

**Déploiement**

Déployez votre code une fois qu’il a réussi le test.

