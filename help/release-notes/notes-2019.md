---
description: De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van het Experience Cloud.
keywords: ID-service
title: Opmerkingen bij de release 2019
exl-id: 11439e27-9740-4afc-a2b8-5e35d179f34f
source-git-commit: 503683b66b6022b7c1fecbfb197fe17e05ae9c64
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# Opmerkingen bij de release van Experience Cloud - 2019 {#release-notes}

De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van het Experience Cloud.

## Versie 4.4.1

Schakel het selectievakje Goedkeuring vóór aanmelding voor mediacontrole in de ECID Launch Extension in.

**Oplossingen**

* Issue with ECID launch extension preOptInApproval input string parsing.
* De daling van prestaties wanneer trackingServer wordt gebruikt.

## Versie 4.4 {#version-4point4}

**Nieuwe Eigenschap**

[ SHA256 het Hashing Steun voor setCustomerIDs ](/help/reference/hashing-support.md). De Dienst van identiteitskaart van het Experience Cloud (ECID) steunt het shashing algoritme SHA-256 dat u toestaat om klant IDs of e-mailadressen over te gaan, en gehakt IDs door te geven.

**Bevestigingen, verhogingen, verbeteringen**

* We hebben een configuratieupdate uitgevoerd naar `cookieDomain` . De ECID-bibliotheek filtert nu de lege tekenreeks `cookieDomain` in `initConfig` uit en gebruikt het cookiedomein op hoofdniveau, dat wordt geretourneerd door de methode getDomain.
* We hebben een fout met betrekking tot `getVisitorValues` in `localVisitor` opgelost.
* We hebben een fout verholpen waarbij er een inconsistentie was voor de MCOPTOUT-waarde in de Safari-browser, geretourneerd door de `getVisitorValue` -methode.
* We hebben de plug-in-bibliotheek bijgewerkt door `optIn.off` toe te voegen om het abonnement op gebeurtenissen op te zeggen.
* We hebben een fout verholpen met betrekking tot de functie setTimeout, waarbij `setTimeout` het Content Security Policy (CSP) op bepaalde klantsites heeft overtreden.

## Versie 4.3 {#version-4point3}

**Steun voor ITP 2.1**. Als een volgende server in een eerste partij CNAME wordt geplaatst, wordt een nieuw koekje (s_ecid) geplaatst met de ECID waarde. De ECID-bibliotheek verwijst naar de waarde om de id langer dan 7 dagen te laten bestaan. Zie [ ECID bibliotheekmethodes in een wereld van Safari ITP ](/help/reference/ecid-library-methods.md).

**moeilijke situatie van het insect voor SecureCookie config.**

## Versie 4.1

`publishDestinations` bijwerken per nieuwe API-wijziging. Met deze update kan de referentie-informatie van de pagina desgewenst worden weergegeven tijdens de id - synchronisatie.

## Versie 4.2

Ondersteuning voor de plug-in Audience Manager voor IAB TCF, beschikbaar via het ECID Opt-in-object.

**Oplossingen**

* IAB + OptIn krijgt geen MID voor het reviseren van klanten.
* Correctie van bug met betrekking tot de plug-in-configuratie OptInApply in DTM.
* De ECID-optie om te weigeren schakelt id-syncs uit.

## Versie 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Opt-binnen dienst**. Inschakelen is een uitbreiding van de Experience Cloud-id (ECID) waarmee u kunt bepalen of (en welke) Experiencen Cloud cookies kunnen maken op webpagina&#39;s voor bezoekers. Gebruikend [ Experience Platform Launch ](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl), kunt u het verzamelen van bezoekersopt-in toestemmingen voor de oplossing van het Experience Cloud vereenvoudigen door Analytics, Doel, Audience Manager, en andere of alle uitgezochte oplossingen van het Experience Cloud aan opt-in aan uw systeem van het toestemmingsbeheer toe te laten.

## Versie 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Item | Beschrijving |
|---|---|
| De markering `disableIdSyncs` werkt niet wanneer een tekenreeks wordt doorgegeven. | Vast. Waarden die zijn ingesteld op de parameter `disableidSyncs` voor de functie `getInstance` , worden nu gerespecteerd. |
| iFrames van derden die geen ECID krijgen | ECID voor Safari Mobil en ECIDs in diverse iFrames verholpen die niet werkten. |
