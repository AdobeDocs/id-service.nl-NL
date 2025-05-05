---
description: Deze instructies gelden voor klanten van Analytics die de Experience Cloud Identity Service willen gebruiken en geen labels voor gegevensverzameling gebruiken. Nochtans, adviseren wij sterk dat u markeringen gebruikt om de dienst van identiteitskaart uit te voeren. Met labels wordt de implementatieworkflow gestroomlijnd en wordt automatisch de juiste plaatsing van code en de juiste volgorde gegarandeerd.
keywords: ID-service
title: Implementeer de dienst Identiteit Experience Cloud voor Analytics
exl-id: c0271e49-32e5-49ee-bb11-548751ccafad
source-git-commit: 792fb5d5192843f345577a99b6179fb6d95fedc0
workflow-type: tm+mt
source-wordcount: '996'
ht-degree: 0%

---

# Implementeer de dienst Identiteit Experience Cloud voor Analytics {#implement-the-experience-cloud-id-service-for-analytics}

Deze instructies zijn voor klanten Analytics die de Dienst van de Identiteit van het Experience Cloud willen gebruiken en [ geen markeringen van de Inzameling van Gegevens ](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl-NL) gebruiken. Nochtans, adviseren wij sterk dat u markeringen gebruikt om de dienst van identiteitskaart uit te voeren. Met labels wordt de implementatieworkflow gestroomlijnd en wordt automatisch de juiste plaatsing van code en de juiste volgorde gegarandeerd.

>[!IMPORTANT]
>
>* [ leest de vereisten ](../reference/requirements.md) alvorens u begint.
>* Vorm en test deze code in een ontwikkelomgeving alvorens het in productie uit te voeren.

Voer de volgende stappen uit om de id-service voor Adobe Analytics te implementeren:

1. [ Download de code van de Dienst van identiteitskaart ](../implementation-guides/setup-analytics.md#section-ead9403a6b7e45b887f9ac959ef89f7f)
1. [ voeg de functie Visitor.getInstance aan de Code van de Dienst van identiteitskaart toe ](../implementation-guides/setup-analytics.md#section-6053a6b7c16c466a9f9fdbf9cb9db3df)
1. [ voeg uw identiteitskaart van de Organisatie van het Experience Cloud aan Visitor.getInstance ](../implementation-guides/setup-analytics.md#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e) toe
1. [ voeg uw volgende servers aan Visitor.getInstance ](../implementation-guides/setup-analytics.md#section-70ec9ebff47940d8ab520be5ec4728c5) toe
1. [ werk uw AppMeasurement.js of s_code.js- dossier ](../implementation-guides/setup-analytics.md#section-b53113aea1bd4de896e0e4e9a7edee19) bij
1. [ voeg de code van Bezoeker API aan de pagina toe ](../implementation-guides/setup-analytics.md#section-d46d6aa324c842f2931d901e38d6db1d)
1. [ (Optioneel) Configureer een respijtperiode ](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3)
1. [ID-servicecode testen en implementeren](../implementation-guides/setup-analytics.md#section-e9c1764ac21a4ec5be1ff338c0e2e01b)

## Stap 1: Download de ID Service-code {#section-ead9403a6b7e45b887f9ac959ef89f7f}

Voor [!UICONTROL ID Service] is de codebibliotheek van `VisitorAPI.js` vereist. Deze codebibliotheek downloaden:

1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Code Manager]** .
1. Klik in [!UICONTROL Code Manager] op **[!UICONTROL JavaScript (New)]** of **[!UICONTROL JavaScript (Legacy)]** .

   Hiermee worden gecomprimeerde codebibliotheken gedownload.

1. Decomprimeer het codebestand en open het `VisitorAPI.js` -bestand.

## Stap 2. Voeg de functie Visitor.getInstance aan de Code van de Dienst van identiteitskaart toe {#section-6053a6b7c16c466a9f9fdbf9cb9db3df}

>[!IMPORTANT]
>
>* Eerdere versies van de id service-API hebben deze functie op een andere locatie geplaatst en een andere syntaxis vereist. Als u van een versie voorafgaand aan [ versie 1.4 ](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572) migreert, neem nota van de nieuwe die plaatsing en syntaxis hier wordt gedocumenteerd.
>* Code in ALL CAPS is een plaatsaanduiding voor werkelijke waarden. Vervang deze tekst door uw organisatie-id, URL van trackingserver of een andere benoemde waarde.

**Deel 1: Kopieer hieronder de functie Visitor.getInstance**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

**Deel 2: Voeg functiecode aan het VisitorAPI.js- dossier** toe

Plaats de functie `Visitor.getInstance` aan het einde van het bestand na het codeblok. Het bewerkte bestand moet er als volgt uitzien:

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library

var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

## Stap 3: Voeg uw identiteitskaart van de Organisatie van het Experience Cloud aan Visitor.getInstance toe {#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e}

Vervang `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` in de functie [!DNL Experience Cloud] door uw organisatie-id. `Visitor.getInstance` Als u uw organisatie-id niet kent, vindt u deze op de beheerpagina van [!DNL Experience Cloud] . Zie ook, [ Beleid - de Diensten van de Kern ](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html?lang=nl-NL). De bewerkte functie kan er ongeveer zo uitzien als het onderstaande voorbeeld.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*verander niet* het geval van de karakters in uw organisatieidentiteitskaart De id is hoofdlettergevoelig en moet precies worden gebruikt zoals opgegeven.

## Stap 4: Voeg uw volgende servers aan Visitor.getInstance toe {#section-70ec9ebff47940d8ab520be5ec4728c5}

Trackingservers worden gebruikt voor [!DNL Analytics] gegevensverzameling.

**Deel 1: Vind uw het volgen server URLs**

Controleer uw `s_code.js` - of `AppMeasurement.js` -bestanden om de URL&#39;s van de trackingserver te zoeken. U wilt de URL&#39;s die door deze variabelen worden opgegeven:

* `s.trackingServer`
* `s.trackingServerSecure`

**Deel 2: Plaats volgende servervariabelen**

Om te bepalen welke volgende servervariabelen moeten worden gebruikt:

1. Beantwoord de vragen in de onderstaande beslissingsmatrix. Gebruik de variabelen die overeenkomen met uw antwoorden.
1. Vervang de plaatsaanduidingen van de trackingserver door de URL&#39;s van de trackingserver.
1. Verwijder ongebruikte trackingserver en [!DNL Experience Cloud] servervariabelen uit de code.

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>Wanneer u de URL&#39;s van de [!DNL Experience Cloud] -server gebruikt, moet u deze als volgt afstemmen op de URL&#39;s van de bijbehorende URL van de volgende server:
>
>* [!DNL Experience Cloud] server-URL = URL van traceringsserver
>* [!DNL Experience Cloud] beveiligde URL van server = beveiligde URL van server bijhouden

Als u niet zeker bent hoe te om uw het volgen server te vinden [ FAQ ](../faq-intro/faq.md) ziet en [ bevolkt correct de variabelen trackingServer en trackingServerSecure ](https://helpx.adobe.com/nl/analytics/kb/determining-data-center.html#).

## Stap 5: Werk uw AppMeasurement.js of s_code.js- dossier bij {#section-b53113aea1bd4de896e0e4e9a7edee19}

Voeg deze functie toe aan uw `AppMeasurement.js` - of `s_code.js` -bestand:

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

Plaats de code in dezelfde sectie die configuraties bevat, zoals `linkInternalFilters` , `charSet` , `trackDownloads` , enz.

***(Optioneel maar aanbevolen)* Een aangepaste proxy maken &#x200B;**

Stel een aangepaste proxy in `AppMeasurement.js` of `s_code.js` in om de dekking te meten. Voeg deze aangepaste proxy toe aan de functie `doPlugins` van uw `AppMeasurement.js` - of `s_code.js` -bestanden:

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## Stap 6: Bezoeker-API-code toevoegen aan de pagina {#section-d46d6aa324c842f2931d901e38d6db1d}

Plaats het bestand `VisitorAPI.js` binnen de tags `<head>` op elke pagina. Wanneer u het `VisitorAPI.js` -bestand op de pagina plaatst:

* Plaats deze aan het begin van de sectie `<head>` , zodat deze voor andere oplossingstags wordt weergegeven.
* Deze moet worden uitgevoerd vóór AppMeasurement en de code voor andere [!DNL Experience Cloud] -oplossingen.

Verplaats deze code naar productie na het testen en controleren.

## Stap 7: (Optioneel) Configureer een evaluatieperiode {#section-7bbb2f72c26e4abeb8881e18366797a3}

Als om het even welk van deze gebruiksgevallen op uw situatie van toepassing zijn, vraag [&#128279;](https://helpx.adobe.com/nl/marketing-cloud/contact-support.html) de Zorg van de Klant om een tijdelijke [ respijtperiode ](../reference/analytics-reference/grace-period.md) te vestigen.  Respijtperioden kunnen maximaal 180 dagen duren. U kunt een respijtperiode verlengen als dat nodig is.

**Gedeeltelijke Implementatie**

U hebt een respijtperiode nodig als u sommige pagina&#39;s gebruikt die de id-service gebruiken en sommige pagina&#39;s dat niet doen, en deze allemaal in dezelfde [!DNL Analytics] -rapportsuite rapporteren. Dit komt vaak voor als u een algemene rapportsuite hebt die rapporten opstelt in verschillende domeinen.

Sluit de respijtperiode af nadat de id-service is geïmplementeerd op al uw webpagina&#39;s die in dezelfde rapportsuite rapporteren.

**s_vi de Vereisten van het Koekje**

U hebt een respijtperiode nodig als u nieuwe bezoekers een s_vi koekje na het migreren aan de dienst van identiteitskaart wilt hebben. Dit is algemeen als uw implementatie het s_vi koekje leest en het in een variabele opslaat.

Sluit de respijtperiode af nadat uw implementatie de MID kan vastleggen in plaats van het s_vi cookie te lezen.

Zie, [ Cookies en de Dienst van de Identiteit van het Experience Cloud ](../introduction/cookies.md).

U hebt een respijtperiode nodig als u gegevens naar een intern systeem verzendt vanuit een Clickstream-gegevensfeed en die processen de kolommen `visid_high` en `visid_low` gebruiken.

Sluit de respijtperiode af nadat de kolommen `post_visid_high` en `post_visid_low` door het gegevensinvoerproces kunnen worden gebruikt.

Zie, {de Verwijzing van de Kolom van Gegevens 0} Clikstream [&#128279;](https://experienceleague.adobe.com/docs/analytics/export/analytics-data-feed/data-feed-overview.html?lang=nl-NL).

**Ingestie van Gegevens Clickstream**

## Stap 8: Test en implementeer ID-servicecode {#section-e9c1764ac21a4ec5be1ff338c0e2e01b}

U kunt als volgt testen en opstellen.

**Test en verifieer**

Als u de implementatie van uw id-service wilt testen, controleert u op het volgende:

* [ het koekje van AMCV ](../introduction/cookies.md) in het domein waar uw pagina wordt ontvangen.
* MID waarde in het [!DNL Analytics] beeldverzoek met het [ debugger hulpmiddel van de Adobe ](https://experienceleague.adobe.com/docs/analytics/implementation/validate/debugger.html?lang=nl-NL).

Zie, [ Test en verifieer de Dienst van de Identiteit van het Experience Cloud ](../implementation-guides/test-verify.md).

**stel code** op

Implementeer de code nadat deze voor het testen is geslaagd.

Als u een respijtperiode in [ Stap 7 ](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3) toeliet:

* Zorg ervoor dat de velden voor [!DNL Analytics] ID (AID) en MID zich in de afbeeldingsaanvraag bevinden.
* Vergeet niet de respijtperiode uit te schakelen wanneer u voldoet aan de criteria voor stopzetting.
