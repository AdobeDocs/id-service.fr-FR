---
description: valeur nulle
keywords: ordre des opérations ; Service d'ID
seo-description: valeur nulle
seo-title: CNAME de collecte de données et suivi inter-domaines
title: CNAME de collecte de données et suivi inter-domaines
uuid: ba 42 c 822-b 677-4139-b 1 ed -4 d 98 d 3320 fd 0
translation-type: tm+mt
source-git-commit: 337e7eef2cce8c0bc827ec04833ad0d14ee9c89a

---


# CNAME de collecte de données et suivi inter-domaines{#data-collection-cnames-and-cross-domain-tracking}

Si vous disposez d’un site d’accès principal où les utilisateurs peuvent être identifiés avant de se rendre sur d’autres domaines, un CNAME peut activer le suivi interdomaines dans les navigateurs qui n’acceptent pas les cookies tiers (tels que Safari).

Dans les navigateurs qui acceptent les cookies tiers, un cookie est défini par les serveurs de collecte de données pendant la demande de récupération d’un identifiant visiteur. Ce cookie permet au service d’identification des visiteurs de renvoyer le même identifiant visiteur Experience Cloud sur tous les domaines configurés à l’aide du même ID d’organisation Experience Cloud.

Dans les navigateurs qui n’acceptent pas les cookies tiers, un nouvel identifiant visiteur Experience Cloud est attribué pour chaque domaine.

Le cookie demdex.net permet au service d’identification des visiteurs de fournir le même niveau de suivi inter-domaines que le cookie s_vi dans Analytics, où le cookie est accepté dans certains navigateurs et utilisé sur plusieurs domaines, mais rejeté par d’autres navigateurs.

## CNAME de collecte de données {#section-48fd186d376a48079769d12c4bd9f317}

Lorsque le cookie Analytics a été défini par le serveur de collecte de données, de nombreux clients ont configuré les enregistrements CNAME du serveur de collecte de données dans le cadre d’une [mise en œuvre de cookie propriétaire](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/) afin d’éviter des problèmes éventuels avec les navigateurs qui rejettent les cookies tiers. Ce processus configure votre domaine de serveur de collecte de données en fonction du domaine de votre site Web, de sorte que le cookie Identifiant visiteur soit défini comme cookie propriétaire.

Puisque le service d’identification des visiteurs définit à l’aide de JavaScript le cookie visiteur directement sur le domaine du site Web actif, cette configuration n’est plus nécessaire pour définir les cookies propriétaires.

Les clients qui disposent d’une propriété Web unique (un seul domaine) peuvent migrer en dehors des CNAME de collecte de données et utiliser plutôt leur nom d’hôte de collecte de données par défaut (`omtrdc.net` ou `2o7.net`).

Toutefois, l’utilisation d’un CNAME pour la collecte de données vous permet par ailleurs d’effectuer un suivi sur les visiteurs entre un domaine d’entrée principal et d’autres domaines dans les navigateurs qui n’acceptent pas les cookies tiers. Les clients qui disposent de plusieurs propriétés Web (plusieurs domaines) peuvent avoir intérêt à préserver un CNAME de collecte de données. La section ci-après explique comment fonctionne le suivi inter-domaines.

## Suivi inter-domaines à l’aide de CNAME – Fonctionnement {#section-78925af798e24917b9abed79de290ad9}

En raison de la façon dont les cookies propriétaires peuvent être utilisés dans un contexte tiers dans Apple Safari et dans certains autres navigateurs, un CNAME vous permet d’effectuer un suivi sur les clients entre un domaine principal et d’autres domaines utilisant le même serveur de suivi.

Supposons que votre site principal se situe à l’adresse `mymainsite.com`. Vous avez configuré l&#39;enregistrement CNAME pour pointer vers votre serveur de collecte de données sécurisé : `smetrics.mymainsite.com`.

Lorsqu’un visiteur se rend sur le site `mymainsite.com`, le cookie du service d’ID est défini par le serveur de collecte de données. Cela est autorisé puisque le domaine du serveur de collecte de données correspond au domaine du site Web. C&#39;est ce qu&#39;on désigne sous le nom d&#39;utilisation d&#39;un cookie dans *un contexte propriétaire*ou simplement d&#39; *un cookie propriétaire*.

Si vous utilisez également ce même serveur de collecte de données sur d&#39;autres sites (et, `myothersiteA.com`par exemple, et `myothersiteB.com`) et qu&#39;un visiteur visite plus tard ces sites, le cookie défini durant la visite est `mymainsite.com` envoyé dans la requête HTTPS au serveur de collecte de données (souvenez-vous que les navigateurs envoient tous les cookies d&#39;un domaine avec toutes les requêtes HTTPS à ce domaine, même si le domaine ne correspond pas au domaine du site Web actuel). Il s&#39;agit de l&#39;utilisation d&#39;un cookie dans un contexte *tiers*, ou simplement d&#39;un cookie *tiers*. Il permet également d&#39;utiliser le même identifiant visiteur sur ces autres domaines. Notez que les navigateurs gèrent les cookies dans des contextes tiers différents des cookies propriétaires.

*Remarque : Safari bloque tous les cookies dans le contexte tiers, quelle que soit la manière dont ils sont définis.*

Par conséquent, pour qu’un visiteur soit identifié entre plusieurs domaines, votre domaine de collecte doit être un domaine que les utilisateurs visitent couramment. S&#39;il n&#39;existe aucun *domaine commun* à utiliser pour le domaine de collecte de données, il n&#39;existe aucun avantage inter-domaines pour la gestion d&#39;un CNAME pour le domaine de collecte de données. Si le site d’accès principal n’est pas le premier site visité, les visiteurs sont identifiés différemment sur le site secondaire et sur le site principal.

## Activation de la prise en charge de la collecte de données propriétaires (CNAME) avec le service Experience Cloud ID {#section-25d4feb686d944e3a877d7aad8dbdf9a}

La prise en charge CNAME du serveur de collecte de données est activée en définissant `visitor.marketingCloudServerSecure` les variables.
