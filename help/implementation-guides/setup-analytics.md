---
description: Deze instructies gelden voor klanten van Analytics die de Experience Cloud Identity Service willen gebruiken en geen Dynamic Tag Management (DTM) gebruiken. Wij raden u echter sterk aan DTM te gebruiken om de id-service te implementeren. DTM stroomlijnt de implementatieworkflow en zorgt automatisch voor de juiste plaatsing van code en de juiste volgorde van code.
keywords: ID Service
seo-description: Deze instructies gelden voor klanten van Analytics die de Experience Cloud Identity Service willen gebruiken en geen Dynamic Tag Management (DTM) gebruiken. Wij raden u echter sterk aan DTM te gebruiken om de id-service te implementeren. DTM stroomlijnt de implementatieworkflow en zorgt automatisch voor de juiste plaatsing van code en de juiste volgorde van code.
seo-title: Implementeer de Experience Cloud Identity Service voor Analytics
title: Implementeer de Experience Cloud Identity Service voor Analytics
uuid: 7fbd6fa0-1713-4232-8680-500ed62709d5
translation-type: tm+mt
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# Implementeer de Experience Cloud Identity Service voor Analytics {#implement-the-experience-cloud-id-service-for-analytics}

Deze instructies gelden voor klanten van Analytics die de Experience Cloud Identity Service willen gebruiken en geen Dynamic Tag Management (DTM) gebruiken. Wij raden u echter sterk aan DTM te gebruiken om de id-service te implementeren. DTM stroomlijnt de implementatieworkflow en zorgt automatisch voor de juiste plaatsing van code en de juiste volgorde van code.

>[!IMPORTANT]
>
>* [Lees de vereisten](../reference/requirements.md) voordat u begint.
>* Vorm en test deze code in een ontwikkelomgeving alvorens het in productie uit te voeren.
>



Voer de volgende stappen uit om de id-service voor Adobe Analytics te implementeren:

1. [De ID-servicecode downloaden](../implementation-guides/setup-analytics.md#section-ead9403a6b7e45b887f9ac959ef89f7f)
1. [Voeg de functie Visitor.getInstance aan de Code van de Dienst van identiteitskaart toe](../implementation-guides/setup-analytics.md#section-6053a6b7c16c466a9f9fdbf9cb9db3df)
1. [Voeg uw Experience Cloud Organization-id toe aan Visitor.getInstance](../implementation-guides/setup-analytics.md#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e)
1. [Voeg uw volgende servers aan Visitor.getInstance toe](../implementation-guides/setup-analytics.md#section-70ec9ebff47940d8ab520be5ec4728c5)
1. [Werk het bestand AppMeturement.js of s_code.js bij](../implementation-guides/setup-analytics.md#section-b53113aea1bd4de896e0e4e9a7edee19)
1. [API-code van bezoeker toevoegen aan de pagina](../implementation-guides/setup-analytics.md#section-d46d6aa324c842f2931d901e38d6db1d)
1. [(Optioneel) Configureer een respijtperiode](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3)
1. [ID-servicecode testen en implementeren](../implementation-guides/setup-analytics.md#section-e9c1764ac21a4ec5be1ff338c0e2e01b)

## Stap 1: De ID-servicecode downloaden {#section-ead9403a6b7e45b887f9ac959ef89f7f}

De [!UICONTROL ID Service] code vereist de `VisitorAPI.js` codebibliotheek. Deze codebibliotheek downloaden:

1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Code Manager]**.
1. Klik [!UICONTROL Code Manager]op **[!UICONTROL JavaScript (New)]** of **[!UICONTROL JavaScript (Legacy)]**.

   Hiermee worden gecomprimeerde codebibliotheken gedownload.

1. Decomprimeer het codebestand en open het `VisitorAPI.js` bestand.

## Stap 2. Voeg de functie Visitor.getInstance aan de Code van de Dienst van identiteitskaart toe {#section-6053a6b7c16c466a9f9fdbf9cb9db3df}

>[!IMPORTANT]
>
>* Eerdere versies van de id service-API hebben deze functie op een andere locatie geplaatst en een andere syntaxis vereist. Als u migreert vanaf een versie die ouder is dan [versie 1.4](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572), moet u de nieuwe plaatsing en syntaxis noteren die hier worden beschreven.
>* Code in ALL CAPS is een plaatsaanduiding voor werkelijke waarden. Vervang deze tekst door uw organisatie-id, URL van trackingserver of een andere benoemde waarde.
>



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

Plaats de `Visitor.getInstance` functie aan het eind van het dossier na het codeblok. Het bewerkte bestand moet er als volgt uitzien:

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

## Stap 3: Voeg uw Experience Cloud Organization-id toe aan Visitor.getInstance {#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e}

Vervang in de `Visitor.getInstance` functie `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` door uw [!DNL Experience Cloud] organisatie-id. Als u uw organisatie-id niet kent, vindt u deze op de [!DNL Experience Cloud] beheerpagina. Zie ook, [Beleid - de Diensten](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html)van de Kern. Uw bewerkte functie kan er ongeveer zo uitzien als het onderstaande voorbeeld.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*Wijzig het hoofdlettergebruik van de tekens in uw organisatie-id niet* . De id is hoofdlettergevoelig en moet precies worden gebruikt zoals opgegeven.

## Stap 4: Voeg uw volgende servers aan Visitor.getInstance toe {#section-70ec9ebff47940d8ab520be5ec4728c5}

De volgende servers worden gebruikt voor [!DNL Analytics] gegevensinzameling.

**Deel 1: URL&#39;s van de volgende server zoeken**

Controleer uw `s_code.js` of `AppMeasurement.js` bestanden om de URL&#39;s van de volgende server te vinden. U wilt de URL&#39;s die door deze variabelen worden opgegeven:

* `s.trackingServer`
* `s.trackingServerSecure`

**Deel 2: Servervariabelen voor bijhouden instellen**

Om te bepalen welke volgende servervariabelen moeten worden gebruikt:

1. Beantwoord de vragen in de onderstaande beslissingsmatrix. Gebruik de variabelen die overeenkomen met uw antwoorden.
1. Vervang de plaatsaanduidingen van de trackingserver door de URL&#39;s van de trackingserver.
1. Verwijder ongebruikte trackingserver- en [!DNL Experience Cloud] servervariabelen uit de code.

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>Wanneer gebruikt, pas de server URL [!DNL Experience Cloud] &#39;s aan hun overeenkomstige het volgen server URLs als dit aan: >
>* [!DNL Experience Cloud] server-URL = URL van traceringsserver
>* [!DNL Experience Cloud] server secure URL = tracking server secure URL
>



Als u niet zeker bent hoe te om uw het volgen server te vinden [FAQ](../faq-intro/faq.md) zien en [Correct bevolken trackingServer en trackingServerSecure variabelen](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).

## Stap 5: Werk het bestand AppMeturement.js of s_code.js bij {#section-b53113aea1bd4de896e0e4e9a7edee19}

Voeg deze functie aan uw `AppMeasurement.js` of `s_code.js` dossier toe:

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

Plaats de code in dezelfde sectie die configuraties zoals `linkInternalFilters`, `charSet`, `trackDownloads`enz. bevat.

***(Optioneel maar aanbevolen)*Een aangepaste proxy maken **

Stel een aangepaste proxy in `AppMeasurement.js` of `s_code.js` om de dekking te meten. Voeg deze aangepaste proxy toe aan de `doPlugins` functie van uw `AppMeasurement.js` of `s_code.js` bestanden:

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## Stap 6: API-code van bezoeker toevoegen aan de pagina {#section-d46d6aa324c842f2931d901e38d6db1d}

Plaats het `VisitorAPI.js` bestand binnen de `<head>` tags op elke pagina. Wanneer u het `VisitorAPI.js` bestand op de pagina plaatst:

* Plaats het aan het begin van de `<head>` sectie aan het verschijnt vóór andere oplossingsmarkeringen.
* Deze moet worden uitgevoerd vóór AppMeasurement en de code voor andere [!DNL Experience Cloud] oplossingen.

Verplaats deze code naar productie na het testen en controleren.

## Stap 7: (Optioneel) Configureer een respijtperiode {#section-7bbb2f72c26e4abeb8881e18366797a3}

Als een van deze gebruiksgevallen op uw situatie van toepassing is, vraagt u de [klantenservice](https://helpx.adobe.com/marketing-cloud/contact-support.html) om een tijdelijke [respijtperiode](../reference/analytics-reference/grace-period.md)in te stellen. Respijtperioden kunnen maximaal 180 dagen duren. U kunt een respijtperiode verlengen als dat nodig is.

**Gedeeltelijke implementatie**

U hebt een respijtperiode nodig als u sommige pagina&#39;s hebt die de id-service gebruiken en sommige pagina&#39;s die dat niet doen, en deze allemaal in dezelfde [!DNL Analytics] rapportsuite rapporteren. Dit komt vaak voor als u een algemene rapportsuite hebt die rapporten opstelt in verschillende domeinen.

Sluit de respijtperiode af nadat de id-service is geïmplementeerd op al uw webpagina&#39;s die in dezelfde rapportsuite rapporteren.

**S_vi Cookie-vereisten**

U hebt een respijtperiode nodig als u nieuwe bezoekers een s_vi koekje na het migreren aan de dienst van identiteitskaart wilt hebben. Dit is algemeen als uw implementatie het s_vi koekje leest en het in een variabele opslaat.

Sluit de respijtperiode af nadat uw implementatie de MID kan vastleggen in plaats van het s_vi cookie te lezen.

See, [Cookies and the Experience Cloud Identity Service](../introduction/cookies.md).

U hebt een respijtperiode nodig als u gegevens naar een intern systeem verzendt vanuit een Clickstream-gegevensfeed en die processen de `visid_high` en `visid_low` kolommen gebruiken.

U kunt de respijtperiode uitschakelen nadat u de kolommen `post_visid_high` en `post_visid_low` kolommen hebt ingevoerd.

Zie [de Verwijzing](https://marketing.adobe.com/resources/help/en_US/sc/clickstream/datafeeds_reference.html)van de Kolom van Gegevens van de Klikstream.

**Clickstream-gegevensinsluiting**

## Stap 8: ID-servicecode testen en implementeren {#section-e9c1764ac21a4ec5be1ff338c0e2e01b}

U kunt als volgt testen en opstellen.

**Testen en verifiëren**

Als u de implementatie van uw id-service wilt testen, controleert u op het volgende:

* [AMCV-cookie](../introduction/cookies.md) in het domein waar uw pagina wordt gehost.
* MID-waarde in de [!DNL Analytics] afbeeldingsaanvraag met het [Adobe-foutopsporingsprogramma](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html).

Zie, [test en verifieer de Experience Cloud Identity Service](../implementation-guides/test-verify.md).

**Code implementeren**

Implementeer de code nadat deze voor het testen is geslaagd.

Als u een respijtperiode hebt ingeschakeld in [stap 7](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3):

* Zorg ervoor dat de [!DNL Analytics] id (AID) en MID in de afbeeldingsaanvraag staan.
* Vergeet niet de respijtperiode uit te schakelen wanneer u voldoet aan de criteria voor stopzetting.
