---
description: Connectez leur plateforme de gestion du consentement (CMP) au module externe Audience Manager de l’inclusion pour la structure de transparence et de consentement IAB (TCF).
seo-description: Connectez leur plateforme de gestion du consentement (CMP) au module externe Audience Manager pour la structure de transparence et de consentement IAB (TCF).
seo-title: Utilisation des services Opt-in avec un framework IAB (bêta)
title: Utilisation des services Opt-in avec un framework IAB (bêta)
uuid: 8df39d9c-c016-490e-b4db-d02e4044b480
translation-type: tm+mt
source-git-commit: cb75ac6a9d7a5a001fcb0a1d9d978d3845a4e829

---


# Utilisation des services Opt-in avec un framework IAB (bêta){#beta-using-opt-in-services-with-iab-framework}

Connectez leur plateforme de gestion de contenu (CMP) au module externe IAB d’inclusion d’Audience Manager.

Les clients d’Audience Manager qui utilisent [IAB Transparency and Consent Framework (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) peuvent connecter leur plateforme de gestion du consentement (CMP) au module externe Audience Manager pour IAB TCF. L’Opt-in est une fonctionnalité intégrée à la bibliothèque JavaScript ECID. Elle peut désactiver les bibliothèques individuelles des solutions Adobe en fonction des préférences du visiteur, définies sur une CMP. Lorsque le module IAB est mis en œuvre avec la bibliothèque d’ECID, les préférences du visiteur de votre CMP conforme aux normes IAB sont automatiquement associées à Opt-in. Ces préférences activent les bibliothèques basées sur Audience Manager (DIL et ECID) et les appels associés lors de la réception du consentement.

## Mise en œuvre d’une CMP qui prend en charge l’IAB {#section-9fd2403b548947dbb1921ac6ff9d0c82}

Pour intégrer Opt-in au consentement de l’IAB, vous devez :

1. mettre en œuvre une CMP prenant en charge l’IAB et [enregistrée comme fournisseur d’IAB](https://vendorlist.consensu.org/vendorlist.json), ou développer une CMP interne qui mette en œuvre les spécifications d’IAB et l’enregistrer comme CMP auprès d’IAB Europe ;
1. définir ou charger `__cmp` avant de charger le JavaScript Adobe.

Pour plus de détails, lisez les [documents d’Interactive Advertising Bureau](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md).

## Activation du module IAB dans votre bibliothèque JavaScript d’ECID {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>Opt-in est disponible uniquement dans ECID 4.0+

Utilisez Adobe Experience Platform Launch pour mettre en œuvre Opt-in et le module IAB pour votre site. Read the [documentation for the ECID Opt-in extension](https://marketing-beta.adobe.com/resources/help/launch/ecid-optin/) to learn how to set up the Experience Platform Launch extension.

Lorsque vous activez manuellement IAB pour Opt-in, assurez-vous que les paramètres suivants sont définis sur « true » dans l’objet Visiteur :

```
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,   
  isIabContext: true   
});
```

Une fois les paramètres correctement configurés, les bibliothèques ECID et DIL sont activées ou désactivées en fonction des critères de consentement de la CMP et du framework IAB.

>[!IMPORTANT]
>
>Audience Manager nécessite un consentement pour les *points 1, 2 et 5, ainsi que du consentement du fournisseur*, afin de déployer des cookies et lancer ou honorer les synchronisations d’ID. Pour en savoir plus sur le module IAB, consultez la documentation Audience Manager, [ici](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html).

Pour plus d’informations sur la façon de valider à la fois Opt-in et le module IAB, référez-vous au cas d’utilisation 4 du guide de validation, [ici](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Documentation connexe {#section-55da1110051a4b39b1037803f4a7b264}

* [Transparency and Consent Framework (TCF) de l’IAB](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - Pour plus d’informations sur le standard IAB
* [Adobe Opt-in](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - Pour plus d’informations sur Opt-in, un composant nécessaire aux solutions de plate-forme de gestion de contenu
* Prise en charge de Transparency and Consent Framework (TCF) de l’IAB [dans Audience Manager](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html).
* [Vos choix en matière de traitement de vos données personnelles](https://www.adobe.com/privacy/opt-out.html#customeruse) - Une autre option de confidentialité à la disposition de vos utilisateurs est la capacité à se désabonner de toute collecte de données grâce à d’autres outils d’opt-out global. L’opt-out global a la priorité sur l’opt-in et la vérification IAB.

