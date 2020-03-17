---
description: Bevat configuraties van servervoorbeelden en de vereiste migratiestappen.
keywords: ID Service
seo-description: Bevat configuraties van servervoorbeelden en de vereiste migratiestappen.
seo-title: Experience Cloud Identity Service Migration Scenario's
title: Experience Cloud Identity Service Migration Scenario's
uuid: 9e229045-6508-48c4-ae39-9537b4941853
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Experience Cloud Identity Service Migration Scenario&#39;s {#experience-cloud-id-service-migration-scenarios}

Bevat configuraties van servervoorbeelden en de vereiste migratiestappen.

## Eén webeigenschap {#section-6ccfea84628d46c99507cb124e7f5445}

* **Klant**: Example Company Inc.
* **Experience Cloud ingeschakeld**: Nee
* **Web-eigenschappen**: example.com
* **Servers** voor gegevensverzameling: metrics.example.com, metrics.example.com
* **JavaScript-analysebestand**: Eén bestand voor alle sitepagina&#39;s

Ten eerste moet deze klant ingeschakeld zijn voor de Experience Cloud (zie de [vereisten](../../reference/requirements.md)). En omdat ze één JavaScript-bestand hebben, heeft deze klant geen respijtperiode nodig. Deze klant zal ook de migratie van de opsteller en dan vanaf hun gegevensinzameling CNAME migreren, wat niet noodzakelijk is.

## Meerdere JavaScript-bestanden, hardgecodeerde afbeeldingstags {#section-a665f6ee202940449198e4e7a5dcac54}

* **Klant**: Een ander voorbeeld Company Inc.
* **Experience Cloud ingeschakeld**: Ja
* **Web-eigenschappen**: Anotherexample.com
* **Servers** voor gegevensverzameling: anotherexample.eco.112.2o7.net
* **JavaScript-analysebestand**: Meerdere JavaScript-bestanden. Eén bestand voor de hoofdsite, een ander bestand voor de ondersteuningssectie dat in een aparte CMS wordt bijgehouden.
* **Andere methoden** voor gegevensverzameling: Hard gecodeerde afbeeldingstags op één sitesectie

Eerst moet deze klant zijn Adobe Experience Cloud Organization-id vinden (zie de [vereisten](../../reference/requirements.md)). Vervolgens moeten ze een migratieperiode configureren omdat ze meerdere JavaScript-bestanden gebruiken. Deze klant stelt ook de migratie van bezoekers in en migreert vervolgens van `*.2o7.net` naar `*.sc.omtrdc.net`.

Wanneer deze klant de nieuwste JavaScript-code Analytics bijwerkt ter voorbereiding op de implementatie van de [!DNL Experience Cloud] ID-service, worden ook alle vasteschijfcodes voor afbeeldingen bijgewerkt zodat deze in plaats daarvan JavaScript kunnen gebruiken.

## Meerdere wegeigenschappen, meerdere JavaScript-bestanden en een op Flash gebaseerde videospeler {#section-34647995ff3740b999fdee22d885e515}

* **Klant**: Een goede LLC voor klanten
* **Experience Cloud ingeschakeld**: Ja
* **Web-eigenschappen**: mymainsite.com, myothersiteA.com, myothersiteB.com
* **Servers** voor gegevensverzameling: metrics.mymainsite.com, metrics.mymainsite.com
* **JavaScript-analysebestand**: Meerdere JavaScript-bestanden. Eén bestand voor elke webeigenschap.
* **Andere methoden** voor gegevensverzameling: Een op Flash gebaseerde videospeler

Eerst moet deze klant zijn Adobe Experience Cloud Organization-id vinden (zie de [vereisten](../../reference/requirements.md)). Vervolgens moeten ze een migratieperiode configureren omdat ze meerdere JavaScript-bestanden gebruiken. Deze klant volgt bezoekers tussen hun primair domein en hun subdomeinen, zodat zullen zij hun gegevensinzameling CNAME met de dienst van bezoekersidentiteitskaart blijven gebruiken.

Wanneer deze klant de nieuwste JavaScript-code Analytics bijwerkt ter voorbereiding op de implementatie van de [!DNL Experience Cloud] ID-service, wordt ook de op Flash gebaseerde videospeler bijgewerkt naar de nieuwste versie van AppMeasurement voor Flash.
