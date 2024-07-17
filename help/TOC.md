---
audience: end-user
user-guide-title: Experience Cloud Identity Service Help
breadcrumb-title: Handleiding voor Identity Service
user-guide-description: De Adobe Experience Cloud Identity Service biedt een universele, permanente ID die uw bezoekers identificeert in alle oplossingen in de Experience Cloud. Het helpt bij het vervangen van de verouderde code voor het genereren van ID's voor Experience Cloud-oplossingen en -services.
user-guide-url: /content/help/en/id-service/using/home.html
source-git-commit: 6ef86bdb7bc10e24dbd3efe2481cb2e6e6c270fb
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 13%

---


# Experience Cloud Identity Service Help {#using}

+ [Help bij Identiteitsservice](home.md)
+ Overzicht {#intro}
   + [Overzicht](introduction/overview.md)
   + [Over de id-service](introduction/about-id-service.md)
   + [Cookies en de id-service](introduction/cookies.md)
   + [Hoe de Dienst van identiteitskaart verzoekt en identiteitskaart plaatst](introduction/id-request.md)
   + [Synchronisatie en overeenkomsten](introduction/match-rates.md)
+ Implementatie {#implementation}
   + [Implementatiemethoden](implementation-guides/implementation-methods.md)
   + [Implementatiehulplijnen](implementation-guides/implementation-guides.md)
   + [Implementeren met Experience Platform-tags](implementation-guides/ecid-implement-with-launch.md)
   + [Implementeren voor Analytics](implementation-guides/setup-analytics.md)
   + [Implementeren voor doel](implementation-guides/setup-target.md)
   + [Implementeren voor analyse en Audience Manager](implementation-guides/setup-aam-analytics.md)
   + [Implementeren voor Analytics, Audience Manager en Target](implementation-guides/setup-aam-analytics-target.md)
   + [Het gebruiken van de Dienst van identiteitskaart met A4T en een Server-zijImplementatie van Doel](implementation-guides/ecid-a4t-target.md)
   + [Directe integratie met de Dienst van identiteitskaart](implementation-guides/direct-integration.md)
   + [Gebruiksscenario&#39;s voor directe integratie](implementation-guides/direct-integration-examples.md)
   + [De Dienst van identiteitskaart testen en verifiëren](implementation-guides/test-verify.md)
   + Inschakelen-service {#opt-in-service}
      + [Overzicht van de OpenService](implementation-guides/opt-in-service/optin-overview.md)
      + [Opt-in-service instellen](implementation-guides/opt-in-service/getting-started.md)
      + [Opt-in-service valideren](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Opt-in configureren met Experience Platform Launch](implementation-guides/opt-in-service/launch.md)
      + [Opt-in configureren met DTM](implementation-guides/opt-in-service/optin-dtm.md)
      + [De Activiteiten van het Experience Cloud van de controle die op de Toestemming van de Gebruiker worden gebaseerd](implementation-guides/opt-in-service/use-opt-in-to-control-experience-cloud-activities-based-on-user-consent.md)
      + [Gebruiksscenario&#39;s openen](implementation-guides/opt-in-service/use-cases.md)
      + [Inschakelen-verwijzing](implementation-guides/opt-in-service/api.md)
      + [Het gebruiken van Opt-in de Diensten met IAB Kader](implementation-guides/opt-in-service/iab.md)
+ ID-service-API {#id-service-api}
   + [ID Service API-overzicht](library/library.md)
   + Configuratie {#configurations}
      + [Overzicht van configuraties](library/function-vars/function-vars.md)
      + [publiekManagerServer en publiekManagerServerSecure](library/function-vars/subdomain-config.md)
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
      + [Beveiligde en SameSite-configuraties](library/function-vars/secure-samesite-config.md)
      + [secureCookie](library/function-vars/securecookie.md)
      + [useCORSOnly](library/function-vars/use-cors-only.md)
      + [whitelistParentDomain en whitelistIframeDomains](library/function-vars/whitelistdomain.md)
   + Methoden {#methods}
      + [Methoden](library/get-set/get-set.md)
      + [appendSupplementalDataIDTo](library/get-set/appendsupplementaldataidto.md)
      + [appendVisitorIDsTo (Cross-Domain Tracking)](library/get-set/appendvisitorid.md)
      + [callTimeOut Methods](library/get-set/timeout-functions.md)
      + [ID-synchronisatie met URL of Data Source](library/get-set/idsync.md)
      + [getInstance](library/get-set/getinstance.md)
      + [getAnalyticsVisitorID](library/get-set/getanalyticsvisitorid.md)
      + [getCustomerIDs](library/get-set/getcustomerids.md)
      + [setCustomerIDs](library/get-set/setcustomerids.md)
      + [getMarketingCloudVisitorID](library/get-set/getmcvid.md)
      + [getLocationHint](library/get-set/getlocationhint.md)
      + [getVisitorValues](library/get-set/getvisitorvalues.md)
      + [isClientSideMarketingCloudVisitorID](library/get-set/client-side-id.md)
      + [resetState](library/get-set/resetstate.md)
+ Referentie {#reference}
   + [Overzicht van verwijzingen](reference/reference.md)
   + Referentie voor analysemogelijkheden {#analytics-reference}
      + [Overzicht van de analysehandleiding](reference/analytics-reference/analytics-reference.md)
      + [Overzicht van CNAME-implementatie](reference/analytics-reference/cname.md)
      + [Analyse- en Experience Cloud-id&#39;s instellen](reference/analytics-reference/analytics-ids.md)
      + [Bewerkingsvolgorde voor analytische id&#39;s](reference/analytics-reference/analytics-order-of-operations.md)
      + [Beslissingspunten voor migratie van id-service](reference/analytics-reference/migration-decisions.md)
      + [ID Service Migration Scenarios](reference/analytics-reference/migration-scenarios.md)
      + [Analyses en identiteitsverzoeken](reference/analytics-reference/legacy-analytics.md)
      + [Implementatie aan de serverzijde gemengd met JavaScript](reference/analytics-reference/server-side.md)
      + [De uitstelperiode voor de id-service](reference/analytics-reference/grace-period.md)
   + [Wijzigingen in Google Chrome SameSite-labels](reference/chrome-samesite-labelling.md)
   + [Het Beleid van de Veiligheid van de inhoud en de Dienst van identiteitskaart](reference/csp.md)
   + [COPPA-ondersteuning in de id-service](reference/coppa.md)
   + [CORS-ondersteuning in de id-service](reference/cors.md)
   + [Klant-id&#39;s en verificatiestatus](reference/authenticated-state.md)
   + [ECID-bibliotheekmethoden in een Safari ITP-wereld](reference/ecid-library-methods.md)
   + [Unieke bezoekers identificeren](reference/unique-vis-method.md)
   + [Regio en gebruikers-id&#39;s ophalen van de AMCV-cookie of de ID-service](reference/regions.md)
   + [Vereisten voor de id-service](reference/requirements.md)
   + [Videohartslag en de Dienst van identiteitskaart](reference/heartbeat.md)
   + [Data Workbench en de Dienst van identiteitskaart](reference/dwb.md)
   + [SHA256 Hashing Support for setCustomerIDs](reference/hashing-support.md)
+ Veelgestelde vragen {#faqs}
   + [Overzicht van veelgestelde vragen](faq-intro/faq-intro.md)
   + [Veelgestelde vragen over ID-service](faq-intro/faq.md)
   + [Veelgestelde vragen over Analytics en ID Service](faq-intro/analytics-faq.md)
   + [Veelgestelde vragen over andere oplossingen voor Experiencen Cloud](faq-intro/other-faq.md)
+ Opmerkingen bij de release voor id-service {#release-notes}
   + [Opmerkingen bij de release 2022](release-notes/notes-2022.md)
   + [Opmerkingen bij de release 2021](release-notes/notes-2021.md)
   + [Opmerkingen bij de release 2020](release-notes/notes-2020.md)
   + [Opmerkingen bij de release 2019](release-notes/notes-2019.md)
   + [Opmerkingen bij de release 2018](release-notes/notes-2018.md)
   + [Opmerkingen bij de release 2017](release-notes/notes-2017.md)
   + [Opmerkingen bij de release 2016](release-notes/notes-2016.md)
   + [Opmerkingen bij de release 2015](release-notes/notes-2015.md)
+ [Analyserest verborgen in inhoudsopgave](analytics-test-file-hidetoc.md)
