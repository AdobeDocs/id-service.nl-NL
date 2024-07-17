---
description: In sommige implementaties worden bezoeker-id's doorgegeven van JavaScript naar een server, zodat extra Analytics-gebeurtenissen (zoals een aankoop) door de server kunnen worden verzonden.
keywords: ID-service
title: Implementatie aan de serverzijde gemengd met JavaScript
exl-id: 1986ee11-2021-4f34-bb56-6eaa87b6dd6d
source-git-commit: fa2549090e6790763a7ac6b87348789678d18ab6
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# Implementatie aan de serverzijde gemengd met JavaScript {#server-side-implementation-mixed-with-javascript}

In sommige implementaties worden bezoeker-id&#39;s doorgegeven van JavaScript naar een server, zodat extra Analytics-gebeurtenissen (zoals een aankoop) door de server kunnen worden verzonden.

De dienst API van identiteitskaart verstrekt de methodes, [ getMarketingCloudVisitorID ](../../library/get-set/getmcvid.md) en [ getAnalyticsVisitorID ](../../library/get-set/getanalyticsvisitorid.md), om de waarden terug te winnen van identiteitskaart die dan aan de server kunnen worden overgegaan.

Controleer of de bezoeker-id van het Experience Cloud en de bezoeker-id van Analytics zijn gecontroleerd en verzend beide id&#39;s (indien aanwezig) om te controleren of de verzonden gegevens zijn gekoppeld aan het bestaande profiel voor Analytics-bezoekers.

>[!IMPORTANT]
>
>AppMeasurement voor Java biedt momenteel geen ondersteuning voor de Experience Cloud Identity Service.

## API voor gegevensinvoer {#section-955ce7664a4646d38b3005cb2df40baf}

Neem de bezoeker-id voor Analytics (indien ingesteld) op in het element `<visitorID>` .

Neem de bezoeker-id van het Experience Cloud op in het element `<marketingCloudVisitorID>` .

Zie [ Gesteunde Markeringen van XML ](https://developer.adobe.com/).

## AppMeasurement voor Java {#section-d664b94934924d048300d9c2b6560085}

De Experience Cloud Identity Service wordt momenteel niet ondersteund door AppMeasurement voor Java.
