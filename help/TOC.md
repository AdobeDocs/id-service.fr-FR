---
cloud: experience-cloud
product: Service d’identification
audience: utilisateur final
user-guide-title: Aide du service d'ID
user-guide-url: /content/help/en/id-service/using/mcvid-home.html
translation-type: tm+mt
source-git-commit: 1dd8b109f7e9567b5f72747ecc653d35d0942413

---


# Aide du service d&#39;ID {#using}

+ [Service Experience Cloud ID](mcvid-home.md)
+ Aperçu {#mcvid-introduction}
   + [Aperçu](mcvid-introduction/mcvid-overview.md)
   + [A propos du service d&#39;ID](mcvid-introduction/mcvid-about-id-service.md)
   + [Les cookies et le service Experience Cloud ID](mcvid-introduction/mcvid-cookies.md)
   + [Demande et définition d&#39;identifiants par le service Experience Cloud ID](mcvid-introduction/mcvid-id-request.md)
   + [Comprendre la synchronisation des identifiants et les taux de correspondance](mcvid-introduction/mcvid-match-rates.md)
+ Guides de mise en œuvre {#implementation-guides}
   + [Guides de mise en œuvre](mcvid-implementation-guides/mcvid-implementation-guides.md)
   + [Méthodes d&#39;implémentation](mcvid-implementation-guides/mcvid-implementation-methods.md)
   + [Mise en œuvre avec Launch](mcvid-implementation-guides/ecid-implement-with-launch.md)
   + [Implémentation avec la gestion dynamique des balises](mcvid-implementation-guides/mcvid-standard.md)
   + [Mise en œuvre du service Experience Cloud ID pour Analytics](mcvid-implementation-guides/mcvid-setup-analytics.md)
   + [Mise en œuvre du service Experience Cloud ID pour Target](mcvid-implementation-guides/mcvid-setup-target.md)
   + [Mise en œuvre du service Experience Cloud ID pour Analytics et Audience Manager](mcvid-implementation-guides/mcvid-setup-aam-analytics.md)
   + [Mise en œuvre du service Experience Cloud ID pour Analytics, Audience Manager et Target](mcvid-implementation-guides/mcvid-setup-aam-analytics-target.md)
   + [Utilisation du service Experience Cloud ID avec A4T et une mise en œuvre côté serveur de Target](mcvid-implementation-guides/ecid-a4t-target.md)
   + [Intégration directe avec le service Experience Cloud ID](mcvid-implementation-guides/mcvid-direct-integration.md)
   + [Cas d’utilisation de l’intégration directe](mcvid-implementation-guides/mcvid-direct-integration-examples.md)
   + [Tester et vérifier le service Experience Cloud ID](mcvid-implementation-guides/mcvid-test-verify.md)
   + Documentation de souscription {#opt-in-service}
      + [Présentation du service de souscription](mcvid-implementation-guides/opt-in-service/mcvid-optin-overview.md)
      + [Définition - Service de souscription](mcvid-implementation-guides/opt-in-service/getting-started.md)
      + [Validation du service de souscription](mcvid-implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Configuration d’Opt-in avec Launch](mcvid-implementation-guides/opt-in-service/launch.md)
      + [Configuration d’Opt-in à l’aide de DTM](mcvid-implementation-guides/opt-in-service/optin-dtm.md)
      + [Cas d’utilisation d’Opt-in](mcvid-implementation-guides/opt-in-service/use-cases.md)
      + [Références d’Opt-in](mcvid-implementation-guides/opt-in-service/api.md)
      + [(bêta) Utilisation des services de souscription avec la structure IAB](mcvid-implementation-guides/opt-in-service/iab.md)
+ API du service d’ID {#id-service-api}
   + [Présentation de l&#39;API du service d&#39;ID](mcvid-library/mcvid-library.md)
   + Configuration {#configurations}
      + [Présentation des configurations](mcvid-library/mcvid-function-vars/mcvid-function-vars.md)
      + [audienceManagerServer et audienceManagerServerSecure](mcvid-library/mcvid-function-vars/mcvid-subdomain-config.md)
      + [cookieDomain](mcvid-library/mcvid-function-vars/mcvid-cookiedomain.md)
      + [cookieLifetime](mcvid-library/mcvid-function-vars/mcvid-cookielifetime.md)
      + [disableIdSyncs](mcvid-library/mcvid-function-vars/mcvid-disableidsync.md)
      + [disableThirdPartyCalls](mcvid-library/mcvid-function-vars/mcvid-disablethirdpartycalls.md)
      + [disableThirdPartyCookies](mcvid-library/mcvid-function-vars/mcvid-disable-cookies.md)
      + [idSyncAttachIframeOnWindowLoad](mcvid-library/mcvid-function-vars/mcvid-idsyncattachiframeonwindowload.md)
      + [idSyncContainerID](mcvid-library/mcvid-function-vars/mcvid-idsyncontainerid.md)
      + [idSyncSSLUseAkamai](mcvid-library/mcvid-function-vars/mcvid-idsyncssluseakamai.md)
      + [isCoopSafe](mcvid-library/mcvid-function-vars/mcvid-coopsafe.md)
      + [loadTimeout](mcvid-library/mcvid-function-vars/mcvid-loadtimeout.md)
      + [overwriteCrossDomainMCIDAndAID](mcvid-library/mcvid-function-vars/mcvid-overwrite-visitor-id.md)
      + [resetBeforeVersion](mcvid-library/mcvid-function-vars/mcvid-resetbeforeversion.md)
      + [sdidParamExpiry](mcvid-library/mcvid-function-vars/mcvid-sdidparamexpiry.md)
      + [secureCookie](mcvid-library/mcvid-function-vars/mcvid-securecookie.md)
      + [useCORSOnly](mcvid-library/mcvid-function-vars/mcvid-use-cors-only.md)
      + [whitelistParentDomain et whitelistIframeDomains](mcvid-library/mcvid-function-vars/mcvid-whitelistdomain.md)
   + Méthodes {#methods}
      + [Méthodes](mcvid-library/mcvid-get-set/mcvid-get-set.md)
      + [appendSupplementalDataIDTo](mcvid-library/mcvid-get-set/mcvid-appendsupplementaldataidto.md)
      + [appendVisitorIDsTo (suivi interdomaines)](mcvid-library/mcvid-get-set/mcvid-appendvisitorid.md)
      + [Méthodes callTimeOut](mcvid-library/mcvid-get-set/mcvid-timeout-functions.md)
      + [Synchronisation des ID par URL ou source de données](mcvid-library/mcvid-get-set/mcvid-idsync.md)
      + [getInstance](mcvid-library/mcvid-get-set/mcvid-getinstance.md)
      + [getAnalyticsVisitorID](mcvid-library/mcvid-get-set/mcvid-getanalyticsvisitorid.md)
      + [getCustomerIDs](mcvid-library/mcvid-get-set/mcvid-getcustomerids.md)
      + [setCustomerIDs](mcvid-library/mcvid-get-set/mcvid-setcustomerids.md)
      + [getMarketingCloudVisitorID](mcvid-library/mcvid-get-set/mcvid-getmcvid.md)
      + [getLocationHint](mcvid-library/mcvid-get-set/mcvid-getlocationhint.md)
      + [getVisitorValues](mcvid-library/mcvid-get-set/mcvid-getvisitorvalues.md)
      + [isClientSideMarketingCloudVisitorID](mcvid-library/mcvid-get-set/mcvid-client-side-id.md)
      + [resetState](mcvid-library/mcvid-get-set/mcvid-resetstate.md)
+ Référence {#reference}
   + [Présentation de référence](mcvid-reference/mcvid-reference.md)
   + Référence Analytics {#analytics-reference}
      + [Présentation de la référence Analytics](mcvid-reference/mcvid-analytics-reference/mcvid-analytics-reference.md)
      + [Définition des Analytics ID et Experience Cloud ID](mcvid-reference/mcvid-analytics-reference/mcvid-analytics-ids.md)
      + [Ordre des opérations pour les Analytics ID](mcvid-reference/mcvid-analytics-reference/mcvid-analytics-order-of-operations.md)
      + [Points de prise de décision concernant la migration vers le service Experience Cloud ID](mcvid-reference/mcvid-analytics-reference/mcvid-migration-decisions.md)
      + [Scénarios de migration du service Experience Cloud ID](mcvid-reference/mcvid-analytics-reference/mcvid-migration-scenarios.md)
      + [Requêtes d’Analytics ID et d’Experience Cloud ID](mcvid-reference/mcvid-analytics-reference/mcvid-legacy-analytics.md)
      + [CNAME de collecte de données et suivi inter-domaines](mcvid-reference/mcvid-analytics-reference/mcvid-cname.md)
      + [Mise en œuvre côté serveur alliée à JavaScript](mcvid-reference/mcvid-analytics-reference/mcvid-server-side.md)
      + [Période de grâce du service d’ID](mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md)    
   + [Stratégies de sécurité du contenu et service Experience Cloud ID](mcvid-reference/mcvid-csp.md)
   + [Prise en charge COPPA dans le service Experience Cloud ID](mcvid-reference/mcvid-coppa.md)
   + [Prise en charge de CORS dans le service Experience Cloud ID](mcvid-reference/mcvid-cors.md)
   + [ID de client et états d’authentification](mcvid-reference/mcvid-authenticated-state.md)
   + [Méthodes de bibliothèque ECID dans un univers ITP Safari](mcvid-reference/ecid-library-methods.md)
   + [Obtention des identifiants de région et d’utilisateur à partir du cookie AMCV et du service d’ID](mcvid-reference/mcvid-regions.md)
   + [Conditions requises pour le service Experience Cloud ID](mcvid-reference/mcvid-requirements.md)
   + [Mesure de pulsation vidéo et service Experience Cloud ID](mcvid-reference/mcvid-heartbeat.md)
   + [Data Workbench et service Experience Cloud ID](mcvid-reference/mcvid-dwb.md)
+ Questions fréquentes {#faqs}
   + [Présentation des questions fréquentes](mcvid-faq-intro/mcvid-faq-intro.md)
   + [FAQ sur le service d’ID](mcvid-faq-intro/mcvid-faq.md)
   + [Questions fréquentes sur Analytics et le service d’ID](mcvid-faq-intro/mcvid-analytics-faq.md)
   + [Questions fréquentes sur d’autres solutions Experience Cloud](mcvid-faq-intro/mcvid-other-faq.md)
+ Notes de mise à jour du service d&#39;ID {#release-notes}
   + [Notes de mise à jour 2019](mcvid-release-notes/mcvid-release-notes.md)
   + [Notes de mise à jour 2018](mcvid-release-notes/mcvid-notes-2018.md)
   + [Notes de mise à jour 2017](mcvid-release-notes/mcvid-notes-2017.md)
   + [Notes de mise à jour 2016](mcvid-release-notes/mcvid-notes-2016.md)
   + [Notes de mise à jour 2015](mcvid-release-notes/mcvid-notes-2015.md)
