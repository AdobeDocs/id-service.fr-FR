---
description: La loi COPPA (Children’s Online Privacy Protection Act) interdit la collecte en ligne d’informations personnelles sur les mineurs de moins de 13 ans sans le consentement vérifiable de l’un des parents. Les clients qui le souhaitent peuvent ajouter une variable en option au code de leur service Experience Cloud Identity afin de l’empêcher de définir des cookies dans le domaine tiers d’un navigateur.
keywords: Service d’ID
title: Prise en charge de la norme COPPA dans le service d’identités d’Experience Cloud
exl-id: c7579f90-3011-4e26-b908-08907bf12ba2
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 100%

---

# Prise en charge de la norme COPPA dans le service d’identités d’Experience Cloud {#coppa-support-in-the-experience-cloud-id-service}

La loi COPPA (Children’s Online Privacy Protection Act) interdit la collecte en ligne d’informations personnelles sur les mineurs de moins de 13 ans sans le consentement vérifiable de l’un des parents. Les clients qui le souhaitent peuvent ajouter une variable en option au code de leur service d’identités d’Experience Cloud afin de l’empêcher de définir des cookies dans le domaine tiers d’un navigateur.

>[!NOTE]
>
>Pour les versions 3.0.0 ou ultérieures.

**Cookies et suivi**

Au chargement d’une page web, le service [!DNL Experience Cloud] ID appelle un serveur de collecte de données [!DNL Adobe]. La réponse du serveur de collecte de données comprend un cookie Experience Cloud et un cookie demdex.net.

* Le cookie Experience Cloud est défini dans le domaine propriétaire. Il ne peut pas être utilisé pour effectuer le suivi des visiteurs sur différents domaines, sauf si ces domaines fonctionnent ensemble pour autoriser l’accès.
* Le cookie demdex.net est défini dans le domaine tiers. Il contient un identifiant unique qui peut être utilisé pour effectuer le suivi des visiteurs sur différents domaines.

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

>[!MORELIKETHIS]
>
>* [Centre de traitement des données personnelles Adobe](http://www.adobe.com/fr/privacy.html)
>* [Définition de la loi COPPA](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)
