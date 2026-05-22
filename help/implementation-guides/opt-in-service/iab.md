---
description: Connectez leur plateforme de gestion du consentement (CMP) à l’aide du plug-in Opt-in Audience Manager pour IAB Transparency and Consent Framework (TCF).
title: Utilisation des services Opt-in avec un framework IAB
exl-id: 9ac9b232-0797-4e77-a611-9cf5d17a5cb7
TQID: https://experienceleague.adobe.com/70QH1BoRSSbiw7cMfRjrHmiSxQLbuiHcWAG5b-xVOLw
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 518
ht-degree: 96%

---

# Utilisation des services Opt-in avec un framework IAB{#using-opt-in-services-with-iab-framework}

>[!IMPORTANT]
>
>Le document suivant s’applique uniquement à IAB 2.0. Les utilisateurs doivent utiliser Visitor.js version 5.0 pour utiliser IAB 2.0.

Connectez la plateforme de gestion du consentement (CMP) au plug-in TCF (Transparency and Consent Framework) de l’IAB de l’Opt-in.

Les clients Adobe Audience Manager qui utilisent le [IAB TCF](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) peuvent connecter leur plateforme de gestion du consentement (CMP) à un plug-in IAB TCF de l’Opt-in. L’Opt-in est une fonctionnalité intégrée à la bibliothèque JavaScript ECID. Elle peut désactiver les bibliothèques individuelles des solutions Adobe en fonction des préférences du visiteur, définies sur une CMP. Lorsque le plug-in IAB TCF est mis en œuvre avec la bibliothèque d’ECID, les préférences du visiteur de votre CMP prenant en charge IAB TCF sont automatiquement associées à Opt-in. Ces préférences activent les bibliothèques basées sur Audience Manager (DIL et ECID) et les appels associés lors de la réception du consentement.

## Implémenter une CMP qui prend en charge IAB {#section-9fd2403b548947dbb1921ac6ff9d0c82}

Pour intégrer Opt-in à IAB TCF, vous devez effectuer les opérations suivantes :

1. Implémentez une CMP prenant en charge IAB et enregistrée comme fournisseur d’IAB ou développez une CMP interne qui met en œuvre les spécifications d’IAB TCF et enregistrez-la comme CMP IAB TCF.
1. définir ou charger `__tcfapi` avant de charger le JavaScript Adobe.

Pour plus de détails, lisez les [documents d’Interactive Advertising Bureau](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/TCFv2/TCF-Implementation-Guidelines.md).

## Activer le plug-in IAB TCF d’Opt-in dans votre bibliothèque JavaScript d’ECID {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>Opt-in est disponible uniquement dans ECID 4.0+.

Utilisez Adobe Experience Platform Launch pour mettre en œuvre le plug-in IAB TCF de l’Opt-in pour votre site. Lors de l’activation manuelle d’IAB pour Opt-in, vérifiez que les paramètres suivants sont définis sur true dans l’objet Visiteur :

```javascript
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,
  isIabContext: true
});
```

Une fois les paramètres correctement configurés, les bibliothèques ECID et DIL seront activées/désactivées selon les critères de consentement d’une CMP et d’IAB TCF.

>[!IMPORTANT]
>
>Audience Manager nécessite un consentement pour les *points 1 et 10, ainsi que le consentement du fournisseur*, afin de déployer des cookies et lancer ou honorer les synchronisations d’ID. Pour en savoir plus sur le plug-in IAB TCF de l’Opt-in, consultez la documentation Audience Manager, [ici](https://experienceleague.adobe.com/docs/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html?lang=fr).

Pour plus d’informations sur la façon de valider le plug-in IAB TCF de l’Opt-in, référez-vous au cas d’utilisation 4 du guide de validation, [ici](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Documentation connexe {#section-55da1110051a4b39b1037803f4a7b264}

* [Transparency and Consent Framework (TCF) de l’IAB](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - Pour plus d’informations sur le standard IAB
* [Adobe Opt-in](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - Pour plus d’informations sur Opt-in, un composant nécessaire aux solutions de plateforme de gestion de contenu
* Prise en charge du Transparency and Consent Framework (TCF) de l’IAB [dans Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html?lang=fr)
* [Vos choix en matière de traitement de vos données personnelles](https://www.adobe.com/fr/privacy/opt-out.html#customeruse) - Une autre option de confidentialité à la disposition de vos utilisateurs est la capacité à se désabonner de toute collecte de données grâce à d’autres outils d’opt-out global. L’opt-out global a la priorité sur l’opt-in et la vérification IAB TCF.

