---
title: Unieke bezoekers identificeren
description: Documentatie voor Adobe ECID (ID-service)
translation-type: tm+mt
source-git-commit: 8ad5ae179540596913fccc59070aecc57b09f586
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 9%

---


# Unieke bezoekers identificeren

De methode voor het identificeren van unieke bezoekers onder meerdere contexten omvat een volgorde met prioriteit om ervoor te zorgen dat deze bepaling accuraat is. In de volgende tabel wordt deze volgorde met prioriteit weergegeven:

| Volgorde gebruikt | Query, parameter (verzamelingsmethode) | post_visid_type, kolomwaarde | Presenteren wanneer |
|---|---|---|---|
|  1  | vid[s.bezoekerID](https://docs.adobe.com/content/help/en/analytics/technotes/visitor-identification.html)  | 0  | `s.visitorID` is ingesteld. |
|  2  | aid[s_vi cookie](https://docs.adobe.com/content/help/en/analytics/technotes/visitor-identification.html)  | 3  | De bezoeker had een bestaand s_vi koekje alvorens u de dienst van identiteitskaart van de Bezoeker uitvoerde, of u hebt een de[gratieperiode](https://docs.adobe.com/content/help/en/id-service/using/reference/analytics-reference/grace-period.html)van identiteitskaart van de Bezoeker gevormd.  |
|  3  | mid[AMCV_ cookie ingesteld door Identity Service](https://docs.adobe.com/content/help/en/id-service/using/home.html)  |  5  |  De browser van de bezoeker accepteert cookies (first-party) en de browser[!UICONTROL Identity Service]wordt geïmplementeerd.  |
|  4  | fid-[fallback-cookie op H.25.3 of hoger, of AppMeasurement voor JavaScript](https://docs.adobe.com/content/help/en/analytics/technotes/visitor-identification.html)  |  4  |  De browser van de bezoeker accepteert cookies (van de eerste partij).  |
|  5  |  [HTTP Mobile Subscriber header](https://docs.adobe.com/content/help/en/analytics/technotes/visitor-identification.html)  |  2  |  Apparaat wordt herkend als een mobiel apparaat.  |
|  6  |  [IP Adres, de Agent van de Gebruiker, IP van de Gateway Adres](https://docs.adobe.com/content/help/en/analytics/technotes/visitor-identification.html)  |  1  |  De browser van de bezoeker accepteert geen cookies. |

Zie [Unieke bezoekers in Analytics](https://docs.adobe.com/content/help/en/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html)voor informatie over de rapportage van unieke bezoekers.
