---
description: De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van de Experience Cloud.
keywords: ID-service
title: Opmerkingen bij de release 2020
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
source-git-commit: dce2c0036f697507381d0763c2f6a9538155681c
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 2%

---

# Opmerkingen bij de release Experience Cloud - 2020 {#release-notes}

De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van de Experience Cloud.

## Versie 5.1.1

* Patchoplossing voor het instellen van AMCV-cookie met `SameSite=None` wanneer VisitorJS in een iFrame wordt geladen.

## Versie 5.1.0

* Toevoegen `sameSiteCookie` config om te specificeren `SameSite` kenmerk voor AMCV cookie. Deze config steunt de volgende waarden voor `SameSite` kenmerk:
   * `Strict`
   * `Lax`
   * `None`

Ga voor meer informatie over deze kenmerkwaarden naar [web.dev](https://web.dev/samesite-cookies-explained/) en [SameSite-updates voor chroomprojecten](https://www.chromium.org/updates/same-site/).

## Versie 5.0.1

* Reparatie voor opnemen `d_cf` markering wanneer een nieuwe IAB toestemmingskoord wordt verzonden naar de randen van de Inzameling van Gegevens van Adobe.

## Versie 5.0.0

* Bezoeker 5.0.0-release met ondersteuning voor `IAB 2.0`.

## Versie 4.6

* Made `loadSSL` markering is standaard ingeschakeld. Alle vraag aan de Dienst van de Identiteit zal zijn `https` standaard.  De klanten kunnen het aan vals plaatsen als zij de Diensten van de Identiteit op http van hun willen roepen `non-ssl` pagina&#39;s.
* De functie die is gebruikt voor detectie is bijgewerkt `Internet-Explorer (IE)` versie, om een probleem te verhelpen dat door is gemeld `ESLint`.
Oplossen voor prestatieprobleem op `Internet-Explorer (IE) 11` wanneer ECID optIn krijgt `pre-approval` en later bijgewerkt.

## Versie 4.5

* Vanaf versie 4.5 worden lege id&#39;s die zijn verzonden naar `setCustomerIDs` methode.
* Probleem verholpen die zich voordeed wanneer de aanmelding is geconfigureerd als `doesOptInApply=false` en `isIabContext=true`.

Zie [Opmerkingen bij de release Experience Cloud](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=nl) voor maandelijks vrijgaveopmerkingen voor alle producten.
