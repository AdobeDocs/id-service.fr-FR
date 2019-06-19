---
title: Méthodes de bibliothèque ECID dans un univers ITP Safari
seo-title: Méthodes de bibliothèque ECID dans un univers ITP Safari
description: Documentation de la bibliothèque Adobe ECID (ID d'ID).
seo-description: Documentation de la bibliothèque Adobe ECID (ID d'ID).
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# Méthodes de bibliothèque ECID dans un univers ITP Safari

Safari renforçant le suivi inter-domaines via ITP, Adobe doit conserver les meilleures pratiques pour les bibliothèques qui prennent en charge les clients, ainsi que la confidentialité et le choix des utilisateurs.

Le 21 février 2019, Apple a annoncé sa dernière mise à jour vers ITP (Intelligent Tracking Prevention). Contrairement aux versions précédentes axées sur les cookies tiers, cette version détaille les nouvelles mesures de prévention du suivi pour les cookies propriétaires. Tous les cookies persistants propriétaires définis via l&#39;API document. cookie, souvent appelés cookies côté client, ont leur expiration plafonnée à 7 jours. Les cookies tiers continueront à être bloqués, comme indiqué dans les versions précédentes d&#39;ITP. Pour plus d&#39;informations sur ITP 2.1 et l&#39;impact des solutions Adobe, lisez [Safari ITP 2.1 Impact sur Adobe Experience Cloud et les clients de Platform Platform](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac).

## Adobe ECID pour Safari ITP FAQ

**Pourquoi le cookie AMCV, défini par la bibliothèque Experience Cloud ID (ECID) dans un domaine propriétaire des clients, est-il affecté par ITP 2.1 ?**

Le cookie AMCV repose actuellement sur l&#39;API document. cookie et est défini par « côté client ».  » » Safari favorise les cookies définis à partir du serveur d&#39;un client.

**Pourquoi un cookie défini via un serveur de suivi CNAME est-il une meilleure option pour le suivi dans Safari ?**

Les règles d&#39;ITP se concentrent sur leur remise aux développeurs. Les implémentations via les certificats CNAME ne peuvent pas être effectuées uniquement via JavaScript. Le programme de certification CNAME d&#39;Adobe (suivi côté serveur) est conforme aux normes ITP et fait partie de la stratégie Adobe depuis de nombreuses années. La bibliothèque ECID publie des méthodes qui se concentrent sur le déplacement de la fonctionnalité de bibliothèque ECID vers une implémentation CNAME.

**Pourquoi Adobe est-il concentré sur la bibliothèque ECID lorsque d&#39;autres méthodes de suivi des visiteurs Analytics sont utilisées avec les CNAME aujourd&#39;hui ?**

La bibliothèque ECID, le cookie AMCV et l&#39;ECID (alias MID) ont commencé comme méthode d&#39;intégration de toutes les solutions Adobe sous un ID. Cet ID restera l&#39;identifiant de niveau cookie prioritaire dans le guide du produit Adobe. Il s&#39;agit de l&#39;identifiant de cookie par défaut pour la plateforme Adobe Experience Platform.

**Les CNAME aident-ils les clients à activer le suivi multidomaines ?**

Les mêmes règles et avertissements existent déjà avec les CNAME. Dans certains cas, cname peut contribuer à un scénario multidomaines. Si vous disposez d&#39;un site d&#39;accès principal où les utilisateurs peuvent être identifiés avant de visiter d&#39;autres domaines, un CNAME peut activer le suivi multidomaines dans les navigateurs qui n&#39;acceptent pas les cookies tiers. Toutefois, alors que cname peut contribuer à plusieurs domaines dans certains cas, la raison du décalage des implémentations ECID vers CNAME est pour l&#39;identification persistante des visiteurs et non pour le suivi multi-domaine. Pour plus d&#39;informations sur CNAME et multidomaines, voir [CNAME de collecte de données et suivi inter-domaines](/help/reference/analytics-reference/cname.md).

D&#39;autres questions fréquentes seront ajoutées ici lorsque des modifications ITP supplémentaires sont publiées. Pour plus d&#39;informations, consultez la [page Adobe Experience League](https://experienceleague.adobe.com/#recommended/solutions/analytics).

## Modifications, méthodes et configurations liées à ITP

Des méthodes supplémentaires étant créées pour le suivi dans Safari, elles seront ajoutées comme référence à cette page.

>[!NOTE]*ECID* = *MID* = *MCID* dans toutes les documentations ci-dessous.

Voir ci-dessous pour connaître les efforts liés à l&#39;utilisation des bibliothèques ITP et ECID.

## Utiliser la bibliothèque ECID et le suivi CNAME pour étendre l&#39;expiration de l&#39;identifiant visiteur

ITP 2.1 empêche la possibilité d&#39;écrire des cookies côté client, ce qui altère la capacité de fournir des informations précises sur le suivi des visiteurs aux clients. Par conséquent, une modification est introduite dans les serveurs de suivi CNAME d&#39;Adobe pour stocker l&#39;identifiant d&#39;expérience du visiteur (ECID) dans un cookie propriétaire.

Cette modification n&#39;est utile que pour les clients ECID qui utilisent un CNAME Analytics dans le contexte propriétaire. Si vous êtes un client Analytics qui n&#39;utilise pas actuellement un CNAME, ou même un client non Analytics, vous êtes toujours éligible pour un enregistrement CNAME. Contactez le service à la clientèle ou le représentant du compte pour lancer le processus d&#39;enregistrement pour un [CNAME](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/adobe_managed_cert_pgm.html).

Effectuez la mise à niveau vers la bibliothèque ECID v. 4.3.0 + pour profiter de cette modification.

**Conception**

Lorsqu&#39;une demande d&#39;ID est envoyée à demdex. net et qu&#39;un ECID est récupéré, si un serveur de suivi est défini dans votre bibliothèque ECID, une demande d&#39;ID est envoyée au domaine du client. Ce point de fin lit le paramètre ecid de la chaîne de requête et définit un [nouveau cookie](/help/introduction/cookies.md) qui comprend uniquement l&#39;ECID et une date d&#39;expiration deux ans à venir. Chaque fois que ce point de fin est appelé de cette manière, `s_ecid` le cookie est réécrit avec une date d&#39;expiration deux ans à compter de l&#39;heure de cet appel. La bibliothèque ECID doit être mise à jour vers la version 4.3.0 afin que la valeur de ce cookie puisse être récupérée.

Ce nouveau `s_ecid` cookie suit le même état d&#39;exclusion que le cookie AMCV. Si l&#39;ecid est lu à partir `s_ecid` du cookie, demdex est toujours appelé immédiatement pour récupérer le dernier état d&#39;exclusion correspondant à cet identifiant et stocké dans le cookie AMCV.

De plus, si votre client a désactivé le suivi Analytics via cette [méthode](https://marketing.adobe.com/resources/help/en_US/sc/implement/opt_out_link.html), ce `s_ecid` cookie sera supprimé.

Le nom du serveur de suivi doit être fourni à la bibliothèque visitorjs lors de l&#39;initialisation de la bibliothèque à l&#39;aide de trackingserver ou trackingserversecure. Ceci doit correspondre à la configuration trackingserver dans les configurations Analytics.

Si vous choisissez de ne pas tirer parti de cette méthode, ajoutez la configuration suivante à votre implémentation de la bibliothèque ECID : Discardtrackingserverecid. Lorsque cette configuration est définie sur true, la bibliothèque du visiteur ne lit pas le MID défini par le serveur de suivi propriétaire.

![](assets/itp-proposal-v1.png)

## Utiliser la méthode appendvisitoridsto pour le suivi inter-domaines (dans les domaines de votre propre société)

Cette fonction vous permet de partager l&#39;ECID d&#39;un visiteur sur plusieurs domaines lorsque les navigateurs bloquent les cookies tiers. Pour utiliser cette fonction, vous devez avoir mis en œuvre le service d’ID et posséder les domaines source et de destination. Disponible dans visitorapi. js 1.7.0 ou version ultérieure (mais pas dans la version 1.10.0).

**Conception**

* Lorsqu&#39;un visiteur navigue sur vos autres domaines, le visiteur. appendvisitoridsto (url) renvoie une URL avec un ECID annexé comme paramètre de requête.

   Utilisez cette URL pour rediriger depuis le domaine d&#39;origine vers le domaine de destination.

* Le code du service d&#39;ID sur le domaine de destination extrait l&#39;ECID de l&#39;URL au lieu d&#39;envoyer une requête à Adobe pour son identifiant.

   Cette requête inclut l’ID de cookie tiers, qui n’est pas disponible dans ce cas.

* Le code du service d&#39;ID sur la page de destination utilise l&#39;ECID transmis pour effectuer le suivi du visiteur.

   >[!NOTE]
   >Si la page de destination dispose déjà d&#39;un ECID provenant de visites précédentes, la décision de surécrire le cookie existant est contrôlée par cette configuration overwritecrossdomainmcidandaid. Pour plus d&#39;informations sur cette configuration, voir [overwritecrossdomainmcidandaid](/help/library/function-vars/overwrite-visitor-id.md).
   >
   >Pour plus d&#39;informations sur cette méthode, consultez la page de référence [appendvisitoridsto (Cross Domain Tracking)](/help/library/get-set/appendvisitorid.md) .
