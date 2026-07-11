---
audience: end-user
user-guide-title: Aide du service d’identification des visiteurs Adobe
breadcrumb-title: Guide du service d’identification des visiteurs
user-guide-description: Le service d’identification des visiteurs d’Adobe fournit un identifiant universel et persistant qui identifie vos visiteurs dans toutes les solutions de l’expérience client. Il permet de remplacer le code de génération d’ID hérité pour les solutions et services d’entreprise CX.
user-guide-url: /content/help/en/id-service/using/home.html
source-git-commit: 7621dc8925235bd3cf159a404741bd02fc9b6a77
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 45%

---


# Aide du service d’identification des visiteurs Adobe {#using}

+ [Aide du service d’identification des visiteurs](home.md)
+ Vue d’ensemble {#intro}
   + [Vue d’ensemble](introduction/overview.md)
   + [À propos du service d’identification des visiteurs](introduction/about-id-service.md)
   + [Cookies et service d’identification des visiteurs](introduction/cookies.md)
   + [Requête et définition d’ID par le service d’identification des visiteurs](introduction/id-request.md)
   + [Comprendre la synchronisation et les taux de correspondance](introduction/match-rates.md)
+ Mise en œuvre {#implementation}
   + [Méthodes de mise en œuvre](implementation-guides/implementation-methods.md)
   + [Guides de mise en œuvre](implementation-guides/implementation-guides.md)
   + [Implémentation avec des balises](implementation-guides/ecid-implement-with-launch.md)
   + [Implémentation pour Analytics](https://experienceleague.adobe.com/en/docs/analytics/implementation/id/overview){target=_blank}
   + [Implémentation pour Target](implementation-guides/setup-target.md)
   + [Implémentation pour Analytics et Audience Manager](implementation-guides/setup-aam-analytics.md)
   + [Implémentation pour Analytics, Audience Manager et Target](implementation-guides/setup-aam-analytics-target.md)
   + [Utilisation du service d’identification des visiteurs avec A4T et une implémentation côté serveur de Target](implementation-guides/ecid-a4t-target.md)
   + [Intégration directe au service d’identification des visiteurs](implementation-guides/direct-integration.md)
   + [Cas d’utilisation de l’intégration directe](implementation-guides/direct-integration-examples.md)
   + [Test et vérification du service d’identification des visiteurs](implementation-guides/test-verify.md)
   + Service Opt-in {#opt-in-service}
      + [Aperçu du service Opt-in](implementation-guides/opt-in-service/optin-overview.md)
      + [Configuration du service Opt-in](implementation-guides/opt-in-service/getting-started.md)
      + [Validation du service Opt-in](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Configuration d’Opt-in avec des balises](implementation-guides/opt-in-service/launch.md)
      + [Contrôlez les activités CX Enterprise en fonction du consentement de l’utilisateur](implementation-guides/opt-in-service/use-opt-in-to-control-experience-cloud-activities-based-on-user-consent.md)
      + [Cas d’utilisation d’Opt-in](implementation-guides/opt-in-service/use-cases.md)
      + [Références d’Opt-in](implementation-guides/opt-in-service/api.md)
      + [Utilisation des services Opt-in avec un framework IAB](implementation-guides/opt-in-service/iab.md)
+ API du service d’identification des visiteurs {#id-service-api}
   + [Présentation de l’API du service d’identification des visiteurs](library/library.md)
   + Configuration {#configurations}
      + [Présentation des configurations](library/function-vars/function-vars.md)
      + [audienceManagerServer et audienceManagerServerSecure](library/function-vars/subdomain-config.md)
      + [cookieDomain](library/function-vars/cookiedomain.md)
      + [cookieLifetime](library/function-vars/cookielifetime.md)
      + [disableIdSyncs](library/function-vars/disableidsync.md)
      + [disableThirdPartyCalls](library/function-vars/disablethirdpartycalls.md)
      + [disableThirdPartyCookies](library/function-vars/disable-cookies.md)
      + [idSyncAttachIframeOnWindowLoad](library/function-vars/idsyncattachiframeonwindowload.md)
      + [idSyncContainerID](library/function-vars/idsyncontainerid.md)
      + [idSyncSSLUseAkamai](library/function-vars/idsyncssluseakamai.md)
      + [loadTimeout](library/function-vars/loadtimeout.md)
      + [overwriteCrossDomainMCIDAndAID](library/function-vars/overwrite-visitor-id.md)
      + [resetBeforeVersion](library/function-vars/resetbeforeversion.md)
      + [sdidParamExpiry](library/function-vars/sdidparamexpiry.md)
      + [Configurations Secure et SameSite](library/function-vars/secure-samesite-config.md)
      + [secureCookie](library/function-vars/securecookie.md)
      + [useCORSOnly](library/function-vars/use-cors-only.md)
      + [whitelistParentDomain et whitelistIframeDomains](library/function-vars/whitelistdomain.md)
   + Méthodes {#methods}
      + [Méthodes](library/get-set/get-set.md)
      + [appendSupplementalDataIDTo](library/get-set/appendsupplementaldataidto.md)
      + [appendVisitorIDsTo (suivi interdomaines)](library/get-set/appendvisitorid.md)
      + [Méthodes callTimeOut](library/get-set/timeout-functions.md)
      + [Synchronisation des ID par URL ou source de données](library/get-set/idsync.md)
      + [getInstance](library/get-set/getinstance.md)
      + [getAnalyticsVisitorID](library/get-set/getanalyticsvisitorid.md)
      + [getCustomerIDs](library/get-set/getcustomerids.md)
      + [setCustomerIDs](library/get-set/setcustomerids.md)
      + [getMarketingCloudVisitorID](library/get-set/getmcvid.md)
      + [getLocationHint](library/get-set/getlocationhint.md)
      + [getVisitorValues](library/get-set/getvisitorvalues.md)
      + [isClientSideMarketingCloudVisitorID](library/get-set/client-side-id.md)
      + [resetState](library/get-set/resetstate.md)
+ Référence {#reference}
   + [Vue d’ensemble de la référence](reference/reference.md)
   + [Modifications de l’étiquetage SameSite de Google Chrome](reference/chrome-samesite-labelling.md)
   + [Politiques de sécurité du contenu et service d’identification des visiteurs](reference/csp.md)
   + [Prise en charge de la loi COPPA dans le service d’identification des visiteurs](reference/coppa.md)
   + [Prise en charge de la norme CORS dans le service d’identification des visiteurs](reference/cors.md)
   + [ID de client et états d’authentification](reference/authenticated-state.md)
   + [Méthodes de bibliothèque ECID dans un univers ITP Safari](reference/ecid-library-methods.md)
   + [Identification des visiteurs uniques](reference/unique-vis-method.md)
   + [Obtention des identifiants de région et d’utilisateur à partir du cookie AMCV ou du service d’identification des visiteurs](reference/regions.md)
   + [Conditions requises pour le service d’identification des visiteurs](reference/requirements.md)
   + [Mesure de pulsation vidéo et service d’identification des visiteurs](reference/heartbeat.md)
   + [Prise en charge du hachage SHA-256 pour setCustomerIDs](reference/hashing-support.md)
+ Questions fréquentes {#faqs}
   + [Présentation des FAQ](faq-intro/faq-intro.md)
   + [FAQ sur le service d’identification des visiteurs](faq-intro/faq.md)
   + [Questions fréquentes sur les autres solutions CX pour les entreprises](faq-intro/other-faq.md)
+ Notes de mise à jour du service d’identification des visiteurs {#release-notes}
   + [Notes de mise à jour de 2022](release-notes/notes-2022.md)
   + [Notes de mise à jour de 2021](release-notes/notes-2021.md)
   + [Notes de mise à jour de 2020](release-notes/notes-2020.md)
   + [Notes de mise à jour de 2019](release-notes/notes-2019.md)
   + [Notes de mise à jour de 2018](release-notes/notes-2018.md)
   + [Notes de mise à jour de 2017](release-notes/notes-2017.md)
   + [Notes de mise à jour de 2016](release-notes/notes-2016.md)
   + [Notes de mise à jour de 2015](release-notes/notes-2015.md)
