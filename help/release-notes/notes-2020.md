---
description: Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service d’identités d’Experience Cloud.
keywords: Service d’ID
title: Notes de mise à jour 2020
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
TQID: https://experienceleague.adobe.com/hqAMIyXTeLBPU-4B6AVRXhcWux3bkyViMCrbjoGiRwk
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 216
ht-degree: 91%

---

# Notes de mise à jour d’Experience Cloud - 2020 {#release-notes}

Description des nouvelles fonctionnalités, des mises à jour et des modifications apportées au service d’identités d’Experience Cloud.

## Version 5.1.1

* Correctif pour la définition du cookie AMCV avec `SameSite=None` lorsque VisitorJS est chargé dans un iFrame.

## Version 5.1.0

* Ajout de la configuration `sameSiteCookie` pour spécifier l’attribut `SameSite` du cookie AMCV. Cette configuration prend en charge les valeurs suivantes pour l’attribut `SameSite` :
   * `Strict`
   * `Lax`
   * `None`

Pour plus d’informations sur ces valeurs d’attribut, voir [web.dev](https://web.dev/samesite-cookies-explained/) et [Mises à jour de SameSite par The Chromium Projects](https://www.chromium.org/updates/same-site/).

## Version 5.0.1

* Correctif pour l’inclusion de l’indicateur `d_cf` lorsqu’une nouvelle chaîne de consentement IAB est envoyée aux périphéries de la collecte de données d’Adobe.

## Version 5.0.0

* Version 5.0.0 de Visitor avec prise en charge de `IAB 2.0`.

## Version 4.6

* L’indicateur `loadSSL` est activé par défaut. Tous les appels au service d’identités seront par défaut en `https`.  Les clients peuvent définir ce paramètre sur false s’ils souhaitent appeler le service d’identités en HTTP à partir de leurs `non-ssl` pages.
* Mise à jour de la fonction utilisée pour détecter `Internet-Explorer (IE)` version, afin de résoudre un problème signalé par `ESLint`.
Correction d’un problème de performances sur `Internet-Explorer (IE) 11` lorsque l’ECID reçoit une `pre-approval` d’opt-in et est mis à jour ultérieurement.

## Version 4.5

* À partir de la version 4.5, ECID rejettera les identifiants vides envoyés à la méthode `setCustomerIDs`.
* Correction d’un problème survenant lorsque l’inclusion était configurée sur `doesOptInApply=false` et `isIabContext=true`.

Pour consulter les notes de mise à jour mensuelles de tous les produits, reportez-vous aux [Notes de mise à jour Experience Cloud](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=fr).

