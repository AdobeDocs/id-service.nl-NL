---
title: Unieke bezoekers identificeren
description: Documentatie voor Adobe ECID (ID-service)
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Unieke bezoekers identificeren

De methode voor het identificeren van unieke bezoekers onder meerdere contexten omvat een volgorde met prioriteit om ervoor te zorgen dat deze bepaling accuraat is. In de volgende tabel wordt deze volgorde met prioriteit weergegeven:
 
| Gebruikte order | Query-parameter (verzamelingsmethode) | kolomwaarde post_visid_type | Aanwezig wanneer |
|— |— |— |— |
| 1 |[vid (s.bezoekerID)](https://docs.adobe.com/content/help/en/analytics/technotes/visitor-identification.html)| 0 |s.bezoekerID is ingesteld.|
| 2 |[aid (s_vi cookie)](https://docs.adobe.com/content/help/en/analytics/technotes/visitor-identification.html)| 3 |Bezoeker had een bestaand s_vi cookie voordat u de Bezoeker ID-service implementeerde of u hebt een[evaluatieperiode](https://docs.adobe.com/content/help/en/id-service/using/reference/analytics-reference/grace-period.html)voor de bezoeker geconfigureerd. |
| 3 |[mid (AMCV_ cookie set by Identity Service)](https://docs.adobe.com/content/help/en/id-service/using/home.html)| 5 | De browser van de bezoeker accepteert cookies (first party) en de Identity Service wordt geïmplementeerd. |
| 4 |[fid (fallback-cookie op H.25.3 of hoger, of AppMeasurement voor JavaScript)](https://docs.adobe.com/content/help/en/analytics/technotes/visitor-identification.html)| 4 | De browser van de bezoeker accepteert cookies (first-party). |
| 5 |[HTTP Mobile Subscriber header](https://docs.adobe.com/content/help/en/analytics/technotes/visitor-identification.html)| 2 | Apparaat wordt herkend als mobiel apparaat. |
| 6 |[IP Adres, de Agent van de Gebruiker, IP van de Gateway Adres](https://docs.adobe.com/content/help/en/analytics/technotes/visitor-identification.html)| 1 | browser van de bezoeker keurt geen koekjes goed. |

Zie [Unieke bezoekers in Analytics](https://docs.adobe.com/content/help/en/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html)voor informatie over de rapportage van unieke bezoekers.
