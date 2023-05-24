---
audience: end-user
user-guide-title: Aide d’Experience Cloud Identity Service
breadcrumb-title: Guide d’Identity Service
user-guide-description: Adobe Experience Cloud Identity Service fournit un identifiant universel et persistant qui identifie vos visiteurs et visiteuses à l’échelle de toutes les solutions dans l’Experience Cloud. Il permet de remplacer le code de génération d’ID hérité pour les services et solutions Experience Cloud.
user-guide-url: /content/help/en/id-service/using/home.html
source-git-commit: 6ef86bdb7bc10e24dbd3efe2481cb2e6e6c270fb
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 100%

---


# Aide d’Experience Cloud Identity Service {#using}

+ [Aide d’Identity Service](home.md)
+ Présentation {#intro}
   + [Présentation](introduction/overview.md)
   + [À propos du service d’ID](introduction/about-id-service.md)
   + [Cookies et service d’ID](introduction/cookies.md)
   + [Requête et définition d’ID par le service d’ID](introduction/id-request.md)
   + [Comprendre la synchronisation et les taux de correspondance](introduction/match-rates.md)
+ Implémentation {#implementation}
   + [Méthodes de mise en œuvre](implementation-guides/implementation-methods.md)
   + [Guides de mise en œuvre](implementation-guides/implementation-guides.md)
   + [Implémentation avec les balises Experience Platform](implementation-guides/ecid-implement-with-launch.md)
   + [Implémentation pour Analytics](implementation-guides/setup-analytics.md)
   + [Implémentation pour Target](implementation-guides/setup-target.md)
   + [Implémentation pour Analytics et Audience Manager](implementation-guides/setup-aam-analytics.md)
   + [Implémentation pour Analytics, Audience Manager et Target](implementation-guides/setup-aam-analytics-target.md)
   + [Utilisation du service ID avec A4T et une mise en œuvre côté serveur de Target](implementation-guides/ecid-a4t-target.md)
   + [Intégration directe avec le service d’ID](implementation-guides/direct-integration.md)
   + [Cas d’utilisation de l’intégration directe](implementation-guides/direct-integration-examples.md)
   + [Test et vérification du service d’ID](implementation-guides/test-verify.md)
   + Service Opt-in {#opt-in-service}
      + [Aperçu du service Opt-in](implementation-guides/opt-in-service/optin-overview.md)
      + [Configuration du service Opt-in](implementation-guides/opt-in-service/getting-started.md)
      + [Validation du service Opt-in](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Configurer Opt-in avec Experience Platform Launch](implementation-guides/opt-in-service/launch.md)
      + [Configuration d’Opt-in à l’aide de DTM](implementation-guides/opt-in-service/optin-dtm.md)
      + [Contrôle des activités Experience Cloud en fonction du consentement de l’utilisateur](implementation-guides/opt-in-service/use-opt-in-to-control-experience-cloud-activities-based-on-user-consent.md)
      + [Cas d’utilisation d’Opt-in](implementation-guides/opt-in-service/use-cases.md)
      + [Références d’Opt-in](implementation-guides/opt-in-service/api.md)
      + [Utilisation des services Opt-in avec un framework IAB](implementation-guides/opt-in-service/iab.md)
+ API du service d’ID {#id-service-api}
   + [Présentation de l’API du service d’ID](library/library.md)
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
   + [Présentation de la référence](reference/reference.md)
   + Référence Analytics {#analytics-reference}
      + [Présentation de la référence Analytics](reference/analytics-reference/analytics-reference.md)
      + [Présentation de l’implémentation CNAME](reference/analytics-reference/cname.md)
      + [Définition des Analytics ID et Experience Cloud ID](reference/analytics-reference/analytics-ids.md)
      + [Ordre des opérations pour les Analytics ID](reference/analytics-reference/analytics-order-of-operations.md)
      + [Points de prise de décision concernant la migration vers le service d’ID](reference/analytics-reference/migration-decisions.md)
      + [Scénarios de migration du service d’ID](reference/analytics-reference/migration-scenarios.md)
      + [Requêtes Analytics et d’identité](reference/analytics-reference/legacy-analytics.md)
      + [Mise en œuvre côté serveur alliée à JavaScript](reference/analytics-reference/server-side.md)
      + [Période de grâce du service d’ID](reference/analytics-reference/grace-period.md)
   + [Modifications de l’étiquetage SameSite de Google Chrome](reference/chrome-samesite-labelling.md)
   + [Politiques de sécurité du contenu et service d’ID](reference/csp.md)
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
+ FAQ {#faqs}
   + [Présentation des FAQ](faq-intro/faq-intro.md)
   + [FAQ sur le service d’ID](faq-intro/faq.md)
   + [Questions fréquentes sur Analytics et le service d’ID](faq-intro/analytics-faq.md)
   + [Questions fréquentes sur d’autres solutions Experience Cloud](faq-intro/other-faq.md)
+ Notes de mise à jour du service d’ID {#release-notes}
   + [Notes de mise à jour de 2022](release-notes/notes-2022.md)
   + [Notes de mise à jour de 2021](release-notes/notes-2021.md)
   + [Notes de mise à jour de 2020](release-notes/notes-2020.md)
   + [Notes de mise à jour de 2019](release-notes/notes-2019.md)
   + [Notes de mise à jour de 2018](release-notes/notes-2018.md)
   + [Notes de mise à jour de 2017](release-notes/notes-2017.md)
   + [Notes de mise à jour de 2016](release-notes/notes-2016.md)
   + [Notes de mise à jour de 2015](release-notes/notes-2015.md)
+ [Test Analytics masqué dans la table des matières](analytics-test-file-hidetoc.md)
