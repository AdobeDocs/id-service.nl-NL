---
description: Functies worden vrijgegeven, bijgewerkt of gewijzigd in de Experience Cloud Identity Service.
keywords: ID Service
seo-description: Functies worden vrijgegeven, bijgewerkt of gewijzigd in de Experience Cloud Identity Service.
seo-title: Opmerkingen bij de release 2019
title: Opmerkingen bij de release 2019
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: tm+mt
source-git-commit: 25a9af7a28462bc0bd26cf4a5a58203e76a83366

---


# Opmerkingen bij de release Experience Cloud - 2019 {#release-notes}

Functies worden vrijgegeven, bijgewerkt of gewijzigd in de Experience Cloud Identity Service.

## Versie 4.4.1

Selectievakje voor goedkeuring vóór aanmelding toevoegen voor media-analyse in ECID Launch Extension (CORE-33185)

**Oplossingen**

* Issue with ECID launch extension preOptInApproval input string parsing(CORE-34041)
* De daling van prestaties wanneer trackingServer wordt gebruikt (CORE-32387)

## Versie 4.4 {#version-4point4}

**Nieuwe functie**

[SHA256 Hashing Support for setCustomerIDs](/help/reference/hashing-support.md). Ervaar de Dienst van de Wolk ID (ECID) steunt het shashing algoritme SHA-256 dat u toestaat om klant IDs of e-mailadressen over te gaan, en gehakt IDs door te geven.

**Oplossingen, verbeteringen, verbeteringen**

* We hebben een configuratieupdate uitgevoerd naar `cookieDomain`. De ECID-bibliotheek filtert nu de lege tekenreeks `cookieDomain` in `initConfig` en gebruikt het cookiedomein op hoofdniveau, dat door de getDomain-methode wordt geretourneerd. (CORE-2923)
* We hebben een bug opgelost die verband houdt met `getVisitorValues` in `localVisitor`. (CORE-31287)
* We hebben een fout verholpen waarbij er een inconsistentie was voor de MCOPTOUT-waarde in de Safari-browser, geretourneerd door de `getVisitorValue` methode. (CORE-29719)
* We hebben de plug-in-bibliotheek bijgewerkt door het abonnement op gebeurtenissen op `optIn.off` te zeggen.
* We hebben een fout verholpen met betrekking tot de functie setTimeout, waarbij het Content Security Policy (CSP) op sommige klantsites werd `setTimeout` overtreden. (CORE-30623)

## Versie 4.3 {#version-4point3}

**Ondersteuning voor ITP 2.1**. Als een volgende server in een eerste partij CNAME wordt geplaatst, wordt een nieuw koekje (s_ecid) geplaatst met de ECID waarde. De ECID-bibliotheek verwijst naar de waarde om de id langer dan 7 dagen te laten bestaan. Zie [ECID-bibliotheekmethoden in een Safari ITP-wereld](/help/reference/ecid-library-methods.md).

**Bugcorrectie voor SecureCookie-configuratie.**

## Versie 4.1

Bijwerken `publishDestinations` per nieuwe API-wijziging. Met deze update kan de referentie-informatie van de pagina desgewenst worden weergegeven tijdens de id - synchronisatie. (CORE-23693)

## Versie 4.2

Ondersteuning voor de plug-in Audience Manager voor IAB TCF, beschikbaar via het ECID Opt-in-object.

**Oplossingen**

* IAB + OptIn krijgt geen MID voor het reviseren van klanten (CORE-26022)
* OptInApply-configuratie met open-in is nu opgelost in DTM (DTM-12958)
* De ECID-optie om te weigeren schakelt id-syncs uit (CORE-23814)

## Versie 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Inschakelen**. Inschakelen is een uitbreiding van de Experience Cloud ID (ECID) waarmee u kunt bepalen of (en welke) Cloud-bibliotheken cookies kunnen maken op webpagina&#39;s voor bezoekers. Met de Launch [van het](https://docs.adobelaunch.com/)Experience Platform kunt u het verzamelen van bezoekers met de optie Instemmen voor Ervaring Cloud-oplossing vereenvoudigen door Analytics, Target, Audience Manager en andere of alle geselecteerde Experience Cloud-oplossingen in te schakelen om u aan te melden bij uw systeem voor het beheer van toestemming.

## Versie 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Item | Beschrijving |
|---|---|
| `disableIdSyncs` markering werkt niet wanneer een tekenreeks wordt doorgegeven. | Vast. Waarden die zijn ingesteld op `disableidSyncs` parameter voor `getInstance` functie worden nu gerespecteerd. |
| iFrames van derden die geen ECID krijgen | ECID voor Safari Mobil en ECIDs in diverse iFrames verholpen die niet werkten. |