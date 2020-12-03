---
description: De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van de Experience Cloud.
keywords: ID Service
seo-description: De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van de Experience Cloud.
seo-title: Opmerkingen bij de release 2019
title: Opmerkingen bij de release 2019
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: tm+mt
source-git-commit: 8ece066545f4ca4a7bd1eca67c8f02dcd2a88369
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 1%

---


# Experience Cloud release notes - 2019 {#release-notes}

De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van de Experience Cloud.

## Versie 4.4.1

Schakel het selectievakje Goedkeuring vóór aanmelding voor mediacontrole in de ECID Launch Extension in.

**Oplossingen**

* Issue with ECID launch extension preOptInApproval input string parsing.
* De daling van prestaties wanneer trackingServer wordt gebruikt.

## Versie 4.4 {#version-4point4}

**Nieuwe functie**

[SHA256 Hashing Support for setCustomerIDs](/help/reference/hashing-support.md). De Dienst van identiteitskaart van de Experience Cloud (ECID) steunt het shashing algoritme SHA-256 dat u toestaat om klant IDs of e-mailadressen over te gaan, en gehakt IDs door te geven.

**Oplossingen, verbeteringen, verbeteringen**

* We hebben een configuratieupdate uitgevoerd naar `cookieDomain`. De ECID-bibliotheek filtert nu de lege tekenreeks `cookieDomain` in `initConfig` en gebruikt het cookiedomein op hoofdniveau, dat door de getDomain-methode wordt geretourneerd.
* We hebben een bug opgelost die verband houdt met `getVisitorValues` in `localVisitor`.
* We hebben een fout verholpen waarbij er een inconsistentie was voor de MCOPTOUT-waarde in de Safari-browser, geretourneerd door de `getVisitorValue` methode.
* We hebben de plug-in-bibliotheek bijgewerkt door het abonnement op gebeurtenissen op `optIn.off` te zeggen.
* We hebben een fout verholpen met betrekking tot de functie setTimeout, waarbij het Content Security Policy (CSP) op sommige klantsites werd `setTimeout` overtreden.

## Versie 4.3 {#version-4point3}

**Ondersteuning voor ITP 2.1**. Als een volgende server in een eerste partij CNAME wordt geplaatst, wordt een nieuw koekje (s_ecid) geplaatst met de ECID waarde. De ECID-bibliotheek verwijst naar de waarde om de id langer dan 7 dagen te laten bestaan. Zie [ECID-bibliotheekmethoden in een Safari ITP-wereld](/help/reference/ecid-library-methods.md).

**Bugcorrectie voor SecureCookie-configuratie.**

## Versie 4.1

Bijwerken `publishDestinations` per nieuwe API-wijziging. Met deze update kan de referentie-informatie van de pagina desgewenst worden weergegeven tijdens de id - synchronisatie.

## Versie 2.2

Ondersteuning voor de plug-in Audience Manager voor IAB TCF, beschikbaar via het ECID Opt-in-object.

**Oplossingen**

* IAB + OptIn krijgt geen MID voor het reviseren van klanten.
* Correctie van bug met betrekking tot de plug-in-configuratie OptInApply in DTM.
* De optie ECID-uitschakelt ID-syncs.

## Versie 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Inschakelen**. Inschakelen is een uitbreiding van de Experience Cloud-id (ECID) waarmee u kunt bepalen of (en welke) Experience Cloud-bibliotheken cookies kunnen maken op webpagina&#39;s voor bezoekers. Gebruikend [Experience Platform Launch](https://docs.adobelaunch.com/), kunt u het verzamelen van bezoekersopt-in toestemmingen voor de oplossing van de Experience Cloud vereenvoudigen door Analytics, Doel, Audience Manager, en andere of alle uitgezochte oplossingen van Experience Cloud toe te laten om aan uw systeem van het toestemmingsbeheer te kiezen.

## Versie 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Item | Beschrijving |
|---|---|
| `disableIdSyncs` markering werkt niet wanneer een tekenreeks wordt doorgegeven. | Vast. Waarden die zijn ingesteld op `disableidSyncs` parameter voor `getInstance` functie worden nu gerespecteerd. |
| iFrames van derden die geen ECID krijgen | ECID voor Safari Mobil en ECIDs in diverse iFrames verholpen die niet werkten. |
