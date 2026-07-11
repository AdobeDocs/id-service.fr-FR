---
description: Le service d’identification des visiteurs Adobe active le framework d’identification courant pour les applications et services d’entreprise CX. Il fonctionne en attribuant à un visiteur ou une visiteuse du site un identifiant persistant et unique, appelé ECID.
keywords: Service d’identification des visiteurs ; ECID
title: Service d’identification des visiteurs Adobe
exl-id: fe1368db-06ca-4c79-b655-b7064e316d74
TQID: https://experienceleague.adobe.com/xzEgzuN2NnyOnhCPocQikOXHFRU6zmLWLGdrJL4C3GM
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 433
ht-degree: 30%

---

# Service d’identification des visiteurs Adobe {#experience-cloud-id-service}

>[!BEGINSHADEBOX]

Le service d’identification des visiteurs n’est **pas** le [service Experience Platform Identity](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=fr). Le service d’identification des visiteurs est la `VisitorAPI.js` bibliothèque JavaScript décrite dans ce guide qui définit l’ECID pour Adobe Analytics, Audience Manager et Target. Si vous recherchez le service Adobe Experience Platform qui résout les identités entre les appareils et les systèmes en un profil client unifié, reportez-vous à la [présentation du service d’identités Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=fr) à la place.

>[!ENDSHADEBOX]

Le service d’identification des visiteurs Adobe active le framework d’identification courant pour les applications et services d’entreprise CX. Il fonctionne en attribuant à un visiteur ou une visiteuse du site un identifiant persistant et unique, appelé ECID.

## Comprendre les principales entités identitaires

Pour mieux comprendre la façon unique dont Adobe identifie les visiteurs et visiteuses et résout les informations d’identité, lisez la présentation ci-dessous :

* **Service d’identification des visiteurs** : le service d’identification des visiteurs **est chargé de définir l’ECID**. Pour plus d’informations, consultez la [présentation du service d’identification des visiteurs](./introduction/overview.md).
* **ECID** : l’ECID est un espace de noms d’identité partagé utilisé dans les applications Adobe Experience Platform et Adobe CX Enterprise pour identifier les personnes et les appareils. Pour plus d’informations sur l’ECID, consultez la [Présentation de l’ECID](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/ecid).
* **Experience Platform Identity Service** : le service d’identités Experience Platform Identity Service vous offre une vue d’ensemble complète de vos client(e)s et de leur comportement en rapprochant les identités sur les appareils et systèmes. Pour plus d’informations, reportez-vous à la [Présentation du service d’identités d’Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=fr).

## Commencer

* [Présentation du service d’identification des visiteurs](introduction/overview.md) : découvrez ce que fait le service d’identification des visiteurs et comment il s’intègre dans l’expérience client d’entreprise.
* [Conditions requises pour le service d’identification des visiteurs](reference/requirements.md) : vérifiez que vos solutions et bibliothèques de code remplissent les conditions préalables avant de mettre en œuvre le service d’identification des visiteurs.
* [Méthodes d’implémentation ](implementation-guides/implementation-methods.md) : comparez l’implémentation standard à l’aide de [balises](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=fr) aux méthodes d’intégration directe non standard.

## Accéder à la documentation

**Mise en œuvre**

* [Guides de mise en œuvre](implementation-guides/implementation-guides.md)
* [Intégration directe au service d’identification des visiteurs](implementation-guides/direct-integration.md)
* [Présentation du service Opt-in](implementation-guides/opt-in-service/optin-overview.md)
* [Test et vérification du service d’identification des visiteurs](implementation-guides/test-verify.md)

**Référence d’API**

* [Présentation de l’API du service d’identification des visiteurs](library/library.md)
* [getVisitorValues](library/get-set/getvisitorvalues.md)
* [idSyncContainerID](library/function-vars/idsyncontainerid.md)

**Questions fréquentes**

* [FAQ sur le service d’identification des visiteurs](faq-intro/faq.md)
* [Questions fréquentes sur les autres solutions CX Enterprise](faq-intro/other-faq.md)

## Ressources supplémentaires

* [Versions de la bibliothèque JavaScript ECID](https://github.com/Adobe-Marketing-Cloud/id-service/releases) sur GitHub
* [Notes de mise à jour du service d’identification des visiteurs](release-notes/notes-2022.md)
* [Centre de traitement des données personnelles d’Adobe](http://www.adobe.com/fr/privacy.html)
* [Documentation sur Adobe CX Enterprise](https://experienceleague.adobe.com/docs/home.html?lang=fr)

