---
title: Unieke bezoekers identificeren
description: Documentatie voor Adobe ECID (ID-service)
translation-type: tm+mt
source-git-commit: dee27fb0150ce2c40f570f98b9af0b6904c16814

---


# Unieke bezoekers identificeren

De methode voor het identificeren van unieke bezoekers onder meerdere contexten omvat een volgorde met prioriteit om ervoor te zorgen dat deze bepaling accuraat is. In de volgende tabel wordt deze volgorde met prioriteit weergegeven:
 
| Gebruikte order | Query-parameter (verzamelingsmethode) | kolomwaarde post_visid_type | Aanwezig wanneer |
|— |— |— |— |
| 1 |[vid (s.bezoekerID)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_custom.html)| 0 |s.bezoekerID is ingesteld.|
| 2 |[aid (s_vi cookie)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_analytics.html)| 3 |Bezoeker had een bestaand s_vi cookie voordat u de Bezoeker ID-service implementeerde of u hebt een[evaluatieperiode](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid_grace_period.html)voor de bezoeker geconfigureerd. |
| 3 |[mid (AMCV_ cookie set by Identity Service)](https://marketing.adobe.com/resources/help/en_US/mcvid/)| 5 | De browser van de bezoeker accepteert cookies (first party) en de Identity Service wordt geïmplementeerd. |
| 4 |[fid (fallback-cookie op H.25.3 of hoger, of AppMeasurement voor JavaScript)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_fallback.html)| 4 | De browser van de bezoeker accepteert cookies (first-party). |
| 5 |[HTTP Mobile Subscriber header](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_mobile.html)| 2 | Apparaat wordt herkend als mobiel apparaat. |
| 6 |[IP Adres, de Agent van de Gebruiker, IP van de Gateway Adres](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_fallback.html)| 1 | browser van de bezoeker keurt geen koekjes goed. |

Zie [Unieke bezoekers in Analytics](https://docs.adobe.com/content/help/en/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html)voor informatie over de rapportage van unieke bezoekers.
