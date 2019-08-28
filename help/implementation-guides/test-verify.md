---
description: Les instructions, outils et procédures suivants vous aident à déterminer si le service d’ID fonctionne correctement. Les tests s’appliquent au service d’ID en général et pour différentes combinaisons de service d’ID et de solutions Experience Cloud.
keywords: Service d’identification
seo-description: Les instructions, outils et procédures suivants vous aident à déterminer si le service d’ID fonctionne correctement. Les tests s’appliquent au service d’ID en général et pour différentes combinaisons de service d’ID et de solutions Experience Cloud.
seo-title: Tester et vérifier le service d'identité Experience Cloud
title: Tester et vérifier le service d'identité Experience Cloud
uuid: 442de9c3-c265-4412-89bd-aeaa286ddad6
translation-type: tm+mt
source-git-commit: ef3169f8928f337d4f2d17922b44a7421d225e51

---


# Test and verify the Experience Cloud Identity Service{#test-and-verify-the-experience-cloud-id-service}

Les instructions, outils et procédures suivants vous aident à déterminer si le service d’ID fonctionne correctement. Les tests s’appliquent au service d’ID en général et pour différentes combinaisons de service d’ID et de solutions Experience Cloud.

## Avant de commencer {#section-b1e76ad552ed4eb793b6e521a55127d4}

Informations importantes à connaître avant de commencer à tester et à vérifier le service d’ID.

**Environnements du navigateur**

Lorsque vous testez dans une session normale du navigateur, effacez le cache du navigateur avant chaque test.

Vous pouvez également tester le service d’ID dans une session anonyme ou privée du navigateur. Dans une session anonyme, vous n’avez pas besoin d’effacer les cookies ou le cache du navigateur avant chaque test.

**Outils**

Le [débogueur Adobe](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html) et le [proxy HTTP Charles](https://www.charlesproxy.com/) peuvent vous aider à déterminer si le service d’ID a été configuré pour fonctionner correctement avec Analytics. Les informations de cette section se basent sur les résultats renvoyés par le débogueur Adobe et Charles. Cependant, sentez-vous libre d’utiliser l’outil ou le débogueur qui fonctionne le mieux pour vous.

## Test à l’aide du débogueur Adobe  {#section-861365abc24b498e925b3837ea81d469}

La mise en œuvre de votre service est correctement configurée lorsqu’un [!DNL Experience Cloud ID] (MID) s’affiche dans la réponse du [!DNL Adobe] débogueur . See [Cookies and the Experience Cloud Identity Service](../introduction/cookies.md) for more information about the MID.

To verify the status of the ID service with the [!DNL Adobe] [debugger](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html):

1. Effacez les cookies du navigateur ou ouvrez une session de navigation anonyme.
1. Chargez votre page de test qui contient le code du service d’ID.
1. Ouvrez le [!DNL Adobe] débogueur .
1. Vérifiez les résultats d’un MID.

## Comprendre les résultats du débogueur Adobe {#section-bd2caa6643d54d41a476d747b41e7e25}

Le MID est stocké dans une paire clé-valeur qui suit cette syntaxe : `MID= *`Experience Cloud ID`*`. Le débogueur affiche ces informations telles que montrées ci-dessous.

**Succès**

Le service d’ID a été correctement mis en œuvre si une réponse telle que celle-ci s’affiche :

```
mid=20265673158980419722735089753036633573
```

Si vous êtes client [!DNL Analytics], un [!DNL Analytics] ID (AID) peut s’afficher en plus du MID. Il se produit la chose suivante :

* Avec certains de vos visiteurs anciens/de longue date.
* Si une période de grâce est activée.

**Échec**

Contactez [le service à la clientèle](https://helpx.adobe.com/marketing-cloud/contact-support.html) si le débogueur :

* Ne renvoie pas un MID.
* Renvoie un message d’erreur qui indique que votre identifiant de partenaire n’a pas été attribué.

## Test à l’aide du proxy HTTP Charles {#section-d9e91f24984146b2b527fe059d7c9355}

Pour vérifier l’état du service d’ID avec Charles :

1. Effacez les cookies du navigateur ou ouvrez une session de navigation anonyme.
1. Démarrez Charles.
1. Chargez votre page de test qui contient le code du service d’ID.
1. Vérifiez les appels de demande et de réponse et les données décrites ci-dessous.

## Comprendre les résultats Charles {#section-c10c3dc0bb9945cbaffcf6fec7082fab}

Consultez cette section pour savoir où chercher et que chercher lorsque vous utilisez Charles pour surveiller les appels HTTP.

**Demandes de service d’ID réussies dans Charles**

Le code de votre service d’ID fonctionne correctement si la fonction `Visitor.getInstance` lance un appel JavaScript à `dpm.demdex.net`. Une demande réussie inclut votre [ID d’organisation](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26). L’ID d’organisation est transmis en tant que paire clé-valeur utilisant la syntaxe : `d_orgid= *`organization ID`*`. Recherchez les appels `dpm.demdex.net` et JavaScript dans l’onglet [!UICONTROL Structure]. Recherchez votre ID d’organisation dans l’onglet [!UICONTROL Demande].

![](assets/charles_request.png)

**Réponses du service d’ID réussies dans Charles**

Votre compte a été configuré correctement pour le service d’ID si la réponse des [serveurs de collecte des données](https://marketing.adobe.com/resources/help/en_US/aam/c_compcollect.html) (DCS) renvoie un MID. Le MID est renvoyé comme une paire clé-valeur qui suit cette syntaxe : `d_mid: *`visiteur Experience Cloud ID`*`. Recherchez le MID dans l’onglet [!UICONTROL Réponse] tel qu’affiché ci-dessous.

![](assets/charles_response_success.png)

**Échec des réponses du service d’ID dans Charles**

Votre compte n’a pas été configuré correctement si la réponse DCS ne contient pas le MID. Une réponse manquée renvoie un code et un message d’erreur dans l’onglet [!UICONTROL Réponse] tel qu’affiché ci-dessous. Contactez le service à la clientèle si ce message d’erreur s’affiche dans la réponse DCS.

![](assets/charles_response_unsuccessful.png)

Pour plus d’informations sur les codes d’erreur, voir [Codes, message et exemples d’erreur DCS](https://marketing.adobe.com/resources/help/en_US/aam/dcs_error_codes.html).
