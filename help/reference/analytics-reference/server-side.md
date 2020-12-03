---
description: In sommige implementaties worden bezoeker-id's vanuit JavaScript doorgegeven aan een server, zodat extra Analytics-gebeurtenissen (zoals een aankoop) door de server kunnen worden verzonden.
keywords: ID Service
seo-description: In sommige implementaties worden bezoeker-id's vanuit JavaScript doorgegeven aan een server, zodat extra Analytics-gebeurtenissen (zoals een aankoop) door de server kunnen worden verzonden.
seo-title: Implementatie aan de serverzijde gemengd met JavaScript
title: Implementatie aan de serverzijde gemengd met JavaScript
uuid: 256ea0e7-1eb4-4c92-9a7e-f61cb1ed13c7
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 2%

---


# Implementatie aan de serverzijde gemengd met JavaScript {#server-side-implementation-mixed-with-javascript}

In sommige implementaties worden bezoeker-id&#39;s vanuit JavaScript doorgegeven aan een server, zodat extra Analytics-gebeurtenissen (zoals een aankoop) door de server kunnen worden verzonden.

De id-service-API biedt de methoden [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md) en [getAnalyticsVisitorID](../../library/get-set/getanalyticsvisitorid.md)om de id-waarden op te halen die vervolgens aan de server kunnen worden doorgegeven.

Controleer of de bezoeker-id van de Experience Cloud en de bezoeker-id van de Analyse zijn gecontroleerd en verstuur beide id&#39;s (indien aanwezig) om te controleren of de verzonden gegevens zijn gekoppeld aan het bestaande profiel van de Analyse-bezoeker.

>[!IMPORTANT]
>
>AppMeasurement voor Java biedt momenteel geen ondersteuning voor de Experience Cloud Identity Service.

## API voor gegevensinvoer {#section-955ce7664a4646d38b3005cb2df40baf}

Neem de bezoeker-id van Analytics (indien ingesteld) op in het `<visitorID>` element.

Neem de Experience Cloud-bezoeker-id op in het `<marketingCloudVisitorID>` element.

Zie [Ondersteunde XML-labels](https://www.adobe.io).

## AppMeasurement voor Java {#section-d664b94934924d048300d9c2b6560085}

De Experience Cloud Identity Service wordt momenteel niet ondersteund door AppMeasurement voor Java.
