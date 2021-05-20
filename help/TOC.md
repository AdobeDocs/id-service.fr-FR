---
cloud: platform-cloud
audience: end-user
user-guide-title: Aide d’Experience Cloud Identity Service
breadcrumb-title: Guide d’Identity Service
user-guide-description: Le service d’ID fournit un ID persistant universel qui identifie vos visiteurs dans toutes les solutions Experience Cloud. Il peut remplacer le code de génération des identifiants pour des services tels qu’Analytics, Audience Manager, Target et d’autres solutions ou fonctionnalités d’Experience Cloud.
user-guide-url: /content/help/en/id-service/using/home.html
translation-type: ht
source-git-commit: 01d50f9def8916b45fac846de235363836ba0429
workflow-type: ht
source-wordcount: '397'
ht-degree: 100%

---


# Aide d’Experience Cloud Identity Service {#using}

+ [Aide du service d’ID](home.md)
+ Aperçu {#intro}
   + [Aperçu](introduction/overview.md)
   + [À propos du service d’ID](introduction/about-id-service.md)
   + [Cookies et service d’ID](introduction/cookies.md)
   + [Requête et définition d’ID par le service d’ID](introduction/id-request.md)
   + [Comprendre la synchronisation et les taux de correspondance](introduction/match-rates.md)
+ Mise en œuvre {#implementation}
   + [Méthodes de mise en œuvre](implementation-guides/implementation-methods.md)
   + [Guides de mise en œuvre](implementation-guides/implementation-guides.md)
   + [Mise en œuvre avec Experience Platform Launch](implementation-guides/ecid-implement-with-launch.md)
   + [Mise en œuvre à l’aide de DTM](implementation-guides/standard.md)
   + [Mise en œuvre pour Analytics](implementation-guides/setup-analytics.md)
   + [Mise en œuvre pour Target](implementation-guides/setup-target.md)
   + [Mise en œuvre pour Analytics et Audience Manager](implementation-guides/setup-aam-analytics.md)
   + [Mise en œuvre pour Analytics, Audience Manager et Target](implementation-guides/setup-aam-analytics-target.md)
   + [Utilisation du service d’ID avec A4T et une mise en œuvre côté serveur de Target](implementation-guides/ecid-a4t-target.md)
   + [Intégration directe avec le service d’ID](implementation-guides/direct-integration.md)
   + [Cas d’utilisation de l’intégration directe](implementation-guides/direct-integration-examples.md)
   + [Test et vérification du service d’ID](implementation-guides/test-verify.md)
   + Service Opt-in {#opt-in-service}
      + [Aperçu du service Opt-in](implementation-guides/opt-in-service/optin-overview.md)
      + [Configuration du service Opt-in](implementation-guides/opt-in-service/getting-started.md)
      + [Validation du service Opt-in](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Configuration d’Opt-in avec Experience Platform Launch](implementation-guides/opt-in-service/launch.md)
      + [Configuration d’Opt-in à l’aide de DTM](implementation-guides/opt-in-service/optin-dtm.md)
      + [Contrôler les activités Experience Cloud en fonction du consentement de l’utilisateur](implementation-guides/opt-in-service/use-opt-in-to-control-experience-cloud-activities-based-on-user-consent.md)
      + [Cas d’utilisation d’Opt-in](implementation-guides/opt-in-service/use-cases.md)
      + [Références d’Opt-in](implementation-guides/opt-in-service/api.md)
      + [Utilisation des services Opt-in avec un framework IAB](implementation-guides/opt-in-service/iab.md)
+ API du service d’ID {#id-service-api}
   + [Présentation de l’API du service d’ID](library/library.md)
   + Configuration {#configurations}
      + [Aperçu des configurations](library/function-vars/function-vars.md)
      + [audienceManagerServer et audienceManagerServerSecure](library/function-vars/subdomain-config.md)
      + [cookieDomain](library/function-vars/cookiedomain.md)
      + [cookieLifetime](library/function-vars/cookielifetime.md)
      + [disableIdSyncs](library/function-vars/disableidsync.md)
      + [disableThirdPartyCalls](library/function-vars/disablethirdpartycalls.md)
      + [disableThirdPartyCookies](library/function-vars/disable-cookies.md)
      + [idSyncAttachIframeOnWindowLoad](library/function-vars/idsyncattachiframeonwindowload.md)
      + [idSyncContainerID](library/function-vars/idsyncontainerid.md)
      + [idSyncSSLUseAkamai](library/function-vars/idsyncssluseakamai.md)
      + [isCoopSafe](library/function-vars/coopsafe.md)
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
   + [Aperçu de la référence](reference/reference.md)
   + Référence Analytics {#analytics-reference}
      + [Aperçu de la référence Analytics](reference/analytics-reference/analytics-reference.md)
      + [Présentation de l’implémentation CNAME](reference/analytics-reference/cname.md)
      + [Définition des Analytics ID et Experience Cloud ID](reference/analytics-reference/analytics-ids.md)
      + [Ordre des opérations pour les Analytics ID](reference/analytics-reference/analytics-order-of-operations.md)
      + [Points de prise de décision concernant la migration vers le service d’ID](reference/analytics-reference/migration-decisions.md)
      + [Scénarios de migration du service d’ID](reference/analytics-reference/migration-scenarios.md)
      + [Requêtes Analytics et d’identité](reference/analytics-reference/legacy-analytics.md)
      + [Mise en œuvre côté serveur alliée à JavaScript](reference/analytics-reference/server-side.md)
      + [Période de grâce du service d’ID](reference/analytics-reference/grace-period.md)
   + [Modifications de l’étiquetage SameSite de Google Chrome](reference/chrome-samesite-labelling.md)
   + [Stratégies de sécurité du contenu et service d’ID](reference/csp.md)
   + [Prise en charge de la loi COPPA dans le service d’ID](reference/coppa.md)
   + [Prise en charge de la norme CORS dans le service d’ID](reference/cors.md)
   + [ID de client et états d’authentification](reference/authenticated-state.md)
   + [Méthodes de bibliothèque ECID dans un univers ITP Safari](reference/ecid-library-methods.md)
   + [Identification des visiteurs uniques](reference/unique-vis-method.md)
   + [Obtention des identifiants de région et d’utilisateur à partir du cookie AMCV ou du service d’ID](reference/regions.md)
   + [Conditions requises pour le service d’ID](reference/requirements.md)
   + [Mesure de pulsation vidéo et service d’ID](reference/heartbeat.md)
   + [Data Workbench et service d’ID](reference/dwb.md)
   + [Prise en charge du hachage SHA-256 pour setCustomerIDs](reference/hashing-support.md)
+ Questions fréquentes {#faqs}
   + [Aperçu des questions fréquentes](faq-intro/faq-intro.md)
   + [FAQ sur le service d’ID](faq-intro/faq.md)
   + [Questions fréquentes sur Analytics et le service d’ID](faq-intro/analytics-faq.md)
   + [Questions fréquentes sur d’autres solutions Experience Cloud](faq-intro/other-faq.md)
+ Notes de mise à jour du service d’ID {#release-notes}
   + [Notes de mise à jour 2020](release-notes/release-notes.md)
   + [Notes de mise à jour 2019](release-notes/notes-2019.md)
   + [Notes de mise à jour 2018](release-notes/notes-2018.md)
   + [Notes de mise à jour 2017](release-notes/notes-2017.md)
   + [Notes de mise à jour 2016](release-notes/notes-2016.md)
   + [Notes de mise à jour 2015](release-notes/notes-2015.md)
