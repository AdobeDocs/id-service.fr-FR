---
description: Connecter leur plateforme de gestion du consentement (CMP) à l’aide du module Opt-in externe Audience Manager pour IAB Transparency and Consent Framework (TCF).
seo-description: Connecter leur plateforme de gestion du consentement (CMP) à l’aide du module externe Audience Manager pour IAB Transparency and Consent Framework (TCF).
seo-title: Utilisation des services Opt-in avec un framework IAB
title: Utilisation des services Opt-in avec un framework IAB
uuid: 8df39d9c-c016-490e-b4db-d02e4044b480
translation-type: ht
source-git-commit: bb61c33491cb67795d58575c5dca5fa2ba4c372f
workflow-type: ht
source-wordcount: '502'
ht-degree: 100%

---


# Utilisation des services Opt-in avec un framework IAB {#using-opt-in-services-with-iab-framework}

Connectez la plateforme de gestion du consentement (CMP) à l’aide du module Opt-in externe Audience Manager pour IAB TCF.

Les clients d’Audience Manager qui utilisent [IAB Transparency and Consent Framework (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) peuvent connecter leur plateforme de gestion du consentement (CMP) au module Opt-in Audience Manager pour IAB TCF. L’Opt-in est une fonctionnalité intégrée à la bibliothèque JavaScript ECID. Elle peut désactiver les bibliothèques individuelles des solutions Adobe en fonction des préférences du visiteur, définies sur une CMP. Lorsque le module Audience Manager pour IAB TCF est mis en œuvre avec la bibliothèque d’ECID, les préférences du visiteur de votre CMP prenant en charge IAB TCF sont automatiquement associées à Opt-in. Ces préférences activent les bibliothèques basées sur Audience Manager (DIL et ECID) et les appels associés lors de la réception du consentement.

## Mise en œuvre d’une CMP qui prend en charge l’IAB {#section-9fd2403b548947dbb1921ac6ff9d0c82}

Pour intégrer Opt-in à IAB TCF, vous devez :

1. mettre en œuvre une CMP prenant en charge IAB et [enregistrée comme fournisseur d’IAB](https://vendorlist.consensu.org/vendorlist.json), ou développer une CMP interne qui mette en œuvre les spécifications d’IAB TCF et l’enregistrer comme CMP auprès d’IAB TCF.
1. définir ou charger `__cmp` avant de charger le JavaScript Adobe.

Pour plus de détails, lisez les [documents d’Interactive Advertising Bureau](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md).

## Activez le module externe Audience Manager pour IAB TCF dans votre bibliothèque Javascript ECID {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>Opt-in est disponible uniquement dans ECID 4.0+.

Utilisez Adobe Experience Platform Launch pour mettre en œuvre Opt-in et le module Audience Manager pour IAB TCF pour votre site. Lors de l’activation manuelle d’IAB pour Opt-in, vérifiez que les paramètres suivants sont définis sur true dans l’objet Visiteur :

```
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,   
  isIabContext: true   
});
```

Une fois les paramètres correctement configurés, les bibliothèques ECID et DIL seront activées/désactivées selon les critères de consentement d’une CMP et d’IAB TCF.

>[!IMPORTANT]
>
>Audience Manager nécessite un consentement pour les *points 1 et 10, ainsi que le consentement du fournisseur*, afin de déployer des cookies et lancer ou honorer les synchronisations d’ID. Pour en savoir plus sur le module externe Audience Manager pour IAB TCF, consultez la documentation d’Audience Manager [ici](https://docs.adobe.com/content/help/fr-FR/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html).

Pour plus d’informations sur la façon de valider à la fois Opt-in et le module Audience Manager pour IAB TCF, référez-vous au cas d’utilisation 4 du guide de validation, [ici](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Documentation connexe {#section-55da1110051a4b39b1037803f4a7b264}

* [Transparency and Consent Framework (TCF) de l’IAB](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - Pour plus d’informations sur le standard IAB
* [Adobe Opt-in](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - Pour plus d’informations sur Opt-in, un composant nécessaire aux solutions de plate-forme de gestion de contenu
* Prise en charge du Transparency and Consent Framework (TCF) de l’IAB [dans Audience Manager](https://docs.adobe.com/content/help/fr-FR/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.translate.html)
* [Vos choix en matière de traitement de vos données personnelles](https://www.adobe.com/fr/privacy/opt-out.html#customeruse) - Une autre option de confidentialité à la disposition de vos utilisateurs est la capacité à se désabonner de toute collecte de données grâce à d’autres outils d’opt-out global. L’opt-out global a la priorité sur l’opt-in et la vérification IAB TCF.

