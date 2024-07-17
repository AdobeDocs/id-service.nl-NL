---
description: De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van het Experience Cloud.
keywords: ID-service
title: Opmerkingen bij de release 2020
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
source-git-commit: dce2c0036f697507381d0763c2f6a9538155681c
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# Opmerkingen bij de release van Experience Cloud - 2020 {#release-notes}

De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van het Experience Cloud.

## Versie 5.1.1

* Reparatie voor het instellen van AMCV-cookie met `SameSite=None` wanneer VisitorJS in een iFrame wordt geladen.

## Versie 5.1.0

* `sameSiteCookie` config toevoegen om het kenmerk `SameSite` voor AMCV-cookie op te geven. Deze config ondersteunt de volgende waarden voor het attribuut `SameSite` :
   * `Strict`
   * `Lax`
   * `None`

Voor meer informatie over deze attributenwaarden, bezoek [ web.dev ](https://web.dev/samesite-cookies-explained/) en [ Updates SameSite door de Projecten van het Chroom ](https://www.chromium.org/updates/same-site/).

## Versie 5.0.1

* Reparatie voor het opnemen van de markering `d_cf` wanneer een nieuwe IAB toestemmingskoord wordt verzonden naar de randen van de Inzameling van Gegevens van de Adobe.

## Versie 5.0.0

* Bezoeker 5.0.0-release met ondersteuning voor `IAB 2.0` .

## Versie 4.6

* Markering `loadSSL` is standaard ingeschakeld. Alle aanroepen naar Identiteitsservice zijn standaard ingeschakeld in `https` .  Klanten kunnen de optie instellen op false als ze Identity Services op http vanaf hun `non-ssl` -pagina&#39;s willen aanroepen.
* De functie voor het detecteren van `Internet-Explorer (IE)` -versie is bijgewerkt om een probleem te verhelpen dat door `ESLint` wordt gemeld.
Oplossing voor prestatieproblemen op `Internet-Explorer (IE) 11` wanneer ECID optIn `pre-approval` krijgt en later wordt bijgewerkt.

## Versie 4.5

* Vanaf versie 4.5 worden lege id&#39;s die naar de methode `setCustomerIDs` zijn verzonden, door ECID afgewezen.
* Probleem verholpen dat zich voordeed wanneer de optie-in is geconfigureerd als `doesOptInApply=false` en `isIabContext=true` .

Zie [ de versienota&#39;s van de Experience Cloud ](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=nl) voor maandelijkse versienota&#39;s voor alle producten.
