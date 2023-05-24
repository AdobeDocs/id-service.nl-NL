---
description: Veelgestelde vragen over functies, functionaliteit en problemen met betrekking tot het gebruik van Analytics met de Experience Cloud Identity Service.
keywords: Experience Cloud Identity-service
title: Veelgestelde vragen over Analytics and Identity Service
exl-id: 98aeca0d-41a2-4b18-b307-19a6de816e38
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '970'
ht-degree: 1%

---

# Veelgestelde vragen over Analytics and Identity Service{#analytics-and-id-service-faqs}

Veelgestelde vragen over functies, functionaliteit en problemen met betrekking tot het gebruik van Analytics met de Identity Service.

## Servers bijhouden {#section-9a2ad7842e364c869e1650480d17f8ef}

**Hoe vind ik mijn het volgen serverinformatie?**

Elk behoorlijk gevormd stuk van code AppMeasurement bevat uw het volgen serverinformatie.

Soms kunnen klanten hun Analytics AppMeturement-bestand echter opsplitsen in afzonderlijke bestanden. Sommige klanten kunnen bijvoorbeeld configuratievariabelen in één bestand plaatsen, een tweede bestand voor plug-ins gebruiken en vervolgens AppMeasurement-code in een derde bestand plaatsen. Dit wordt niet aanbevolen.

Als u de gegevens van de trackingserver niet kunt vinden, is het mogelijk dat de instantie Analytics niet correct is geconfigureerd. Contact [Klantenservice](https://helpx.adobe.com/marketing-cloud/contact-support.html) als u de gegevens van de trackingserver niet kunt vinden.

**Wat gebeurt als ik de Dienst van de Identiteit gebruik en mijn het volgen server verander?**

Er verandert niets voor gebruikers die al door de identiteitsdienst zijn geïdentificeerd. Oudere bezoekers die niet naar de identiteitsdienst zijn gemigreerd en nog steeds met een Analytics-cookie zijn geïdentificeerd, worden uitgeknipt. Het aantal betrokken gebruikers zou afhangen van hoe lang de Dienst van de Identiteit actief is geweest. Zo kan een implementatie waarbij de identiteitsservice al één week actief is, meer verouderde gebruikers hebben dan een implementatie waarbij de identiteitsservice al zes maanden actief is omdat gebruikers die naar de site terugkeren, zijn gemigreerd.

## Implementatie en configuratie {#section-6028f55d5b514ae6a631c6a79f42fb89}

**Moet ik opstelling een NAAM om bezoekers over domeinen te volgen?**

Als u een hoofdinvoersite hebt waarop klanten kunnen worden geïdentificeerd voordat ze andere domeinen bezoeken, kan een CNAME het bijhouden van gegevens naar andere domeinen toestaan in browsers die cookies van derden (zoals Safari) niet accepteren.

In browsers die cookies van derden accepteren, wordt een cookie ingesteld in het dialoogvenster [demdex.net-domein](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html) tijdens de aanvraag om een bezoekersidentiteitskaart op te halen. Met dit cookie kan de Identity Service dezelfde Experience Cloud bezoeker-id retourneren op alle domeinen die zijn geconfigureerd met dezelfde organisatie-id. In browsers die cookies van derden afwijzen, wordt voor elk domein een nieuwe Experience Cloud-bezoeker-id toegewezen.

Zelfs wanneer een CNAME wordt gevormd, als de belangrijkste ingangsplaats niet eerst wordt bezocht, worden de bezoekers geïdentificeerd verschillend op de secundaire plaats en de belangrijkste plaats in browsers die derde koekjes niet goedkeuren.

**Waarom is de parameter van Experience Cloud ID (MID) niet in het verzoek Analytics?**

Als de Identiteitsdienst correct informatie terugkeert maar u ziet niet `MID` , zorgt u ervoor dat u een upgrade hebt uitgevoerd naar een ondersteunde versie van AppMeasurement.

**Kan mijn site H-code en AppMeasurement gebruiken voor JavaScript met de Identity Service?**

Ja. Zolang beide bestanden naar hetzelfde bestand VisitorAPI.js verwijzen, kunt u op uw site een combinatie van H-code en AppMeasurement voor JavaScript gebruiken.

H-code wordt echter niet ondersteund met de code bezoekerAPI.js versie 1.6 of hoger. Als u wilt upgraden naar bezoekerAPI.js v 1.6 (of hoger), kunt u niet doorgaan met het gebruik van H-code.

**Wat is een respijtperiode en hoe vorm ik het?**

Zie [De statusrespijtperiode van de identiteitsdienst](../reference/analytics-reference/grace-period.md) en contact opnemen [Klantenservice](https://helpx.adobe.com/marketing-cloud/contact-support.html).

**Waarom moet ik naar de Inzameling van Gegevens in real time (RDC) migreren om de Dienst van de Identiteit te gebruiken?**

De RDC biedt prestatievoordelen en is vereist om ervoor te zorgen dat uw implementatie gereed is voor de volgende functies die wereldwijd Adobe van randnotities kunnen benutten. Zie [Analysevereisten: Regionale gegevensverzameling (RDC)](../reference/requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f).

## Rapportage {#section-123cd55a32e54a45a23beb140becfa8f}

**Wat zijn enkele mogelijke oorzaken van discrepanties wanneer Analytics met de Dienst van de Identiteit wordt gebruikt?**

Veelvoorkomende oorzaken van verschillen bij het gebruik van de identiteitsdienst zijn:

* Doorgaan met gebruik van het verouderde s_vi cookie. Dit draagt bij tot discrepanties in de gegevensverzameling.
* Bezoekers dubbeltellen wanneer ze van een enquête naar een pop-up gaan.

## Cookies {#section-b7d5384fbedd47b09e1030211c39a3d1}

**Wat gebeurt er in Analytics wanneer de Identity Service het AMCV-cookie niet kan instellen?**

Er zijn drie mogelijke scenario&#39;s waarbij dit van invloed is op de analysegegevens voor nieuwe bezoekers:

1. Een eindgebruiker verlaat een pagina voordat de AMCV-cookies correct zijn ingesteld (binnen het 30-tweede time-outvenster).

   Als een bezoeker een pagina verlaat voordat deze klaar is met laden, wordt de hit Analytics niet verzonden. Analytics zal geen gegevens van dit scenario ontvangen en zou van mening zijn dat de gegevens aan een vroege sluiting van de pagina verloren gaan. Op basis van onze tests, die ook betrekking hadden op perifere gebieden, hebben we vastgesteld dat dit scenario gemiddeld minder dan 1 procent van het verkeer vertegenwoordigde. Het is belangrijk om op te merken dat dit scenario soms zelfs zonder de aanwezigheid van de Dienst van de Identiteit voorkomt - het is een artefact van de opneming van de de gegevensverzamelingscode van de Analytics bij de bodem van de pagina.

1. Aan een eindgebruiker wordt geen identiteitsservice of analyse-id toegewezen binnen het tweede time-outvenster van 30 wegens langzame verbindingen of het &#39;draaien&#39; van de browser.

   Zowel zouden de Dienst van de Identiteit als identiteitskaart van de Analyse niet worden geplaatst en de bezoeker zou een cliënt-zijidentiteitskaart worden toegewezen. Hierdoor kunnen analysegegevens worden vastgelegd, maar het profiel van de bezoeker wordt onderbroken wanneer op een volgende pagina een Analytics-id wordt ingesteld. De client-side id komt ook niet overeen met een bestaand bezoekersprofiel dat is opgeslagen in Audience Manager of Analytics. Deze client-side id wordt ook weergegeven als twee verschillende bezoekers in Analytics als twee aparte domeinen naar dezelfde rapportsuite worden verzonden.

1. Aan een eindgebruiker wordt geen id voor Identiteitsservice toegewezen binnen het 30-tweede time-outvenster, maar er wordt een standaard Analytics tracking-id toegewezen en de respijtperiode is niet ingeschakeld.

   Scenario 3 heeft het zelfde resultaat aan scenario 2 in die zin dat op cliënt-kant gebaseerde identiteitskaart wordt gebruikt.

>[!TIP]
>
>Als u de meest recente updates van VisitorAPI.js en AppMeasurement.js met de standaardinstellingen gebruikt, voorkomt u ernstige of merkbare gevolgen van de drie bovenstaande onwaarschijnlijke scenario&#39;s.

>[!MORELIKETHIS]
>
>* [Klantenservice](https://helpx.adobe.com/marketing-cloud/contact-support.html)

