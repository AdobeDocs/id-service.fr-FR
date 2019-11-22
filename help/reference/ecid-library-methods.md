---
title: Méthodes de bibliothèque ECID dans un univers ITP Safari
seo-title: Méthodes de bibliothèque ECID dans un univers ITP Safari
description: Documentation pour la bibliothèque Adobe ECID (Service d’ID).
seo-description: Documentation pour la bibliothèque Adobe ECID (Service d’ID).
translation-type: tm+mt
source-git-commit: 51abd7b0f38da4c3375c0d2fe48d8bf96bdfb387

---


# Méthodes de bibliothèque ECID dans un univers ITP Safari

Safari renforçant le suivi inter-domaines via ITP, Adobe doit conserver les meilleures pratiques pour les bibliothèques qui prennent en charge les clients, ainsi que la confidentialité et le choix des utilisateurs.

Le 21 février 2019, Apple a annoncé sa dernière mise à jour vers ITP (Intelligent Tracking Prevention). Contrairement aux versions précédentes axées sur les cookies tiers, cette version détaille les nouvelles mesures de prévention du suivi pour les cookies propriétaires. Tous les cookies propriétaires persistants définis via l’API document.cookie, souvent appelés cookies « côté client », voient leur expiration plafonnée à 7 jours. Les cookies tiers continueront d’être bloqués, comme indiqué dans les versions précédentes d’ITP. For more details on ITP 2.1 and the impact of Adobe solutions, read [Safari ITP 2.1 Impact on Adobe Experience Cloud and Experience Platform Customers](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac).

## FAQ de l’ECID Adobe pour Safari ITP

**Pourquoi le cookie AMCV, défini par la bibliothèque Experience Cloud ID (ECID) dans un domaine propriétaire des clients, est-il affecté par ITP 2.1 ?**

Le cookie AMCV repose actuellement sur l’API document.cookie et est défini « côté client ». Safari favorise les cookies définis à partir du serveur d’un client.

**Pourquoi un cookie défini via un serveur de suivi CNAME est-il une meilleure option pour le suivi dans Safari ?**

Les règles d’ITP visent à redonner le contrôle aux développeurs. Les mises en œuvre via les certificats CNAME ne peuvent pas être effectuées uniquement via JavaScript. Le programme de certification CNAME d’Adobe (suivi côté serveur) est conforme aux normes ITP et fait partie de la stratégie Adobe depuis de nombreuses années. La bibliothèque ECID publie des méthodes qui se concentrent sur le déplacement de la fonctionnalité de bibliothèque ECID vers une mise en œuvre CNAME.

**Pourquoi Adobe se concentre sur la bibliothèque ECID lorsque d’autres méthodes de suivi des visiteurs Analytics sont utilisées avec les CNAME aujourd’hui ?**

La bibliothèque ECID, le cookie AMCV et l’ECID (alias MID) étaient au départ la méthode d’intégration de toutes les solutions Adobe sous un ID. Cet ID restera l’identifiant prioritaire de niveau cookie dans la feuille de route du produit Adobe. Il s’agit de l’identifiant de cookie par défaut pour Adobe Experience Platform.

D’autres questions fréquentes seront ajoutées ici lorsque des modifications ITP supplémentaires seront publiées. Pour plus d’informations, consultez [Adobe Experience League](https://experienceleague.adobe.com/#recommended/solutions/analytics).

## Modifications, méthodes et configurations liées à ITP

À mesure que des méthodes supplémentaires sont créées pour le suivi dans Safari, elles seront ajoutées comme référence à cette page.

>[!NOTE] *ECID* = *MID* = *MCID* dans toutes les documentations ci-dessous.

Voir ci-dessous pour connaître les efforts liés à l’utilisation des bibliothèques ITP et ECID.

## Utilisation de la bibliothèque ECID du le suivi CNAME pour étendre l’expiration de l’identifiant visiteur

ITP 2.1 empêche la possibilité d’écrire des cookies côté client, ce qui empêche de fournir aux clients des informations précises de suivi des visiteurs. Par conséquent, une modification est introduite dans les serveurs de suivi CNAME d’Adobe pour stocker l’identifiant Experience Cloud ID (ECID) dans un cookie propriétaire.

Cette modification n’est utile que pour les clients ECID qui utilisent un CNAME Analytics dans un contexte propriétaire. Si vous êtes un client Analytics qui n’utilise pas actuellement de CNAME, ou même un client non Analytics, vous êtes tout de même éligible pour un enregistrement CNAME. Contact Customer Care or your account representative to start the process of registering for a [CNAME](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/adobe_managed_cert_pgm.html).

Effectuez la mise à niveau vers la bibliothèque ECID v. 4.3.0 + pour profiter de cette modification.

**Conception**

Lorsqu’une requête d’ID est envoyée à demdex.net et qu’un ECID est récupéré, si un serveur de suivi est défini dans votre bibliothèque ECID, une requête d’ID est envoyée au domaine du client. Ce point de terminaison lit le paramètre ecid dans la chaîne de requête et définit un nouveau [cookie](/help/introduction/cookies.md) qui comprend uniquement l’ECID et une date d’expiration de deux ans. Chaque fois que ce point de terminaison est appelé de cette manière, le cookie `s_ecid` est réécrit avec une date d’expiration de deux ans à compter du moment de cet appel. La bibliothèque ECID doit être mise à jour vers la version 4.3.0 afin que la valeur de ce cookie puisse être récupérée.

Ce nouveau cookie `s_ecid` suit le même état d’exclusion que le cookie AMCV. Si l’ecid est lu à partir du cookie `s_ecid`, demdex est toujours appelé immédiatement pour récupérer le dernier état d’exclusion correspondant à cet identifiant et stocké dans le cookie AMCV.

In addition, if your consumer has opted out of Analytics tracking via this [method](https://marketing.adobe.com/resources/help/en_US/sc/implement/opt_out_link.html), this `s_ecid` cookie will be deleted.

Le nom du serveur de suivi doit être fourni à la bibliothèque VisitorJS lors de l’initialisation de la bibliothèque à l’aide de trackingServer ou de trackingServerSecure. Cela doit correspondre à la configuration trackingServer dans les configurations Analytics.

Si vous choisissez de ne pas tirer parti de cette méthode, ajoutez la configuration suivante à votre mise en œuvre de la bibliothèque ECID : discardtrackingServerECID. Lorsque cette configuration est définie sur la valeur true, la bibliothèque du visiteur ne lit pas le MID défini par le serveur de suivi propriétaire.

![](assets/itp-proposal-v1.png)

## Utiliser la méthode appendVisitorIDsTo pour le suivi inter-domaines (dans les domaines de votre propre société)

Cette fonction permet de partager l’ECID d’un visiteur sur plusieurs domaines lorsque les navigateurs bloquent les cookies tiers. Pour utiliser cette fonction, vous devez avoir mis en œuvre le service d’ID et posséder les domaines source et de destination. Disponible dans VisitorAPI.js version 1.7.0 ou version ultérieure (mais pas dans la version 1.10.0).

**Conception**

* Lorsqu’un visiteur navigue sur vos autres domaines, le Visitor.appendVisitorIDsTo(url) renvoie une URL avec un ECID annexé comme paramètre de requête.

   Utilisez cette URL pour rediriger depuis le domaine d’origine vers le domaine de destination.

* Le code du service d’ID sur le domaine de destination extrait l’ECID de l’URL au lieu d’envoyer une requête d’identifiant à Adobe pour l’ID de ce visiteur.

   Cette requête inclut l’ID de cookie tiers, qui n’est pas disponible dans ce cas.

* Le code du service d’ID sur la page de destination utilise l’ECID transmis pour effectuer le suivi du visiteur.

   >[!NOTE]
   >Si la page de destination dispose déjà d’un ECID provenant de visites précédentes, la décision de remplacer le cookie existant est contrôlée par cette configuration overwriteCrossDomainMCIDAndAID. Pour plus d’informations sur cette configuration, voir [overwriteCrossDomainMCIDAndAID](/help/library/function-vars/overwrite-visitor-id.md).
   >
   >Pour plus d’informations sur cette méthode, consultez la page de référence [appendVisitorIDsTo (suivi inter-domaines)](/help/library/get-set/appendvisitorid.md).
