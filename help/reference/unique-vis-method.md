---
title: Unieke bezoekers identificeren
description: Documentatie voor Adobe ECID (ID-service)
exl-id: 379dbf0a-814d-4348-9ac4-d0e8fc13b9dc
source-git-commit: c65816530ae2269b216f60b9b0450077e5aaac2f
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# Unieke bezoekers identificeren

De methode voor het identificeren van unieke bezoekers onder meerdere contexten omvat een volgorde met prioriteit om ervoor te zorgen dat deze bepaling accuraat is. In de volgende tabel wordt deze volgorde met prioriteit weergegeven:

| Volgorde gebruikt | Query, parameter (verzamelingsmethode) | post_visid_type, kolomwaarde | Presenteren wanneer |
|---|---|---|---|
|  1  | vid [ s.bezoekorID ](https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/visitorid.html?lang=en)  | 0  | `s.visitorID` is ingesteld. |
|  2  | steun  [ s_vi koekje ](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=en#section-5d50a078de444d12b7d927d68ff3b679)  | 3  | De bezoeker had een bestaand s_vi- koekje alvorens u de dienst van identiteitskaart van de Bezoeker opstelde, of u hebt een Gelijkgestelde periode van de Verhoging van identiteitskaart van de Bezoeker [&#128279;](https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/grace-period.html?lang=en) gevormd.  |
|  3  | mid [ AMCV_cookie die door de Dienst van de Identiteit wordt geplaatst ](../introduction/cookies.md)  |  5  |  De browser van de bezoeker accepteert cookies (eerste partij) en de [!DNL Identity Service] wordt geïmplementeerd.  |
|  4  | fid [ fallback koekje op H.25.3 of nieuwer, of AppMeasurement voor JavaScript ](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=en#section-65e33f9bfc264959ac1513e2f4b10ac7)  |  4  |  De browser van de bezoeker accepteert cookies (eerste partij).  |
|  5  |  [ de Mobiele kopbal van de Abonnee van HTTP ](https://experienceleague.adobe.com/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-reference.html?lang=en)  |  2  |  Apparaat wordt herkend als een mobiel apparaat.  |
|  6  |  [ IP Adres, de Agent van de Gebruiker, IP van de Gateway Adres ](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=en)  |  1  |  De browser van de bezoeker accepteert geen cookies. |

{style="table-layout:auto"}

Voor informatie over hoe de unieke bezoekers worden gemeld, zie [ Unieke Bezoekers in Analytics ](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=en).
