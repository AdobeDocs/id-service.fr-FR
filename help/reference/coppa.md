---
description: La loi COPPA (Children’s Online Privacy Protection Act) interdit la collecte en ligne d’informations personnelles sur les mineurs de moins de 13 ans sans le consentement vérifiable de l’un des parents. Les clients concernés par la loi COPPA peuvent ajouter une variable facultative à leur code de service Experience Cloud ID, ce qui l'empêche de définir les cookies dans le domaine tiers d'un navigateur.
keywords: Service d’identification
seo-description: La loi COPPA (Children’s Online Privacy Protection Act) interdit la collecte en ligne d’informations personnelles sur les mineurs de moins de 13 ans sans le consentement vérifiable de l’un des parents. Les clients concernés par la loi COPPA peuvent ajouter une variable facultative à leur code de service Experience Cloud ID, ce qui l'empêche de définir les cookies dans le domaine tiers d'un navigateur.
seo-title: Prise en charge COPPA dans le service Experience Cloud ID
title: Prise en charge COPPA dans le service Experience Cloud ID
uuid: 621 b 5 ebd -92 e 7-4635-be 85-8 d 7 e 36589 fcb
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Prise en charge COPPA dans le service Experience Cloud ID {#coppa-support-in-the-experience-cloud-id-service}

La loi COPPA (Children’s Online Privacy Protection Act) interdit la collecte en ligne d’informations personnelles sur les mineurs de moins de 13 ans sans le consentement vérifiable de l’un des parents. Les clients concernés par la loi COPPA peuvent ajouter une variable facultative à leur code de service Experience Cloud ID, ce qui l&#39;empêche de définir les cookies dans le domaine tiers d&#39;un navigateur.

>[!NOTE]
>
>Pour les versions 1.5.3 ou ultérieures.

**Cookies et suivi**

Au chargement d’une page web, le service [!DNL Experience Cloud] ID appelle un serveur de collecte de données [!DNL Adobe]. La réponse du serveur de collecte de données comprend un cookie Experience Cloud et un cookie demdex.net.

* Le cookie Experience Cloud est défini dans le domaine propriétaire. Il ne peut pas être utilisé pour effectuer le suivi des visiteurs dans différents domaines, à moins que ces domaines ne fonctionnent ensemble pour autoriser l’accès.
* Le cookie demdex.net est défini dans le domaine tiers. Il contient un identifiant unique qui peut être utilisé pour suivre les visiteurs dans différents domaines.

**Cookies et conformité à la loi COPPA**

Les cookies tiers qui effectuent le suivi des visiteurs dans différents domaines sur des sites Web destinés aux enfants déclenchent des exigences de consentement des parents COPPA. Pour respecter plus facilement la loi COPPA dans le cadre des analyses internes du site Web, ajoutez la variable `disableThirdPartyCookies:true` à la fonction `Visitor.getInstance`, comme illustré ci-après.

```js
//Call the ID service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

Lorsqu’il est défini sur la valeur `true`, l’objet `disableThirdPartyCookies` empêche le serveur de collecte de données de renvoyer le cookie tiers demdex.net. Si le navigateur d’un visiteur du site contient déjà ce cookie, le service d’ID ne l’utilise pas pour créer un [!DNL Experience Cloud] ID ou renvoyer un ID existant. Le service [!DNL Experience Cloud] ID crée à la place un ID aléatoire dans le cookie propriétaire. Une fois qu’il est activé, vous pouvez collecter des données à l’aide du service d’ID et les partager dans les différentes solutions [!DNL Experience Cloud], y compris les autres opérations internes autorisées par la loi COPPA.

>[!MORE_ LIKE_ THIS]
>
>* [Centre de traitement des données personnelles Adobe](http://www.adobe.com/privacy.html)
>* [Définition de la loi COPPA](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis) (en anglais)

