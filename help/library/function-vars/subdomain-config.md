---
description: Définissez le nom de domaine par défaut utilisé par les appels au service d’identités d’Experience Cloud en votre propre nom de sous-domaine avec ces configurations.
keywords: Service d’ID
title: audienceManagerServer et audienceManagerServerSecure
exl-id: b740eb5c-ac4e-46f4-ba7c-1080d8d9292d
TQID: https://experienceleague.adobe.com/a5KVErDX4putY8d9vGf-uAwswNzE0Maf-JEyfmQxhbg
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 222
ht-degree: 100%

---

# audienceManagerServer et audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

Définissez le nom de domaine par défaut utilisé par les appels au service d’identités d’Experience Cloud en votre propre nom de sous-domaine avec ces configurations.

**Syntaxe :**

* `audienceManagerServer: " *`votre nom de sous-domaine`*.demdex.net"`
* `audienceManagerServerSecure: " *`votre nom de sous-domaine`*.demdex.net"`

**Rôle**

Normalement, le service [!DNL Experience Cloud] ID appelle [!DNL Adobe] à l’adresse `dpm.demdex.net`. Parfois, vous pouvez ne pas vouloir effectuer des appels à cette destination, car elle semble trop générique ou « tierce ». Pour que l’appel au service d’ID ressemble davantage à un appel propriétaire, utilisez ces configurations pour ajouter votre nom de [!DNL Audience Manager] sous-domaine à `demdex.net` comme indiqué ci-dessous. Pour plus d’informations sur l’appel à `dpm.demdex.net`, voir [Signification des appels vers le domaine Demdex](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=fr).

**Conditions**

Ces configurations nécessitent que vous utilisiez les éléments suivants :

* Le nom du [!DNL Audience Manager] sous-domaine de l’enregistrement pour votre société. Vérifiez ou obtenez ce nom auprès de votre conseiller.
* Le nom du sous-domaine associé à votre [!UICONTROL Organization ID].
* *Les deux* paramètres de configuration portent le même nom de sous-domaine.

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

