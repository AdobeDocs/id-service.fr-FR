---
description: Remplacez le nom de domaine par défaut utilisé par les appels au service Experience Cloud ID par votre propre nom de sous-domaine avec ces configurations.
keywords: Service d’identification
seo-description: Remplacez le nom de domaine par défaut utilisé par les appels au service Experience Cloud ID par votre propre nom de sous-domaine avec ces configurations.
seo-title: audienceManagerServer et audienceManagerServerSecure
title: audienceManagerServer et audienceManagerServerSecure
uuid: e 21 cacbf -5151-4 d 34-b 0 f 7-9 e 90275 f 4 c 7 c
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# audienceManagerServer et audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

Remplacez le nom de domaine par défaut utilisé par les appels au service Experience Cloud ID par votre propre nom de sous-domaine avec ces configurations.

**Syntaxe :**

* ` audienceManagerServer: " *`votre nom de sous-domaine`*.demdex.net"`
* ` audienceManagerServerSecure: " *`votre nom de sous-domaine`*.demdex.net"`

**Rôle**

Normally, the [!DNL Experience Cloud] ID service makes calls to [!DNL Adobe] at `dpm.demdex.net`. Parfois, vous pouvez ne pas vouloir effectuer des appels à cette destination, car elle semble trop générique ou « tierce ». Pour que l’appel au service d’ID ressemble davantage à un appel propriétaire, utilisez ces configurations pour ajouter votre nom de sous-domaine [!DNL Audience Manager] à `demdex.net` comme indiqué ci-dessous. Pour plus d’informations sur l’appel à `dpm.demdex.net`, voir [Signification des appels vers le domaine Demdex](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html).

**Conditions**

Ces configurations nécessitent que vous utilisiez :

* The [!DNL Audience Manager] subdomain name of record for your company. Vérifiez ou obtenez ce nom auprès de votre conseiller.
* The subdomain name associated with your [!DNL Organization ID].
* *Les deux* paramètres de configuration portant le même nom de sous-domaine.

**Exemple de code**

Dans cet exemple, imaginons une société de divertissement multimédia qui a exprimé des inquiétudes juridiques relatives aux appels à `dpm.demdex.net`. Dans [!DNL Audience Manager], le nom du sous-domaine d’enregistrement de la société est Music1. L’exemple de code suivant montre comment attribuer une marque à l’appel de données du service d’ID avec ce nom de sous-domaine spécifique au client.

```
//Instantiate Visitor 
var visitor = Visitor.getInstance("Insert Experience Cloud Organization ID here",{ 
     ... 
     //Configure ID service call 
     audienceManagerServer: "Music1.demdex.net", 
     audienceManagerServerSecure: "Music1.demdex.net" 
     } 
);
```

