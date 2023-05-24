---
title: Unieke bezoekers identificeren
description: Documentatie voor Adobe ECID (ID-service)
exl-id: 379dbf0a-814d-4348-9ac4-d0e8fc13b9dc
source-git-commit: c65816530ae2269b216f60b9b0450077e5aaac2f
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 4%

---

# Unieke bezoekers identificeren

De methode voor het identificeren van unieke bezoekers onder meerdere contexten omvat een volgorde met prioriteit om ervoor te zorgen dat deze bepaling accuraat is. In de volgende tabel wordt deze volgorde met prioriteit weergegeven:

| Volgorde gebruikt | Query, parameter (verzamelingsmethode) | post_visid_type, kolomwaarde | Presenteren wanneer |
|---|---|---|---|
|  1  | vid [s.bezoekerID](https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/visitorid.html?lang=en)  | 0  | `s.visitorID` is ingesteld. |
|  2  | steun  [s_vi cookie](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=en#section-5d50a078de444d12b7d927d68ff3b679)  | 3  | De bezoeker had een bestaand s_vi koekje alvorens u de dienst van identiteitskaart van de Bezoeker uitvoerde, of u hebt Bezoeker identiteitskaart [respijtperiode](https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/grace-period.html?lang=en) geconfigureerd.  |
|  3  | midden [AMCV_ cookie ingesteld door Identity Service](../introduction/cookies.md)  |  5  |  De browser van de bezoeker accepteert cookies (van de eerste partij) en de [!DNL Identity Service] wordt geïmplementeerd.  |
|  4  | fid [fallback-cookie op H.25.3 of hoger, of AppMeasurement voor JavaScript](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=en#section-65e33f9bfc264959ac1513e2f4b10ac7)  |  4  |  De browser van de bezoeker accepteert cookies (van de eerste partij).  |
|  5  |  [HTTP Mobile Subscriber header](https://experienceleague.adobe.com/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-reference.html?lang=en)  |  2  |  Apparaat wordt herkend als een mobiel apparaat.  |
|  6  |  [IP Adres, de Agent van de Gebruiker, IP van de Gateway Adres](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=en)  |  1  |  De browser van de bezoeker accepteert geen cookies. |

{style="table-layout:auto"}

Voor informatie over de manier waarop unieke bezoekers worden gerapporteerd, raadpleegt u [Unieke bezoekers in Analytics](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=en).
