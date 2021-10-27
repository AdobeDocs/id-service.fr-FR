---
description: Si vous disposez d’un site d’accès principal où les clients peuvent être identifiés avant de se rendre sur d’autres domaines, un CNAME peut activer le suivi inter-domaines dans les navigateurs qui n’acceptent pas les cookies tiers (comme Safari).
keywords: ordre des opérations ; service d’ID
title: Présentation de l’implémentation CNAME
exl-id: f95dda3c-7bb2-4c7d-a25a-a4d20b58fe27
source-git-commit: 61f9f1888430ff0fdbb90a8cf6561bf23d204a45
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 45%

---

# Présentation de l’implémentation CNAME{#cname-implementation-overview}

Les implémentations CNAME vous permettent de personnaliser le domaine de collecte utilisé par Adobe afin qu’il corresponde au vôtre. Ces domaines sont également appelés domaines de collecte propriétaires. Ces mises en oeuvre permettent à Adobe de définir des cookies propriétaires côté serveur au lieu du côté client à l’aide de JavaScript. Auparavant, ces cookies internes côté serveur n’étaient pas soumis aux limites imposées par la politique ITP (Intelligent Tracking Prevention) d’Apple. Cependant, en novembre 2020, [!DNL Apple] a mis à jour ses stratégies afin que ces restrictions soient également appliquées aux cookies définis via CNAME. Actuellement, les deux cookies définis côté serveur via CNAME et côté client via Javascript sont limités à un délai d’expiration de sept jours ou 24 heures sous ITP. Pour plus d’informations sur la politique ITP, consultez ce document [!DNL Apple] traitant de la [prévention du suivi](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp).

Bien qu’une mise en oeuvre CNAME ne fournisse aucun avantage en termes de durée de vie des cookies, il peut y avoir d’autres avantages. Ces avantages incluent les bloqueurs d’annonces et les navigateurs moins courants qui empêchent l’envoi de données aux domaines qu’ils classent comme outils de suivi. Dans ce cas, l’utilisation d’un CNAME peut empêcher que votre collecte de données ne soit interrompue pour les utilisateurs qui utilisent ces outils.

En outre, les implémentations CNAME vous permettent de spécifier **[!UICONTROL Choisir le type de collecte de données régionale personnalisé]** qui contrôle l’emplacement où les accès des utilisateurs sont initialement acheminés. La plupart des clients n’utilisent pas de types de collecte de données régionale personnalisés.
