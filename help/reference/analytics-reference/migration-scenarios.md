---
description: Bevat configuraties van servervoorbeelden en de vereiste migratiestappen.
keywords: ID-service
title: Migratiescenario's voor identiteitsservice van Experience Cloud
exl-id: 419532bf-399f-4646-a95f-31c35535d6fc
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# Migratiescenario&#39;s voor identiteitsservice van Experience Cloud {#experience-cloud-id-service-migration-scenarios}

Bevat configuraties van servervoorbeelden en de vereiste migratiestappen.

## Eén webeigenschap {#section-6ccfea84628d46c99507cb124e7f5445}

* **Klant**: Het Bedrijf Inc. van het voorbeeld.
* **toegelaten Experience Cloud**: Nr
* **Eigenschappen van het Web**: example.com
* **de inzamelingsservers van Gegevens**: metrics.example.com, smetrics.example.com
* **het dossier van JavaScript van Analytics**: Één enkel dossier voor alle plaatspagina&#39;s

Eerst, zou deze klant voor het Experience Cloud moeten worden toegelaten (zie de [ vereisten ](../../reference/requirements.md)). En omdat ze één JavaScript-bestand hebben, heeft deze klant geen respijtperiode nodig. Deze klant zal ook de migratie van de opsteller en dan vanaf hun gegevensinzameling CNAME migreren, wat niet noodzakelijk is.

## Meerdere JavaScript-bestanden, hardgecodeerde afbeeldingstags {#section-a665f6ee202940449198e4e7a5dcac54}

* **Klant**: Een ander Bedrijf Inc. van het Voorbeeld.
* **toegelaten Experience Cloud**: Ja
* **Eigenschappen van het Web**: anotherexample.com
* **de inzamelingsservers van Gegevens**: anotherexampleco.112.2o7.net
* **het dossier van JavaScript van Analytics**: De veelvoudige dossiers van JavaScript. Eén bestand voor de hoofdsite, een ander bestand voor de ondersteuningssectie dat in een aparte CMS wordt bijgehouden.
* **Andere methodes van de gegevensinzameling**: Vast-gecodeerde beeldmarkeringen op één plaatsctie

Eerst, zou deze klant hun identiteitskaart van de Organisatie van Adobe Experience Cloud moeten vinden (zie de [ vereisten ](../../reference/requirements.md)). Vervolgens moeten ze een migratieperiode configureren omdat ze meerdere JavaScript-bestanden gebruiken. Deze klant stelt ook een migratie naar bezoekers in en migreert vervolgens van `*.2o7.net` naar `*.sc.omtrdc.net` .

Wanneer deze klant de nieuwste JavaScript-code voor Analytics bijwerkt ter voorbereiding op de implementatie van de [!DNL Experience Cloud] ID-service, worden ook alle tags voor afbeeldingen met harde codes bijgewerkt zodat deze JavaScript kunnen gebruiken.

## Meerdere webeigenschappen, meerdere JavaScript-bestanden en een op Flash gebaseerde videospeler {#section-34647995ff3740b999fdee22d885e515}

* **Klant**: Een Goede Klant LLC
* **toegelaten Experience Cloud**: Ja
* **Eigenschappen van het Web**: mymainsite.com, myothersiteA.com, myothersiteB.com
* **de inzamelingsservers van Gegevens**: metrics.mymainsite.com, smetrics.mymainsite.com
* **het dossier van JavaScript van Analytics**: De veelvoudige dossiers van JavaScript. Eén bestand voor elke webeigenschap.
* **Andere methodes van de gegevensinzameling**: Een op Flash-gebaseerde videospeler

Eerst, zou deze klant hun identiteitskaart van de Organisatie van Adobe Experience Cloud moeten vinden (zie de [ vereisten ](../../reference/requirements.md)). Vervolgens moeten ze een migratieperiode configureren omdat ze meerdere JavaScript-bestanden gebruiken. Deze klant volgt bezoekers tussen hun primair domein en hun subdomeinen, zodat zullen zij hun gegevensinzameling CNAME met de dienst van bezoekersidentiteitskaart blijven gebruiken.

Wanneer deze klant de meest recente JavaScript-code voor Analytics bijwerkt ter voorbereiding op de implementatie van de [!DNL Experience Cloud] ID-service, wordt ook de op Flash gebaseerde videospeler bijgewerkt naar de meest recente versie van AppMeasurement voor Flash.
