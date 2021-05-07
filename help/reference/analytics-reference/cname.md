---
description: Si vous disposez d’un site d’accès principal où les clients peuvent être identifiés avant de se rendre sur d’autres domaines, un CNAME peut activer le suivi inter-domaines dans les navigateurs qui n’acceptent pas les cookies tiers (comme Safari).
keywords: ordre des opérations ; service d’ID
seo-description: Si vous disposez d’un site d’accès principal où les clients peuvent être identifiés avant de se rendre sur d’autres domaines, un CNAME peut activer le suivi inter-domaines dans les navigateurs qui n’acceptent pas les cookies tiers (comme Safari).
seo-title: Présentation de la mise en oeuvre CNAME
title: Présentation de la mise en oeuvre CNAME
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: ebeca9e285af71872c05d58ba252ca65bde24f3d
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 28%

---


# Présentation de l’implémentation CNAME{#cname-implementation-overview}

Les implémentations CNAME vous permettent de personnaliser le domaine de collecte utilisé par l’Adobe afin qu’il corresponde à votre propre domaine. Cela permet à l’Adobe de définir des cookies propriétaires côté serveur plutôt que côté client à l’aide de JavaScript. Auparavant, ces cookies propriétaires côté serveur n’étaient pas soumis aux limites imposées par la politique ITP (Intelligent Tracking Prevention) d’Apple. Cependant, en novembre 2020, [!DNL Apple] a mis à jour leurs stratégies afin que ces limitations soient également appliquées aux cookies définis via CNAME. Actuellement, les deux cookies définis côté serveur via CNAME et les cookies définis côté client via Javascript sont limités à une expiration de sept jours ou 24 heures sous ITP. Pour plus d&#39;informations sur la politique du PTI, consultez le [!DNL Apple] document [sur la prévention du suivi](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp).

Bien qu’une implémentation CNAME ne présente aucun avantage en termes de durée de vie des cookies, d’autres avantages peuvent être associés, tels que le blocage des publicités et les navigateurs moins courants, qui empêchent l’envoi de données vers des domaines qu’ils classent comme suivis. Dans ces cas, l’utilisation d’un CNAME peut empêcher que votre collecte de données ne soit perturbée pour les utilisateurs qui utilisent ces outils.