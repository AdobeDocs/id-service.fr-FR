---
title: Méthodes de bibliothèque ECID dans un univers ITP Safari
description: Documentation pour la bibliothèque Adobe ECID (service d’identification des visiteurs).
exl-id: ac1d1ee1-2b5f-457a-a694-60bb4c960ae7
TQID: https://experienceleague.adobe.com/GwI5LkCBXGiKyfjGm6bOqbyGbHQ2GwW64PeyLIrl3Ck
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 830
ht-degree: 75%

---

# Méthodes de bibliothèque ECID dans un univers ITP Safari

>[!NOTE]
>
>Des mises à jour ont été apportées pour refléter les dernières modifications appliquées à ITP, publiées le 12 novembre 2020 dans le cadre de la version Big Sur de macOS.

Safari renforçant le suivi inter-domaines via ITP, Adobe doit conserver de bonnes pratiques pour les bibliothèques qui prennent en charge les clients, ainsi que la confidentialité et le choix des utilisateurs.

Depuis le 10 novembre 2020, tous les cookies propriétaires persistants définis via l’API document.cookie, souvent appelés cookies « côté client », ainsi que les cookies définis via les implémentations CNAME propriétaires dans Safari et les navigateurs mobiles iOS sont dotés d’une durée d’expiration plafonnée à sept jours. Les cookies tiers continueront d’être bloqués, comme indiqué dans les versions précédentes d’ITP. Pour plus d’informations sur ITP 2.1 et l’impact des solutions Adobe, lisez [Safari ITP 2.1 Impact on Adobe Experience Platform Customers (en anglais)](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac).

## Modifications, méthodes et configurations liées à l’ITP

À mesure que des méthodes supplémentaires sont créées pour le suivi dans Safari, elles seront ajoutées comme référence à cette page.

>[!NOTE]
>
>*ECID* = *MID* = *MCID* dans toutes les documentations ci-dessous.

Voir ci-dessous pour connaître les efforts liés à l’utilisation des bibliothèques ITP et ECID.

## Comportement actuel de la bibliothèque ECID avec l’ITP et WebKit d’Apple

ITP 2.1 empêche la possibilité d’écrire des cookies côté client, ce qui empêche de fournir aux clients des informations précises de suivi des visiteurs. Par conséquent, une modification est introduite dans les serveurs de suivi CNAME d’Adobe pour stocker l’ECID du visiteur dans un cookie propriétaire.

Cette modification n’est utile que pour les clients ECID qui utilisent un CNAME Analytics dans un contexte propriétaire. Si vous êtes un client Analytics qui n’utilise pas actuellement de CNAME, ou même un client non Analytics, vous êtes tout de même éligible pour un enregistrement CNAME. Contactez le service à la clientèle ou votre représentant de compte pour lancer le processus d’enregistrement d’un [CNAME](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-first-party.html?lang=fr).

Mise à niveau vers la bibliothèque ECID v. 4.3.0 + pour tirer parti de ce changement.

Ce qui suit décrit le comportement de la bibliothèque ECID avec l’ITP 2.1 et les dernières modifications apportées par Apple dans le cadre de la version Big Sur.

**Conception**

Lorsqu’une requête d’ID est envoyée à demdex.net et qu’un ECID est récupéré, si un serveur de suivi est défini dans votre bibliothèque ECID, une requête d’ID est envoyée au domaine du client. Ce point d’entrée lit le paramètre ecid dans la chaîne de requête et définit un nouveau [cookie](/help/introduction/cookies.md) qui comprend uniquement l’ECID et une date d’expiration de deux ans. Chaque fois que ce point d’entrée est appelé de cette manière, le cookie `s_ecid` est réécrit avec une date d’expiration de deux ans à compter du moment de cet appel. La bibliothèque ECID doit être mise à jour vers la version 4.3.0 afin que la valeur de ce cookie puisse être récupérée.

>[!IMPORTANT]
>
>Dans le cadre des mises à jour de Big Sur, un `s_ecid` cookie défini via CNAME est également conservé pendant sept jours, jusqu’à son expiration.

Ce nouveau cookie `s_ecid` suit le même état d’exclusion que le cookie AMCV. Si l’ecid est lu à partir du cookie `s_ecid`, demdex est toujours appelé immédiatement pour récupérer le dernier état d’exclusion correspondant à cet identifiant et stocké dans le cookie AMCV.

De plus, si votre client a désactivé le suivi Analytics via cette [méthode](https://experienceleague.adobe.com/docs/analytics/implementation/js/opt-out.html?lang=fr), ce cookie `s_ecid` sera supprimé.

Le nom du serveur de suivi doit être fourni à la bibliothèque VisitorJS lors de l’initialisation de la bibliothèque à l’aide de `trackingServer` ou de `trackingServerSecure`. Cela doit correspondre à la configuration `trackingServer` dans les configurations Analytics.

Si vous choisissez de ne pas utiliser cette méthode, ajoutez la configuration suivante à votre implémentation de la bibliothèque ECID : `discardtrackingServerECID`. Lorsque cette configuration est définie sur la valeur true, la bibliothèque du visiteur ne lit pas le MID défini par le serveur de suivi propriétaire.

![](assets/itp-proposal-v1.png)

## Utiliser la méthode appendVisitorIDsTo pour le suivi inter-domaines (dans les domaines de votre propre société)

Cette fonction permet de partager l’ECID d’un visiteur sur plusieurs domaines lorsque les navigateurs bloquent les cookies tiers. Pour utiliser cette fonction, vous devez avoir mis en œuvre le service d’identification des visiteurs et être propriétaire des domaines source et de destination. Disponible dans `VisitorAPI.js` version 1.7.0 ou ultérieure (mais pas dans la version 1.10.0).

**Conception**

* Lorsqu’un visiteur navigue sur vos autres domaines, le Visitor.appendVisitorIDsTo(url) renvoie une URL avec un ECID annexé comme paramètre de requête.

  Utilisez cette URL pour rediriger depuis le domaine d’origine vers le domaine de destination.

* Le code du service d’identification des visiteurs sur le domaine de destination extrait l’ECID de l’URL au lieu d’envoyer une requête pour obtenir l’identifiant de ce visiteur à Adobe.

  Cette requête inclut l’ID de cookie tiers, qui n’est pas disponible dans ce cas.

* Le code du service d’identification des visiteurs sur la page de destination utilise l’ECID transmis pour suivre le visiteur.

  >[!NOTE]
  >Si la page de destination dispose déjà d’un ECID provenant de visites précédentes, la décision de remplacer le cookie existant est contrôlée par cette configuration overwriteCrossDomainMCIDAndAID. Pour plus d’informations sur cette configuration, voir [overwriteCrossDomainMCIDAndAID](/help/library/function-vars/overwrite-visitor-id.md).
  >
  >Pour plus d’informations sur cette méthode, consultez la page de référence [appendVisitorIDsTo (suivi inter-domaines)](/help/library/get-set/appendvisitorid.md).

