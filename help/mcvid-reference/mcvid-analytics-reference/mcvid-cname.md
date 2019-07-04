---
description: valeur nulle
keywords: ordre des opérations ; service d’ID
seo-description: valeur nulle
seo-title: CNAME de collecte de données et suivi inter-domaines
title: CNAME de collecte de données et suivi inter-domaines
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: ht
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

Supposons que votre site principal se situe à l’adresse `mymainsite.com`. Vous avez configuré l’enregistrement CNAME pour pointer vers votre serveur de collecte de données sécurisé : `smetrics.mymainsite.com`.

Lorsqu’un visiteur se rend sur le site `mymainsite.com`, le cookie du service d’ID est défini par le serveur de collecte de données. Cela est autorisé dans la mesure où le domaine du serveur de collecte de données correspond à celui du site Web. C’est ce que l’on désigne sous le nom d’utilisation d’un *contexte propriétaire* ou plus simplement de *cookie propriétaire*.

Si vous utilisez le même serveur de collecte de données sur d’autres sites (`myothersiteA.com` et `myothersiteB.com` par exemple), et qu’un visiteur se rend ultérieurement sur ces sites, le cookie qui avait été défini au cours de la visite de `mymainsite.com` est envoyé dans la demande HTTPS adressée au serveur de collecte de données (pour rappel, les navigateurs envoient tous les cookies d’un domaine avec l’ensemble des demandes HTTPS adressées à ce domaine, même si ce dernier ne correspond pas au domaine du site Web en cours). On parle, dans ce cas, d’utilisation d’un *contexte tiers* ou plus simplement de *cookie tiers*. Cela permet de réutiliser le même identifiant visiteur sur ces autres domaines. Notez que les navigateurs gèrent les cookies dans des contextes tiers différents des cookies propriétaires.

*Remarque : Safari bloque tous les cookies dans le contexte tiers, quelle que soit la manière dont ils sont définis.*

Par conséquent, pour qu’un visiteur soit identifié entre plusieurs domaines, votre domaine de collecte doit être un domaine que les utilisateurs visitent couramment. En l’absence de domaine *courant* à utiliser comme domaine de collecte de données, la gestion d’un enregistrement CNAME ne présente aucun avantage sur le plan inter-domaines. Si le site d’accès principal n’est pas le premier site visité, les visiteurs sont identifiés différemment sur le site secondaire et sur le site principal.

## Activation de la prise en charge de la collecte de données propriétaires (CNAME) avec le service Experience Cloud ID {#section-25d4feb686d944e3a877d7aad8dbdf9a}

Pour activer la prise en charge du CNAME du serveur de collecte de données, définissez les `visitor.marketingCloudServerSecure` variables.
