---
cloud: platform-cloud
product: Service d’identification
audience: end-user
user-guide-title: Aide du service d'identité Experience Cloud
user-guide-url: /content/help/en/id-service/using/home.html
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Experience Cloud Identity Service Help {#using}

+ [Aide du service d’ID](home.md)
+ Aperçu {#intro}
   + [Aperçu](introduction/overview.md)
   + [À propos du service d’ID](introduction/about-id-service.md)
   + [Cookies et service d’ID](introduction/cookies.md)
   + [Requête et définition d’ID par le service  ID](introduction/id-request.md)
   + [Comprendre la synchronisation et les taux de correspondance](introduction/match-rates.md)
+ Guides de mise en œuvre {#implementation-guides}
   + [Guides de mise en œuvre](implementation-guides/implementation-guides.md)
   + [Méthodes de mise en œuvre](implementation-guides/implementation-methods.md)
   + [Implémentation avec le lancement de plateforme Experience](implementation-guides/ecid-implement-with-launch.md)
   + [Mise en œuvre à l’aide de DTM](implementation-guides/standard.md)
   + [Implémentation pour Analytics](implementation-guides/setup-analytics.md)
   + [Implémentation pour Target](implementation-guides/setup-target.md)
   + [Mise en œuvre pour Analytics et Audience Manager](implementation-guides/setup-aam-analytics.md)
   + [Implémentation pour Analytics, Audience Manager et Target](implementation-guides/setup-aam-analytics-target.md)
   + [Utilisation du service  ID avec A4T et une mise en œuvre côté serveur de Target](implementation-guides/ecid-a4t-target.md)
   + [Intégration directe au service d'ID](implementation-guides/direct-integration.md)
   + [Cas d’utilisation de l’intégration directe](implementation-guides/direct-integration-examples.md)
   + [Tester et vérifier le service d'ID](implementation-guides/test-verify.md)
   + Documentation Opt-in {#opt-in-service}
      + [Aperçu du service Opt-in](implementation-guides/opt-in-service/optin-overview.md)
      + [Configuration du service Opt-in](implementation-guides/opt-in-service/getting-started.md)
      + [Validation du service Opt-in](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Configuration de souscription avec le lancement de plateforme d'expérience](implementation-guides/opt-in-service/launch.md)
      + [Configuration d’Opt-in à l’aide de DTM](implementation-guides/opt-in-service/optin-dtm.md)
      + [Cas d’utilisation d’Opt-in](implementation-guides/opt-in-service/use-cases.md)
      + [Références d’Opt-in](implementation-guides/opt-in-service/api.md)
      + [Utilisation des services Opt-in avec un framework IAB (bêta)](implementation-guides/opt-in-service/iab.md)
+ API du service d’ID {#id-service-api}
   + [Présentation de l'API du service d'ID](library/library.md)
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
   + [Présentation de référence](reference/reference.md)
   + Référence Analytics {#analytics-reference}
      + [Aperçu de la référence Analytics](reference/analytics-reference/analytics-reference.md)
      + [Définition des Analytics ID et Experience Cloud ID](reference/analytics-reference/analytics-ids.md)
      + [Ordre des opérations pour les Analytics ID](reference/analytics-reference/analytics-order-of-operations.md)
      + [Points de prise de décision concernant la migration du service d'ID](reference/analytics-reference/migration-decisions.md)
      + [Scénarios de migration du service d'ID](reference/analytics-reference/migration-scenarios.md)
      + [Demandes Analytics et d'identité](reference/analytics-reference/legacy-analytics.md)
      + [CNAME de collecte de données et suivi inter-domaines](reference/analytics-reference/cname.md)
      + [Mise en œuvre côté serveur alliée à JavaScript](reference/analytics-reference/server-side.md)
      + [Période de grâce du service d’ID](reference/analytics-reference/grace-period.md)
   + [Stratégies de sécurité du contenu et service d'ID](reference/csp.md)
   + [Prise en charge COPPA dans le service d'ID](reference/coppa.md)
   + [Prise en charge de CORS dans le service d'ID](reference/cors.md)
   + [ID de client et états d’authentification](reference/authenticated-state.md)
   + [Méthodes de bibliothèque ECID dans un univers ITP Safari](reference/ecid-library-methods.md)
   + [Obtention des identifiants de région et d’utilisateur à partir du cookie AMCV et du service d’ID](reference/regions.md)
   + [Conditions requises pour le service d'ID](reference/requirements.md)
   + [Pulsation vidéo et service d'ID](reference/heartbeat.md)
   + [Outils de données et service d'ID](reference/dwb.md)
+ Questions fréquentes {#faqs}
   + [Aperçu des questions fréquentes](faq-intro/faq-intro.md)
   + [FAQ sur le service d’ID](faq-intro/faq.md)
   + [Questions fréquentes sur Analytics et le service d’ID](faq-intro/analytics-faq.md)
   + [Questions fréquentes sur d’autres solutions Experience Cloud](faq-intro/other-faq.md)
+ Notes de mise à jour du service d’ID {#release-notes}
   + [Notes de mise à jour 2019](release-notes/release-notes.md)
   + [Notes de mise à jour 2018](release-notes/notes-2018.md)
   + [Notes de mise à jour 2017](release-notes/notes-2017.md)
   + [Notes de mise à jour 2016](release-notes/notes-2016.md)
   + [Notes de mise à jour 2015](release-notes/notes-2015.md)
