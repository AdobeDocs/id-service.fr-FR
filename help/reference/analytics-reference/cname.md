---
description: Si vous disposez d’un site d’accès principal où les clients peuvent être identifiés avant de se rendre sur d’autres domaines, un CNAME peut activer le suivi inter-domaines dans les navigateurs qui n’acceptent pas les cookies tiers (comme Safari).
keywords: ordre des opérations ; service d’ID
title: Présentation de l’implémentation CNAME
exl-id: f95dda3c-7bb2-4c7d-a25a-a4d20b58fe27
source-git-commit: d2586fc722be25df1b82caaf2cc6de6a2a6c31bf
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 100%

---

# Présentation de l’implémentation CNAME {#cname-implementation-overview}

Les implémentations CNAME vous permettent de personnaliser le domaine de collecte utilisé par Adobe afin qu’il corresponde au vôtre. Ces domaines sont également appelés domaines de collecte propriétaires. Ces implémentations permettent à Adobe de définir des cookies propriétaires côté serveur au lieu du côté client à lʼaide de JavaScript. Auparavant, ces cookies internes côté serveur n’étaient pas soumis aux limites imposées par la politique ITP (Intelligent Tracking Prevention) d’Apple. Cependant, en novembre 2020, [!DNL Apple] a mis à jour ses politiques afin que ces restrictions soient également appliquées aux cookies définis via CNAME. Actuellement, tant les cookies définis côté serveur via CNAME que les cookies définis côté client via JavaScript sont limités à une durée de vie de sept jours ou 24 heures en vertu de la politique ITP. Pour plus d’informations sur la politique ITP, consultez ce document [!DNL Apple] traitant de la [prévention du suivi](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp).

Bien quʼune implémentation CNAME ne permette pas dʼallonger la durée de vie des cookies, elle offre dʼautres avantages. Parmi ceux-ci, citons les bloqueurs de publicités et les navigateurs moins utilisés qui empêchent lʼenvoi des données aux domaines quʼils considèrent être des dispositifs de suivi. Dans ce cas, lʼutilisation dʼun CNAME peut éviter que votre collecte de données ne soit interrompue pour les utilisateurs qui se servent de ces outils.

En outre, les implémentations CNAME vous permettent de [choisir un type de collecte de données régionales personnalisé](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html?lang=fr), qui détermine où les accès des utilisateurs sont initialement dirigés. La plupart des clients nʼutilisent pas de type de collecte de données régionales personnalisé.
