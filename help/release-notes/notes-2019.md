---
description: De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van de Experience Cloud.
keywords: ID-service
title: Opmerkingen bij de release 2019
exl-id: 11439e27-9740-4afc-a2b8-5e35d179f34f
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 1%

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

* We hebben een configuratieupdate uitgevoerd naar `cookieDomain`. De ECID-bibliotheek filtert nu de lege tekenreeks `cookieDomain` in `initConfig` uit en gebruikt het cookiedomein op het hoogste niveau, dat door de getDomain-methode wordt geretourneerd.
* We hebben een fout met betrekking tot `getVisitorValues` opgelost in `localVisitor`.
* We hebben een fout verholpen waarbij er een inconsistentie was voor de MCOPTOUT-waarde in de Safari-browser, geretourneerd door de `getVisitorValue`-methode.
* We hebben de plug-in-bibliotheek bijgewerkt door `optIn.off` toe te voegen om het abonnement op gebeurtenissen op te zeggen.
* We hebben een fout verholpen met betrekking tot de setTimeout-functie, waarbij `setTimeout` het Content Security Policy (CSP) op bepaalde klantsites heeft overtreden.

## Versie 4.3 {#version-4point3}

**Ondersteuning voor ITP 2.1**. Als een volgende server in een eerste partij CNAME wordt geplaatst, wordt een nieuw koekje (s_ecid) geplaatst met de ECID waarde. De ECID-bibliotheek verwijst naar de waarde om de id langer dan 7 dagen te laten bestaan. Zie [ECID-bibliotheekmethoden in een Safari ITP-wereld](/help/reference/ecid-library-methods.md).

**Bugcorrectie voor SecureCookie-configuratie.**

## Versie 4.1

`publishDestinations` bijwerken per nieuwe API-wijziging. Met deze update kan de referentie-informatie van de pagina desgewenst worden weergegeven tijdens de id - synchronisatie.

## Versie 4.2

Ondersteuning voor de plug-in Audience Manager voor IAB TCF, beschikbaar via het ECID Opt-in-object.

**Oplossingen**

* IAB + OptIn krijgt geen MID voor het reviseren van klanten.
* Correctie van bug met betrekking tot de plug-in-configuratie OptInApply in DTM.
* De optie ECID-uitschakelt ID-syncs.

## Versie 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Inschakelen**. Inschakelen is een uitbreiding van de Experience Cloud-id (ECID) waarmee u kunt bepalen of (en welke) Experience Cloud-bibliotheken cookies kunnen maken op webpagina&#39;s voor bezoekers. Gebruikend [Experience Platform Launch](https://experienceleague.adobe.com/docs/launch/using/home.html), kunt u het verzamelen van bezoekersopt-in toestemmingen voor de oplossing van de Experience Cloud vereenvoudigen door Analytics, Doel, Audience Manager, en andere of allen toe te laten selecteren Experience Cloud oplossingen aan opt-in aan uw systeem van het toestemmingsbeheer.

## Versie 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Item | Beschrijving |
|---|---|
| `disableIdSyncs` markering werkt niet wanneer een tekenreeks wordt doorgegeven. | Vast. Waarden die zijn ingesteld op de parameter `disableidSyncs` voor de functie `getInstance` worden nu gerespecteerd. |
| iFrames van derden die geen ECID krijgen | ECID voor Safari Mobil en ECIDs in diverse iFrames verholpen die niet werkten. |
