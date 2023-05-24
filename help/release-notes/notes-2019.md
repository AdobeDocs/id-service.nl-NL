---
description: De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van de Experience Cloud.
keywords: ID-service
title: Opmerkingen bij de release 2019
exl-id: 11439e27-9740-4afc-a2b8-5e35d179f34f
source-git-commit: 503683b66b6022b7c1fecbfb197fe17e05ae9c64
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 2%

---

# Opmerkingen bij de release Experience Cloud - 2019 {#release-notes}

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

* We hebben een configuratieupdate uitgevoerd naar `cookieDomain`. De ECID-bibliotheek filtert nu de lege tekenreeks uit `cookieDomain` in `initConfig` en gebruikt het cookiedomein op het hoogste niveau, dat door de methode getDomain is teruggekeerd.
* We hebben een fout verholpen met betrekking tot `getVisitorValues` in `localVisitor`.
* We hebben een bug opgelost waarbij er een inconsistentie was voor de MCOPTOUT-waarde in de Safari-browser, geretourneerd door de `getVisitorValue` methode.
* We hebben de plug-in-bibliotheek bijgewerkt door het toevoegen van `optIn.off` om uw abonnement op gebeurtenissen op te zeggen.
* We hebben een fout verholpen met betrekking tot de functie setTimeout, waarbij `setTimeout` overtreden het Beleid van de Veiligheid van de Inhoud (CSP) op sommige klantenplaatsen.

## Versie 4.3 {#version-4point3}

**Ondersteuning voor ITP 2.1**. Als een volgende server in een eerste partij CNAME wordt geplaatst, wordt een nieuw koekje (s_ecid) geplaatst met de ECID waarde. De ECID-bibliotheek verwijst naar de waarde om de id langer dan 7 dagen te laten bestaan. Zie [ECID-bibliotheekmethoden in een Safari ITP-wereld](/help/reference/ecid-library-methods.md).

**Bugcorrectie voor SecureCookie-configuratie.**

## Versie 4.1

Bijwerken `publishDestinations` per nieuwe API-wijziging. Met deze update kan de referentie-informatie van de pagina desgewenst worden weergegeven tijdens de id - synchronisatie.

## Versie 4.2

Ondersteuning voor de plug-in Audience Manager voor IAB TCF, beschikbaar via het ECID Opt-in-object.

**Oplossingen**

* IAB + OptIn krijgt geen MID voor het reviseren van klanten.
* Correctie van bug met betrekking tot de plug-in-configuratie OptInApply in DTM.
* De ECID-optie om te weigeren schakelt id-syncs uit.

## Versie 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Inschakelen van service**. Inschakelen is een uitbreiding van de Experience Cloud-id (ECID) waarmee u kunt bepalen of (en welke) Experience Cloud-bibliotheken cookies kunnen maken op webpagina&#39;s voor bezoekers. Gebruiken [Experience Platform Launch](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl), kunt u het verzamelen van bezoekersopt-in toestemmingen voor de oplossing van de Experience Cloud vereenvoudigen door Analytics, Doel, Audience Manager, en andere of allen uitgezochte oplossingen van de Experience Cloud toe te laten om aan uw systeem van het toestemmingsbeheer te kiezen.

## Versie 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Item | Beschrijving |
|---|---|
| `disableIdSyncs` markering werkt niet wanneer een tekenreeks wordt doorgegeven. | Vast. Waarden ingesteld op `disableidSyncs` parameter for `getInstance` de functie wordt nu gerespecteerd . |
| iFrames van derden die geen ECID krijgen | ECID voor Safari Mobil en ECIDs in diverse iFrames verholpen die niet werkten. |
