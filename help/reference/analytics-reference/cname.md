---
description: Si vous disposez d’un site d’accès principal où les clients peuvent être identifiés avant de se rendre sur d’autres domaines, un CNAME peut activer le suivi inter-domaines dans les navigateurs qui n’acceptent pas les cookies tiers (comme Safari).
keywords: ordre des opérations ; service d’ID
seo-description: Si vous disposez d’un site d’accès principal où les clients peuvent être identifiés avant de se rendre sur d’autres domaines, un CNAME peut activer le suivi inter-domaines dans les navigateurs qui n’acceptent pas les cookies tiers (comme Safari).
seo-title: Présentation de l’implémentation CNAME
title: Présentation de l’implémentation CNAME
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: ht
source-git-commit: ebeca9e285af71872c05d58ba252ca65bde24f3d
workflow-type: ht
source-wordcount: '259'
ht-degree: 100%

---


# Présentation de l’implémentation CNAME {#cname-implementation-overview}

Les implémentations CNAME vous permettent de personnaliser le domaine de collecte utilisé par Adobe afin qu’il corresponde au vôtre. Cela permet à Adobe de définir des cookies internes côté serveur plutôt que côté client à l’aide de JavaScript. Auparavant, ces cookies internes côté serveur n’étaient pas soumis aux limites imposées par la politique ITP (Intelligent Tracking Prevention) d’Apple. Cependant, en novembre 2020, [!DNL Apple] a mis à jour ses stratégies afin que ces restrictions soient également appliquées aux cookies définis via CNAME. Actuellement, tant les cookies définis côté serveur via CNAME que les cookies définis côté client via JavaScript sont limités à une durée de vie de sept jours ou 24 heures en vertu de la politique ITP. Pour plus d’informations sur la politique ITP, consultez ce document [!DNL Apple] traitant de la [prévention du suivi](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp).

Bien qu’une implémentation CNAME ne présente aucun avantage en termes de durée de vie des cookies, d’autres avantages peuvent y être associés, comme des bloqueurs de publicité et des navigateurs moins courants qui empêchent l’envoi de données vers des domaines qu’ils considèrent comme des dispositifs de suivi (ou traceurs). Dans ce cas, l’utilisation d’un CNAME peut éviter que votre collecte de données ne soit interrompue pour les utilisateurs qui se servent de ces outils.