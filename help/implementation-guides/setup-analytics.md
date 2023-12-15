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

Deze instructies gelden voor klanten van Analytics die de Experience Cloud Identity Service willen gebruiken en niet [Labels voor gegevensverzameling](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en). Nochtans, adviseren wij sterk dat u markeringen gebruikt om de dienst van identiteitskaart uit te voeren. Met labels wordt de implementatieworkflow gestroomlijnd en wordt automatisch de juiste plaatsing van code en de juiste volgorde gegarandeerd.

>[!IMPORTANT]
>
>* [Lees de vereisten](../reference/requirements.md) voordat u begint.
>* Vorm en test deze code in een ontwikkelomgeving alvorens het in productie uit te voeren.

Voer de volgende stappen uit om de id-service voor Adobe Analytics te implementeren:

1. [De ID-servicecode downloaden](../implementation-guides/setup-analytics.md#section-ead9403a6b7e45b887f9ac959ef89f7f)
1. [Voeg de functie Visitor.getInstance aan de Code van de Dienst van identiteitskaart toe](../implementation-guides/setup-analytics.md#section-6053a6b7c16c466a9f9fdbf9cb9db3df)
1. [Voeg uw identiteitskaart van de Organisatie van het Experience Cloud aan Visitor.getInstance toe](../implementation-guides/setup-analytics.md#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e)
1. [Voeg uw volgende servers aan Visitor.getInstance toe](../implementation-guides/setup-analytics.md#section-70ec9ebff47940d8ab520be5ec4728c5)
1. [Het bestand AppMeasurement.js of s_code.js bijwerken](../implementation-guides/setup-analytics.md#section-b53113aea1bd4de896e0e4e9a7edee19)
1. [API-code van bezoeker toevoegen aan de pagina](../implementation-guides/setup-analytics.md#section-d46d6aa324c842f2931d901e38d6db1d)
1. [(Optioneel) Configureer een respijtperiode](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3)
1. [ID-servicecode testen en implementeren](../implementation-guides/setup-analytics.md#section-e9c1764ac21a4ec5be1ff338c0e2e01b)

## Stap 1: Download de ID Service-code {#section-ead9403a6b7e45b887f9ac959ef89f7f}

De [!UICONTROL ID Service] vereist `VisitorAPI.js` codebibliotheek. Deze codebibliotheek downloaden:

1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Code Manager]**.
1. In [!UICONTROL Code Manager]Klik op een van de **[!UICONTROL JavaScript (New)]** of **[!UICONTROL JavaScript (Legacy)]**.

   Hiermee worden gecomprimeerde codebibliotheken gedownload.

1. Het codebestand decomprimeren en het dialoogvenster `VisitorAPI.js` bestand.

## Stap 2. Voeg de functie Visitor.getInstance aan de Code van de Dienst van identiteitskaart toe {#section-6053a6b7c16c466a9f9fdbf9cb9db3df}

>[!IMPORTANT]
>
>* Eerdere versies van de id service-API hebben deze functie op een andere locatie geplaatst en een andere syntaxis vereist. Als u migreert op basis van een eerdere versie dan [versie 1.4](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572), let op de nieuwe plaatsing en syntaxis die hier wordt gedocumenteerd.
>* Code in ALL CAPS is een plaatsaanduiding voor werkelijke waarden. Vervang deze tekst door uw organisatie-id, URL van trackingserver of een andere benoemde waarde.

**Deel 1: Kopieer de functie Visitor.getInstance hieronder**

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

**Deel 2: Functiecode toevoegen aan het bestand VisitorAPI.js**

Plaats de `Visitor.getInstance` aan het einde van het bestand na het codeblok. Het bewerkte bestand moet er als volgt uitzien:

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

In de `Visitor.getInstance` functie, vervangen `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` met uw [!DNL Experience Cloud] organisatie-id. Als u uw organisatie-id niet kent, kunt u deze vinden op de [!DNL Experience Cloud] beheerpagina. Zie ook: [Beheer - Core Services](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html). De bewerkte functie kan er ongeveer zo uitzien als het onderstaande voorbeeld.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*Niet gebruiken* Wijzig het hoofdlettergebruik van de tekens in uw organisatie-id. De id is hoofdlettergevoelig en moet precies worden gebruikt zoals opgegeven.

## Stap 4: Voeg uw volgende servers aan Visitor.getInstance toe {#section-70ec9ebff47940d8ab520be5ec4728c5}

Trackingservers worden gebruikt voor [!DNL Analytics] gegevensverzameling.

**Deel 1: Zoeken naar URL&#39;s van uw trackingserver**

Controleer uw `s_code.js` of `AppMeasurement.js` bestanden om de URL&#39;s van de trackingserver te zoeken. U wilt de URL&#39;s die door deze variabelen worden opgegeven:

* `s.trackingServer`
* `s.trackingServerSecure`

**Deel 2: Set tracking server variables**

Om te bepalen welke volgende servervariabelen moeten worden gebruikt:

1. Beantwoord de vragen in de onderstaande beslissingsmatrix. Gebruik de variabelen die overeenkomen met uw antwoorden.
1. Vervang de plaatsaanduidingen van de trackingserver door de URL&#39;s van de trackingserver.
1. Ongebruikte trackingserver verwijderen en [!DNL Experience Cloud] servervariabelen uit de code.

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>Indien gebruikt, aanpassen [!DNL Experience Cloud] server-URL&#39;s naar de overeenkomstige URL&#39;s van de volgende server:
>
>* [!DNL Experience Cloud] server-URL = URL van traceringsserver
>* [!DNL Experience Cloud] server secure URL = tracking server secure URL

Als u niet zeker bent hoe te om uw het volgen server te vinden zie [Veelgestelde vragen](../faq-intro/faq.md) en [De variabelen trackingServer en trackingServerSecure correct vullen](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).

## Stap 5: Werk uw AppMeasurement.js of s_code.js- dossier bij {#section-b53113aea1bd4de896e0e4e9a7edee19}

Deze functie toevoegen aan uw `AppMeasurement.js` of `s_code.js` bestand:

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

Plaats de code in dezelfde sectie die configuraties bevat zoals `linkInternalFilters`, `charSet`, `trackDownloads`, enz.

***(Optioneel, maar aanbevolen)* Een aangepaste proxy maken **

Aangepaste proxy instellen in `AppMeasurement.js` of `s_code.js` om de dekking te meten. Deze aangepaste proxy toevoegen aan de `doPlugins` functie van uw `AppMeasurement.js` of `s_code.js` bestanden:

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## Stap 6: Bezoeker-API-code toevoegen aan de pagina {#section-d46d6aa324c842f2931d901e38d6db1d}

Plaats de `VisitorAPI.js` bestand in het `<head>` -tags op elke pagina. Wanneer u `VisitorAPI.js` bestand naar uw pagina:

* Zet het aan het begin van `<head>` voor andere oplossingstags.
* Het moet vóór AppMeasurement en de code voor andere uitvoeren [!DNL Experience Cloud] oplossingen.

Verplaats deze code naar productie na het testen en controleren.

## Stap 7: (Optioneel) Configureer een evaluatieperiode {#section-7bbb2f72c26e4abeb8881e18366797a3}

Als een van deze gebruiksgevallen op uw situatie van toepassing is, raadpleegt u [Klantenservice](https://helpx.adobe.com/marketing-cloud/contact-support.html) een tijdelijke [respijtperiode](../reference/analytics-reference/grace-period.md). Respijtperioden kunnen maximaal 180 dagen duren. U kunt een respijtperiode verlengen als dat nodig is.

**Gedeeltelijke implementatie**

U hebt een respijtperiode nodig als u sommige pagina&#39;s hebt die de id-service gebruiken en sommige pagina&#39;s die dat niet doen, en ze allemaal in dezelfde pagina rapporteren [!DNL Analytics] rapportsuite. Dit komt vaak voor als u een algemene rapportsuite hebt die rapporten opstelt in verschillende domeinen.

Sluit de respijtperiode af nadat de id-service is geïmplementeerd op al uw webpagina&#39;s die in dezelfde rapportsuite rapporteren.

**S_vi Cookie-vereisten**

U hebt een respijtperiode nodig als u nieuwe bezoekers een s_vi koekje na het migreren aan de dienst van identiteitskaart wilt hebben. Dit is algemeen als uw implementatie het s_vi koekje leest en het in een variabele opslaat.

Sluit de respijtperiode af nadat uw implementatie de MID kan vastleggen in plaats van het s_vi cookie te lezen.

Zie, [Cookies en de identiteitsservice van Experiencen Cloud](../introduction/cookies.md).

U hebt een respijtperiode nodig als u gegevens naar een intern systeem verzendt vanuit een Clickstream-gegevensinvoer en die processen het `visid_high` en `visid_low` kolommen.

De respijtperiode beëindigen nadat het proces voor het invoeren van gegevens de `post_visid_high` en `post_visid_low` kolommen.

Zie, [Referentie kolom Clickstream](https://experienceleague.adobe.com/docs/analytics/export/analytics-data-feed/data-feed-overview.html).

**Clickstream-gegevensinsluiting**

## Stap 8: Test en implementeer ID-servicecode {#section-e9c1764ac21a4ec5be1ff338c0e2e01b}

U kunt als volgt testen en opstellen.

**Testen en verifiëren**

Als u de implementatie van uw id-service wilt testen, controleert u op het volgende:

* [AMCV cookie](../introduction/cookies.md) in het domein waar uw pagina wordt gehost.
* MID-waarde in het dialoogvenster [!DNL Analytics] afbeeldingsverzoek met de [Adobe-foutopsporingsprogramma](https://experienceleague.adobe.com/docs/analytics/implementation/validate/debugger.html).

Zie, [De identiteitsdienst van het Experience Cloud testen en verifiëren](../implementation-guides/test-verify.md).

**Code implementeren**

Implementeer de code nadat deze voor het testen is geslaagd.

Als u een respijtperiode hebt ingeschakeld in [Stap 7](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3):

* Zorg ervoor dat [!DNL Analytics] ID (HULP) en MID bevinden zich in de aanvraag voor de afbeelding.
* Vergeet niet de respijtperiode uit te schakelen wanneer u voldoet aan de criteria voor stopzetting.
