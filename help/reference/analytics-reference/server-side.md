---
description: In sommige implementaties worden bezoeker-id's vanuit JavaScript doorgegeven aan een server, zodat extra Analytics-gebeurtenissen (zoals een aankoop) door de server kunnen worden verzonden.
keywords: ID-service
title: Implementatie aan de serverzijde gemengd met JavaScript
exl-id: 1986ee11-2021-4f34-bb56-6eaa87b6dd6d
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 3%

---

# Implementatie aan de serverzijde gemengd met JavaScript {#server-side-implementation-mixed-with-javascript}

In sommige implementaties worden bezoeker-id&#39;s vanuit JavaScript doorgegeven aan een server, zodat extra Analytics-gebeurtenissen (zoals een aankoop) door de server kunnen worden verzonden.

De ID service-API biedt de methoden [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md) en [getAnalyticsVisitorID](../../library/get-set/getanalyticsvisitorid.md) om de id-waarden op te halen die vervolgens aan de server kunnen worden doorgegeven.

Controleer of de bezoeker-id van de Experience Cloud en de bezoeker-id van de Analyse zijn gecontroleerd en verstuur beide id&#39;s (indien aanwezig) om te controleren of de verzonden gegevens zijn gekoppeld aan het bestaande profiel van de Analyse-bezoeker.

>[!IMPORTANT]
>
>AppMeasurement voor Java biedt momenteel geen ondersteuning voor de Experience Cloud Identity Service.

## API voor gegevensinvoer {#section-955ce7664a4646d38b3005cb2df40baf}

Neem de bezoeker-id voor Analytics (indien ingesteld) op in het element `<visitorID>`.

Neem de Experience Cloud-bezoeker-id op in het element `<marketingCloudVisitorID>`.

Zie [Ondersteunde XML-labels](https://www.adobe.io).

## AppMeasurement voor Java {#section-d664b94934924d048300d9c2b6560085}

De Experience Cloud Identity Service wordt momenteel niet ondersteund door AppMeasurement voor Java.
