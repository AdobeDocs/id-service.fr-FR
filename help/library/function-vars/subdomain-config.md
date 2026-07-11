---
description: Remplacez le nom de domaine par défaut utilisé par les appels au service d’identification des visiteurs par votre propre nom de sous-domaine avec ces configurations.
keywords: Service d’identification des visiteurs
title: audienceManagerServer et audienceManagerServerSecure
exl-id: b740eb5c-ac4e-46f4-ba7c-1080d8d9292d
TQID: https://experienceleague.adobe.com/a5KVErDX4putY8d9vGf-uAwswNzE0Maf-JEyfmQxhbg
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 234
ht-degree: 44%

---

# audienceManagerServer et audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

Remplacez le nom de domaine par défaut utilisé par les appels au service d’identification des visiteurs par votre propre nom de sous-domaine avec ces configurations.

**Syntaxe :**

* `audienceManagerServer: " *`votre nom de sous-domaine`*.demdex.net"`
* `audienceManagerServerSecure: " *`votre nom de sous-domaine`*.demdex.net"`

**Rôle**

Normalement, le service d’identification des visiteurs passe des appels à Adobe au `dpm.demdex.net`. Parfois, vous pouvez ne pas vouloir effectuer des appels à cette destination, car elle semble trop générique ou « tierce ». Pour que l’appel du service d’identification des visiteurs ressemble davantage à un appel propriétaire, utilisez ces configurations pour ajouter votre nom de sous-domaine Audience Manager à `demdex.net`, comme illustré ci-dessous. Pour plus d’informations sur l’appel à `dpm.demdex.net`, voir [Signification des appels vers le domaine Demdex](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=fr).

**Conditions**

Ces configurations nécessitent que vous utilisiez les éléments suivants :

* Nom d’enregistrement du sous-domaine Audience Manager de votre société. Vérifiez ou obtenez ce nom auprès de votre conseiller.
* Nom de sous-domaine associé à votre ID d’organisation IMS.
* *Les deux* paramètres de configuration portent le même nom de sous-domaine.

**Exemple de code**

Dans cet exemple, imaginons une société de divertissement multimédia qui a exprimé des inquiétudes juridiques relatives aux appels à `dpm.demdex.net`. Dans Audience Manager, le nom de sous-domaine de société de l’enregistrement est Music1. L’exemple de code suivant montre comment attribuer une marque à l’appel de données du service d’identification des visiteurs avec ce nom de sous-domaine spécifique au client.

```
//Instantiate Visitor 
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE",{ 
     ... 
     //Configure Visitor ID Service call 
     audienceManagerServer: "Music1.demdex.net", 
     audienceManagerServerSecure: "Music1.demdex.net" 
     } 
);
```

