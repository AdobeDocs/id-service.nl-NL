---
description: Het AMCV-cookie bevat de Experience Cloud-id (MID) en een regio-id voor uw sitebezoekers. Deze id's worden opgeslagen als sleutelwaardeparen. De id van de middelste gebruiker bevat de Experience Cloud-id van de bezoeker. De naam van de regio-id bevat de regio-id voor uw sitebezoekers. U kunt deze informatie herstellen door het AMCV-cookie te parseren.
keywords: ID Service
seo-description: Het AMCV-cookie bevat de Experience Cloud-id (MID) en een regio-id voor uw sitebezoekers. Deze id's worden opgeslagen als sleutelwaardeparen. De id van de middelste gebruiker bevat de Experience Cloud-id van de bezoeker. De naam van de regio-id bevat de regio-id voor uw sitebezoekers. U kunt deze informatie herstellen door het AMCV-cookie te parseren.
seo-title: Regio en gebruikers-id's ophalen van de AMCV-cookie of de ID-service
title: Regio en gebruikers-id's ophalen van de AMCV-cookie of de ID-service
uuid: bdd9d001-f29f-4ff0-800b-8182243da218
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---


# Regio en gebruikers-id&#39;s ophalen van de AMCV-cookie of de ID-service {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

Het AMCV-cookie bevat de Experience Cloud-id (MID) en een regio-id voor uw sitebezoekers. Deze id&#39;s worden opgeslagen als sleutelwaardeparen. De id mid:user bevat de Experience Cloud-id van de bezoeker. De naam:regio-id bevat de regio-id voor uw sitebezoekers. U kunt deze informatie herstellen door het AMCV-cookie te parseren.

Voor meer informatie, zie [krijgen gebruikersidentiteitskaart en Gebieden door de Dienst](https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html)van de Identiteit van de Experience Cloud.

Als u een [!DNL Audience Manager] klant bent, kunt u gebiedsidentiteitskaart van de reactie krijgen die door de Server van de Inzameling van Gegevens (DCS) wordt verzonden. See [Get User IDs and Regions from a DCS Response](https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html).

U kunt de regio-id ook ophalen met een `GET` methode die wordt geleverd door de id-service. Zie Gebied-id&#39;s [ophalen (Locatiehint)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).
