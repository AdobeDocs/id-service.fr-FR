---
cloud: platform-cloud
product: Service d'identité
audience: utilisateur final
user-guide-title: Aide du service d'identité de Platform Platform
user-guide-url: /content/help/en/id-service/using/home.html
translation-type: tm+mt
source-git-commit: 1af38efa5e85c09548a6dee6c9c550900f90a8ed

---


# Aide du service d&#39;identité {#using}

+ [Aide du service d&#39;identité](home.md)
+ Aperçu {#intro}
   + [Aperçu](introduction/overview.md)
   + [A propos du service d&#39;identité](introduction/about-id-service.md)
   + [Cookies et service d&#39;identité](introduction/cookies.md)
   + [Demande et définition des identifiants par le service d&#39;identité](introduction/id-request.md)
   + [Comprendre la synchronisation et les taux de correspondance](introduction/match-rates.md)
+ Guides de mise en œuvre {#implementation-guides}
   + [Guides de mise en œuvre](implementation-guides/implementation-guides.md)
   + [Méthodes d&#39;implémentation](implementation-guides/implementation-methods.md)
   + [Mise en œuvre avec Launch](implementation-guides/ecid-implement-with-launch.md)
   + [Mise en œuvre à l’aide de DTM](implementation-guides/standard.md)
   + [Implémentation pour Analytics](implementation-guides/setup-analytics.md)
   + [Implémentation pour Target](implementation-guides/setup-target.md)
   + [Mise en œuvre pour Analytics et Audience Manager](implementation-guides/setup-aam-analytics.md)
   + [Implémentation pour Analytics, Audience Manager et Target](implementation-guides/setup-aam-analytics-target.md)
   + [Utilisation du service d&#39;identité avec A 4 T et une implémentation côté serveur de Target](implementation-guides/ecid-a4t-target.md)
   + [Intégration directe au service d&#39;identité](implementation-guides/direct-integration.md)
   + [Cas d’utilisation de l’intégration directe](implementation-guides/direct-integration-examples.md)
   + [Tester et vérifier le service d&#39;identité](implementation-guides/test-verify.md)
   + Documentation de souscription {#opt-in-service}
      + [Présentation du service de souscription](implementation-guides/opt-in-service/optin-overview.md)
      + [Définition - Service de souscription](implementation-guides/opt-in-service/getting-started.md)
      + [Validation du service de souscription](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Configuration d’Opt-in avec Launch](implementation-guides/opt-in-service/launch.md)
      + [Configuration d’Opt-in à l’aide de DTM](implementation-guides/opt-in-service/optin-dtm.md)
      + [Cas d’utilisation d’Opt-in](implementation-guides/opt-in-service/use-cases.md)
      + [Références d’Opt-in](implementation-guides/opt-in-service/api.md)
      + [(bêta) Utilisation des services de souscription avec la structure IAB](implementation-guides/opt-in-service/iab.md)
+ API des services d’identités {#id-service-api}
   + [Présentation de l&#39;API du service d&#39;identité](library/library.md)
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
      + [Présentation de la référence Analytics](reference/analytics-reference/analytics-reference.md)
      + [Définition des analyses et des identifiants](reference/analytics-reference/analytics-ids.md)
      + [Ordre des opérations pour les Analytics ID](reference/analytics-reference/analytics-order-of-operations.md)
      + [Points de prise de décision concernant la migration du service d&#39;identité](reference/analytics-reference/migration-decisions.md)
      + [Scénarios de migration du service d&#39;identité](reference/analytics-reference/migration-scenarios.md)
      + [Demandes Analytics et d&#39;identité](reference/analytics-reference/legacy-analytics.md)
      + [CNAME de collecte de données et suivi inter-domaines](reference/analytics-reference/cname.md)
      + [Mise en œuvre côté serveur alliée à JavaScript](reference/analytics-reference/server-side.md)
      + [Période de grâce du service d&#39;identité](reference/analytics-reference/grace-period.md)
   + [Stratégies de sécurité du contenu et service d&#39;identité](reference/csp.md)
   + [Prise en charge COPPA dans le service d&#39;identité](reference/coppa.md)
   + [Prise en charge de CORS dans le service d&#39;identité](reference/cors.md)
   + [ID de client et états d’authentification](reference/authenticated-state.md)
   + [Méthodes de bibliothèque ECID dans un univers ITP Safari](reference/ecid-library-methods.md)
   + [Obtention de la région et de l&#39;utilisateur - ID du cookie AMCV ou du service d&#39;identité](reference/regions.md)
   + [Conditions requises pour le service d&#39;identité](reference/requirements.md)
   + [Video Heartbeat et le service d&#39;identité](reference/heartbeat.md)
   + [Outils de données et service d&#39;identité](reference/dwb.md)
+ Questions fréquentes {#faqs}
   + [Présentation des questions fréquentes](faq-intro/faq-intro.md)
   + [FAQ sur le service d&#39;identité](faq-intro/faq.md)
   + [FAQ sur le service d&#39;analyse et d&#39;identité](faq-intro/analytics-faq.md)
   + [Questions fréquentes sur d’autres solutions Experience Cloud](faq-intro/other-faq.md)
+ Notes de mise à jour du service d&#39;identité {#release-notes}
   + [Notes de mise à jour 2019](release-notes/release-notes.md)
   + [Notes de mise à jour 2018](release-notes/notes-2018.md)
   + [Notes de mise à jour 2017](release-notes/notes-2017.md)
   + [Notes de mise à jour 2016](release-notes/notes-2016.md)
   + [Notes de mise à jour 2015](release-notes/notes-2015.md)
