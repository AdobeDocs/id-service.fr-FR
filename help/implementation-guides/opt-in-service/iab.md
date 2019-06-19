---
description: Connectez leur plateforme de gestion de l'approbation (CMP) à l'aide du module externe IAB de souscription.
seo-description: Connectez leur plateforme de gestion de l'approbation (CMP) à l'aide du module externe IAB de souscription.
seo-title: (bêta) Utilisation des services de souscription avec la structure IAB
title: (bêta) Utilisation des services de souscription avec la structure IAB
uuid: 8 df 39 d 9 c-c 016-490 e-b 4 db-d 02 e 4044 b 480
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# (bêta) Utilisation des services de souscription avec la structure IAB{#beta-using-opt-in-services-with-iab-framework}

Connectez leur plateforme de gestion de l&#39;approbation (CMP) à l&#39;aide du module externe IAB de souscription.

Les clients Audience Manager qui utilisent [la structure de transparence et le cadre de consentement IAB (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) peuvent connecter leur plateforme de gestion de l&#39;autorisation (CMP) à l&#39;aide du module externe IAB de souscription. La souscription est une fonctionnalité incorporée dans la bibliothèque JavaScript ECID qui peut désactiver les bibliothèques de solutions Adobe individuelles en fonction des préférences du visiteur définies dans un CMP. Lorsque le module IAB est implémenté avec la bibliothèque ECID, les préférences du visiteur issues de votre CMP compatible IAB sont automatiquement mappées à la souscription. Ces préférences activent les bibliothèques basées sur Audience Manager (DIL et ECID) et les appels associés lors de la réception du consentement.

## Mise en œuvre d’une CMP qui prend en charge l’IAB {#section-9fd2403b548947dbb1921ac6ff9d0c82}

Pour intégrer Opt-in au consentement de l’IAB, vous devez :

1. mettre en œuvre une CMP prenant en charge l’IAB et [enregistrée comme fournisseur d’IAB](https://vendorlist.consensu.org/vendorlist.json), ou développer une CMP interne qui mette en œuvre les spécifications d’IAB et l’enregistrer comme CMP auprès d’IAB Europe ;
1. Définissez/chargez le `__cmp` fichier avant de charger le fichier JS Adobe.

Pour plus de détails, lisez les [documents d’Interactive Advertising Bureau](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md).

## Activation du module IAB dans votre bibliothèque JavaScript d’ECID {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>La souscription n&#39;est disponible que dans ECID 4.0 +

Utilisez Adobe Launch pour mettre en œuvre Opt-in et le module IAB pour votre site. Lisez la [documentation de l’extension Opt-in d’ECID](https://marketing-beta.adobe.com/resources/help/launch/ecid-optin/) pour apprendre à configurer l’extension Launch.

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
>Audience Manager nécessite un consentement pour les *points 1, 2 et 5, ainsi que du consentement du fournisseur*, afin de déployer des cookies et lancer ou honorer les synchronisations d’ID. Pour plus d&#39;informations sur le module externe IAB dans la documentation d&#39;Audience Manager** [ici](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html)**.

Pour plus d’informations sur la façon de valider à la fois Opt-in et le module IAB, référez-vous au cas d’utilisation 4 du guide de validation, [**ici** ](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Documentation connexe {#section-55da1110051a4b39b1037803f4a7b264}

* [Transparency and Consent Framework (TCF) de l’IAB](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - Pour plus d’informations sur le standard IAB
* [Adobe Opt-in](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - Pour plus d’informations sur Opt-in, un composant nécessaire aux solutions de plate-forme de gestion de contenu
* Prise en charge de Transparency and Consent Framework (TCF) de l’IAB [dans Audience Manager](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html).
* [Vos choix en matière de traitement de vos données personnelles](https://www.adobe.com/privacy/opt-out.html#customeruse) - Une autre option de confidentialité à la disposition de vos utilisateurs est la capacité à se désabonner de toute collecte de données grâce à d’autres outils d’opt-out global. L’opt-out global a la priorité sur l’opt-in et la vérification IAB.

