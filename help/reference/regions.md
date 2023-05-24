---
description: Het AMCV-cookie bevat de Experience Cloud-id (MID) en een regio-id voor uw sitebezoekers. Deze id's worden opgeslagen als sleutelwaardeparen. De id van de middelste gebruiker bevat de Experience Cloud-id van de bezoeker. De naam van de regio-id bevat de regio-id voor uw sitebezoekers. U kunt deze informatie herstellen door het AMCV-cookie te parseren.
keywords: ID-service
title: Regio en gebruikers-id's ophalen van de AMCV-cookie of de ID-service
exl-id: 986e761e-4bc7-4511-86b7-7d13a7761a2b
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Regio en gebruikers-id&#39;s ophalen van de AMCV-cookie of de ID-service {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

Het AMCV-cookie bevat de Experience Cloud-id (MID) en een regio-id voor uw sitebezoekers. Deze id&#39;s worden opgeslagen als sleutelwaardeparen. De id mid:user bevat de Experience Cloud-id van de bezoeker. De naam:regio-id bevat de regio-id voor uw sitebezoekers. U kunt deze informatie herstellen door het AMCV-cookie te parseren.

Zie voor meer informatie [Gebruikersnaam en regio&#39;s ophalen via de Experience Cloud Identity Service](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html).

Als je een [!DNL Audience Manager] klant, kunt u gebiedsidentiteitskaart van de reactie krijgen die door de Server van de Inzameling van Gegevens (DCS) wordt verzonden. Zie [Gebruikersnaam en regio&#39;s ophalen van een DCS-reactie](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html).

U kunt de regio-id ook ophalen met een `GET` door de id-service opgegeven methode. Zie [Gebied-id&#39;s ophalen (locatiehint)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).
