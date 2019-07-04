---
description: La loi COPPA (Children’s Online Privacy Protection Act) interdit la collecte en ligne d’informations personnelles sur les mineurs de moins de 13 ans sans le consentement vérifiable de l’un des parents. Les clients qui le souhaitent peuvent ajouter une variable en option au code de leur service Experience Cloud ID afin de l’empêcher de définir des cookies dans le domaine tiers d’un navigateur.
keywords: Service d’identification
seo-description: La loi COPPA (Children’s Online Privacy Protection Act) interdit la collecte en ligne d’informations personnelles sur les mineurs de moins de 13 ans sans le consentement vérifiable de l’un des parents. Les clients qui le souhaitent peuvent ajouter une variable en option au code de leur service Experience Cloud ID afin de l’empêcher de définir des cookies dans le domaine tiers d’un navigateur.
seo-title: Prise en charge COPPA dans le service Experience Cloud ID
title: Prise en charge COPPA dans le service Experience Cloud ID
uuid: 621b5ebd-92e7-4635-be85-8d7e36589fcb
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Prise en charge COPPA dans le service Experience Cloud ID {#coppa-support-in-the-experience-cloud-id-service}

La loi COPPA (Children’s Online Privacy Protection Act) interdit la collecte en ligne d’informations personnelles sur les mineurs de moins de 13 ans sans le consentement vérifiable de l’un des parents. Les clients qui le souhaitent peuvent ajouter une variable en option au code de leur service Experience Cloud ID afin de l’empêcher de définir des cookies dans le domaine tiers d’un navigateur.

>[!NOTE]
>
>Pour les versions 1.5.3 ou ultérieures.

**Cookies et suivi**

Au chargement d’une page web, le service [!DNL Experience Cloud] ID appelle un serveur de collecte de données [!DNL Adobe]. La réponse du serveur de collecte de données comprend un cookie Experience Cloud et un cookie demdex.net.

* Le cookie Experience Cloud est défini dans le domaine propriétaire. Il ne peut pas être utilisé pour effectuer le suivi des visiteurs dans différents domaines, à moins que ces domaines ne fonctionnent ensemble pour autoriser l’accès.
* Le cookie demdex.net est défini dans le domaine tiers. Il contient un identifiant unique qui peut être utilisé pour suivre les visiteurs dans différents domaines.

**Cookies et conformité à la loi COPPA**

Les cookies tiers qui effectuent le suivi des visiteurs dans différents domaines sur des sites Web destinés aux enfants déclenchent des exigences de consentement des parents COPPA. Pour respecter plus facilement la loi COPPA dans le cadre des analyses internes du site Web, ajoutez la variable `disableThirdPartyCookies:true` à la `Visitor.getInstance` fonction, comme illustré ci-après.

```js
//Call the ID service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

Lorsqu’il est défini sur la valeur `true`, `disableThirdPartyCookies` l’objet empêche le serveur de collecte de données de renvoyer le cookie tiers demdex.net. Si le navigateur d’un visiteur du site contient déjà ce cookie, le service d’ID ne l’utilise pas pour créer un [!DNL Experience Cloud] ID ou renvoyer un ID existant. Le service [!DNL Experience Cloud] ID crée à la place un ID aléatoire dans le cookie propriétaire. Une fois qu’il est activé, vous pouvez collecter des données à l’aide du service d’ID et les partager dans les différentes [!DNL Experience Cloud] solutions, y compris les autres opérations internes autorisées par la loi COPPA.

>[!MORE_LIKE_THIS]
>
>* [Centre de traitement des données personnelles Adobe](http://www.adobe.com/fr/privacy.html)
>* [Définition de la loi COPPA (en anglais)](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

