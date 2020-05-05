---
description: 'null'
keywords: order of operations;ID Service
seo-description: valeur nulle
seo-title: CNAME de collecte de données et suivi inter-domaines
title: CNAME de collecte de données et suivi inter-domaines
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: 9fe63cf3983a2ed6642837b02a3c3441ef745d70

---


# CNAME de collecte de données et suivi inter-domaines {#data-collection-cnames-and-cross-domain-tracking}

Si vous disposez d’un site d’entrée principal sur lequel les clients peuvent être identifiés avant de se rendre sur d’autres domaines, un CNAME peut activer le suivi inter-domaines dans les navigateurs qui n’acceptent pas les cookies tiers (tels que Safari).

Dans les navigateurs qui acceptent les cookies tiers, un cookie est défini par les serveurs de collecte de données lors de la demande d’un ID de visiteur. Ce cookie permet au service d’identification des visiteurs de renvoyer le même ID de visiteur Experience Cloud sur tous les domaines qui sont configurés à l’aide du même ID d’organisation Experience Cloud.

Dans les navigateurs qui rejettent les cookies tiers, un nouvel ID de visiteur Experience Cloud est attribué pour chaque domaine.

Le cookie demdex.net permet au service d’identification des visiteurs de fournir le même niveau de suivi inter-domaines que le cookie s_vi dans Analytics, où le cookie est accepté dans certains navigateurs et utilisé sur plusieurs domaines, mais rejeté par d’autres navigateurs.

## CNAME de collecte de données {#section-48fd186d376a48079769d12c4bd9f317}

Lorsque le cookie Analytics a été défini par le serveur de collecte de données, de nombreux clients ont configuré les enregistrements CNAME du serveur de collecte de données dans le cadre d’une [mise en œuvre de cookie propriétaire](https://docs.adobe.com/content/help/fr-FR/core-services/interface/ec-cookies/cookies-first-party.html) afin d’éviter des problèmes éventuels avec les navigateurs qui rejettent les cookies tiers. Ce processus configure votre domaine de serveur de collecte de données pour qu’il corresponde à votre domaine de site Web, de sorte que le cookie ID de visiteur soit défini comme cookie propriétaire.

Puisque le service d’identification des visiteurs définit le cookie visiteur directement sur le domaine du site Web en cours à l’aide de JavaScript, cette configuration n’est plus nécessaire pour définir des cookies propriétaires.

Les clients qui disposent d’une propriété Web unique (un seul domaine) peuvent migrer en dehors des CNAME de collecte de données et utiliser plutôt leur nom d’hôte de collecte de données par défaut (`omtrdc.net` ou `2o7.net`).

Toutefois, l’utilisation d’un CNAME pour la collecte de données vous permet par ailleurs d’effectuer un suivi sur les visiteurs entre un domaine d’entrée principal et d’autres domaines dans les navigateurs qui n’acceptent pas les cookies tiers. Les clients qui disposent de plusieurs propriétés Web (plusieurs domaines) peuvent avoir intérêt à préserver un CNAME de collecte de données. La section suivante explique comment fonctionne le suivi entre visiteurs de domaines.

## Suivi entre domaines {#section-78925af798e24917b9abed79de290ad9}

Le service d’identification des visiteurs utilise demdex.net comme domaine pour le suivi des visiteurs entre domaines (mais dans la même société de propriété) si les paramètres de confidentialité et de navigateur de l’utilisateur le permettent.

Un CNAME ne fournit pas d’avantages interdomaines supplémentaires. Supposons que votre site principal se situe à l’adresse `mymainsite.com`. Vous avez configuré l’enregistrement CNAME pour pointer vers votre serveur de collecte de données sécurisé : `smetrics.mymainsite.com`.

Lorsqu’un visiteur se rend sur le site `mymainsite.com`, le cookie du service d’ID est défini par le serveur de collecte de données. Cela est autorisé dans la mesure où le domaine du serveur de collecte de données correspond à celui du site Web. C’est ce que l’on désigne sous le nom d’utilisation d’un *contexte propriétaire* ou plus simplement de *cookie propriétaire*.

Si vous utilisez le même serveur de collecte de données sur d’autres sites (`myothersiteA.com` et `myothersiteB.com` par exemple), et qu’un visiteur se rend ultérieurement sur ces sites, le cookie qui avait été défini au cours de la visite de `mymainsite.com` est envoyé dans la demande HTTPS adressée au serveur de collecte de données (pour rappel, les navigateurs envoient tous les cookies d’un domaine avec l’ensemble des demandes HTTPS adressées à ce domaine, même si ce dernier ne correspond pas au domaine du site Web en cours). Il s’agit de ce que l’on appelle l’utilisation d’un cookie dans un contexte ** tiers ou simplement d’un cookie ** tiers, même si vous utilisez un CNAME. Adobe recommande un CNAME pour chaque domaine unique.

*Remarque : Safari bloque tous les cookies dans le contexte tiers, quelle que soit la manière dont ils sont définis.*

## Activation de la prise en charge de la collecte de données propriétaires (CNAME) avec le service Experience Cloud Identity {#section-25d4feb686d944e3a877d7aad8dbdf9a}

Pour activer la prise en charge du CNAME du serveur de collecte de données, définissez les variables `visitor.marketingCloudServerSecure`.
