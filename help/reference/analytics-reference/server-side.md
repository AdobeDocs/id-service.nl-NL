---
description: In sommige implementaties worden bezoeker-id's vanuit JavaScript doorgegeven aan een server, zodat extra Analytics-gebeurtenissen (zoals een aankoop) door de server kunnen worden verzonden.
keywords: ID Service
seo-description: In sommige implementaties worden bezoeker-id's vanuit JavaScript doorgegeven aan een server, zodat extra Analytics-gebeurtenissen (zoals een aankoop) door de server kunnen worden verzonden.
seo-title: Implementatie aan de serverzijde gemengd met JavaScript
title: Implementatie aan de serverzijde gemengd met JavaScript
uuid: 256ea0e7-1eb4-4c92-9a7e-f61cb1ed13c7
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Implementatie aan de serverzijde gemengd met JavaScript {#server-side-implementation-mixed-with-javascript}

In sommige implementaties worden bezoeker-id&#39;s vanuit JavaScript doorgegeven aan een server, zodat extra Analytics-gebeurtenissen (zoals een aankoop) door de server kunnen worden verzonden.

De id-service-API biedt de methoden [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md) en [getAnalyticsVisitorID](../../library/get-set/getanalyticsvisitorid.md)om de id-waarden op te halen die vervolgens aan de server kunnen worden doorgegeven.

Controleer of u zowel de Experience Cloud-bezoeker-id als de Analytics-bezoeker-id hebt gecontroleerd en verzend beide id&#39;s (indien aanwezig) om te controleren of de verzonden gegevens zijn gekoppeld aan het bestaande Analytics-bezoekersprofiel.

>[!IMPORTANT]
>
>AppMeasurement voor Java biedt momenteel geen ondersteuning voor de Experience Cloud Identity Service.

## API voor gegevensinvoer {#section-955ce7664a4646d38b3005cb2df40baf}

Neem de bezoeker-id voor Analytics (indien ingesteld) op in het `<visitorID>` element.

Neem de Experience Cloud-bezoekersidentiteitskaart op in het `<marketingCloudVisitorID>` element.

Zie [Ondersteunde XML-labels](https://marketing.adobe.com/developer/en_US/documentation/data-insertion/r-supported-tags).

## AppMeasurement voor Java {#section-d664b94934924d048300d9c2b6560085}

De Experience Cloud Identity Service wordt momenteel niet ondersteund door AppMeasurement voor Java.
