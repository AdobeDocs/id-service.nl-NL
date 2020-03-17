---
description: Deze instructies gelden voor klanten van Analytics and Audience Manager die de Experience Cloud Identity Service willen gebruiken en geen Dynamic Tag Management (DTM) gebruiken. Wij raden u echter sterk aan DTM te gebruiken om de id-service te implementeren. DTM stroomlijnt de implementatieworkflow en zorgt automatisch voor de juiste plaatsing van code en de juiste volgorde van code.
keywords: ID Service
seo-description: Deze instructies gelden voor klanten van Analytics and Audience Manager die de Experience Cloud Identity Service willen gebruiken en geen Dynamic Tag Management (DTM) gebruiken. Wij raden u echter sterk aan DTM te gebruiken om de id-service te implementeren. DTM stroomlijnt de implementatieworkflow en zorgt automatisch voor de juiste plaatsing van code en de juiste volgorde van code.
seo-title: Implementeer de Experience Cloud Identity Service voor Analytics en Audience Manager
title: Implementeer de Experience Cloud Identity Service voor Analytics en Audience Manager
uuid: d46050ae-87de-46cc-911b-d6346c7fd511
translation-type: tm+mt
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# Implementeer de Experience Cloud Identity Service voor Analytics en Audience Manager{#implement-the-experience-cloud-id-service-for-analytics-and-audience-manager}

Deze instructies gelden voor klanten van Analytics and Audience Manager die de Experience Cloud Identity Service willen gebruiken en geen Dynamic Tag Management (DTM) gebruiken. Wij raden u echter sterk aan DTM te gebruiken om de id-service te implementeren. DTM stroomlijnt de implementatieworkflow en zorgt automatisch voor de juiste plaatsing van code en de juiste volgorde van code.

>[!IMPORTANT]
>
>* [Lees de vereisten](../reference/requirements.md) voordat u begint.
>* Deze procedure vereist AppMeasurement. Klanten die s_code gebruiken kunnen deze procedure niet voltooien.
>* Vorm en test deze code in een ontwikkelomgeving alvorens het in productie uit te voeren.
>



## Stap 1: Plan voor server-kant door:sturen {#section-880797cc992d4755b29cada7b831f1fc}

Naast de hier beschreven stappen, klanten die gebruiken [!DNL Analytics] en aan server-zij door:sturen [!DNL Audience Manager] zouden moeten migreren. Door:sturen aan de serverzijde kunt u DIL (de code van de gegevensinzameling van de Manager van de Audience) verwijderen en het vervangen met de Module [van het Beheer van de](https://marketing.adobe.com/resources/help/en_US/aam/c_profiles_audiences.html)Publiek. Zie de [server-kant het door:sturen documentatie](https://marketing.adobe.com/resources/help/en_US/analytics/audiences/ssf.html) voor meer informatie.

Het migreren aan server-zij door:sturen vereist planning en coördinatie. Dit proces omvat externe wijzigingen in uw sitecode en interne stappen die Adobe moet uitvoeren om uw account aan te bieden. Veel van deze migratieprocedures moeten parallel lopen en samen worden vrijgegeven. Het implementatiepad moet deze reeks gebeurtenissen volgen:

1. Werk met uw [!DNL Analytics] en [!DNL Audience Manager] contacten om uw dienst van identiteitskaart en server-kant het door:sturen migratie te plannen. Maak het selecteren van een volgende server een belangrijk deel van dit plan.

1. Voltooi het formulier op de [integratie- en inrichtingssite](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=X8SVES) om aan de slag te gaan.

1. Voer de dienst van identiteitskaart en [!DNL Audience Management Module] gelijktijdig uit. Om behoorlijk te werken, [!DNL Audience Management Module] (server-zijdoor:sturen) en de dienst van identiteitskaart moeten voor de zelfde reeks pagina&#39;s en tezelfdertijd worden vrijgegeven.

## Stap 2: De ID-servicecode downloaden {#section-0780126cf43e4ad9b6fc5fe17bb3ef86}

Voor de ID-service is de `VisitorAPI.js` codebibliotheek vereist. Deze codebibliotheek downloaden:

1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Code Manager]**.

1. Klik in Codebeheer op **[!UICONTROL JavaScrpt (New)]** of **[!UICONTROL JavaScript (Legacy)]**. Hiermee worden gecomprimeerde codebibliotheken gedownload.

1. Decomprimeer het codebestand en open het `VisitorAPI.js` bestand.

## Stap 3: Voeg de functie Visitor.getInstance aan de code van de Dienst van identiteitskaart toe {#section-9e30838b4d0741658a7a492153c49f27}

>[!IMPORTANT]
>
>* Eerdere versies van de id service-API hebben deze functie op een andere locatie geplaatst en een andere syntaxis vereist. Als u migreert vanaf een versie die ouder is dan [versie 1.4](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572), moet u de nieuwe plaatsing en syntaxis noteren die hier worden beschreven.
>* Code in ALL CAPS is een plaatsaanduiding voor werkelijke waarden. Vervang deze tekst door uw organisatie-id, URL van trackingserver of een andere benoemde waarde.
>



**Deel 1: Kopieer de functie Visitor.getInstance hieronder**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

**Deel 2: Functiecode toevoegen aan het bestand Visitor API.js**

Plaats de `Visitor.getInstance` functie aan het eind van het dossier na het codeblok. Het bewerkte bestand moet er als volgt uitzien:

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library 
 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

## Stap 4: Voeg uw Experience Cloud Organization-id toe aan Visitor.getInstance {#section-e2947313492546789b0c3b2fc3e897d8}

Vervang de functie in de `Visitor.getInstance` functie `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` door de organisatie-id van Experience Cloud. Als u uw organisatie-id niet kent, vindt u deze op de beheerpagina van Experience Cloud. Uw bewerkte functie kan er ongeveer zo uitzien als het onderstaande voorbeeld.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*Wijzig het hoofdlettergebruik van de tekens in uw organisatie-id niet* . De id is hoofdlettergevoelig en moet precies worden gebruikt zoals opgegeven.

## Stap 5: Voeg uw volgende servers aan Visitor.getInstance toe {#section-0dfc52096ac2427f86045aab9a0e0dfc}

Analytics gebruikt trackingservers voor gegevensverzameling.

**Deel 1: URL&#39;s van de volgende server zoeken**

Controleer uw `s_code.js` of `AppMeasurement.js` bestanden om de URL&#39;s van de volgende server te vinden. U wilt de URL&#39;s die door deze variabelen worden opgegeven:

* `s.trackingServer`
* `s.trackingServerSecure`

**Deel 2: Servervariabelen voor bijhouden instellen**

Om te bepalen welke volgende servervariabelen moeten worden gebruikt:

1. Beantwoord de vragen in de onderstaande beslissingsmatrix. Gebruik de variabelen die overeenkomen met uw antwoorden.
1. Vervang de plaatsaanduidingen van de trackingserver door de URL&#39;s van de trackingserver.
1. Ongebruikte traceringsserver en Experience Cloud-servervariabelen uit de code verwijderen.

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>Wanneer u de URL&#39;s van de Experience Cloud-server gebruikt, moet u deze als volgt afstemmen op de URL&#39;s van de bijbehorende trackingserver:

* Experience Cloud Server URL = URL van trackingserver
* Experience Cloud Server secure URL = tracking server secure URL

Als u niet zeker bent hoe te om uw het volgen server te vinden [FAQ](../faq-intro/faq.md) zien en [Correct bevolken trackingServer en trackingServerSecure variabelen](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).

## Stap 6: Werk het bestand AppMeasurement.js bij {#section-5517e94a09bc44dfb492ebca14b43048}

Deze stap is vereist [!UICONTROL AppMeasurement]. U kunt niet doorgaan als u nog steeds s_code gebruikt.

Voeg de hieronder getoonde `Visitor.getInstance` functie aan uw `AppMeasurement.js` dossier toe. Plaats het in de sectie die configuraties zoals `linkInternalFilters`, `charSet`, `trackDownloads`enz. bevat. :

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

>[!IMPORTANT]
>
>Op dit punt, zou u de code van [!DNL Audience Manager] DIL moeten verwijderen en het met de Module van het Beheer van de Publiek vervangen. Zie [Server-kant doorsturen](https://marketing.adobe.com/resources/help/en_US/reference/ssf.html) implementeren voor instructies.

***(Optioneel, maar aanbevolen)*Een aangepaste proxy maken **

Stel een aangepaste proxy in `AppMeasurement.js` om de dekking te meten. Voeg deze aangepaste proxy toe aan de `doPlugins` functie van het `AppMeasurement.js` bestand:

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## Stap 7: API-code van bezoeker toevoegen aan de pagina {#section-c2bd096a3e484872a72967b6468d3673}

Plaats het ` [!UICONTROL VisitorAPI.js]` bestand binnen de `<head>` tags op elke pagina. Wanneer u het `VisitorAPI.js` bestand op de pagina plaatst:

* Plaats het aan het begin van de `<head>` sectie aan het verschijnt vóór andere oplossingsmarkeringen.
* Deze moet worden uitgevoerd vóór AppMeasurement en de code voor andere [!DNL Experience Cloud] oplossingen.

## Stap 8: (Optioneel) Configureer een respijtperiode {#section-aceacdb7d5794f25ac6ff46f82e148e1}

Als een van deze gebruiksgevallen op uw situatie van toepassing is, vraagt u de [klantenservice](https://helpx.adobe.com/marketing-cloud/contact-support.html) om een tijdelijke [respijtperiode](../reference/analytics-reference/grace-period.md)in te stellen. Respijtperioden kunnen maximaal 180 dagen duren. U kunt een respijtperiode verlengen als dat nodig is.

**Gedeeltelijke implementatie**

U hebt een respijtperiode nodig als u sommige pagina&#39;s hebt die de id-service gebruiken en sommige pagina&#39;s die dat niet doen, en deze allemaal in dezelfde analytische rapportsuite rapporteren. Dit komt vaak voor als u een algemene rapportsuite hebt die rapporten opstelt in verschillende domeinen.

Sluit de respijtperiode af nadat de id-service is geïmplementeerd op al uw webpagina&#39;s die in dezelfde rapportsuite rapporteren.

**S_vi Cookie-vereisten**

U hebt een respijtperiode nodig als u nieuwe bezoekers een s_vi koekje na het migreren aan de dienst van identiteitskaart wilt hebben. Dit is algemeen als uw implementatie het s_vi koekje leest en het in een variabele opslaat.

Sluit de respijtperiode af nadat uw implementatie de MID kan vastleggen in plaats van het s_vi cookie te lezen.

Zie ook [Cookies en de Experience Cloud Identity Service](../introduction/cookies.md).

**De Integratie van Gegevens Clickstream**

U hebt een respijtperiode nodig als u gegevens naar een intern systeem verzendt vanuit een Clickstream-gegevensfeed en die processen de `visid_high` en `visid_low` kolommen gebruiken.

U kunt de respijtperiode uitschakelen nadat u de kolommen `post_visid_high` en `post_visid_low` kolommen hebt ingevoerd.

Zie ook [de Verwijzing](https://marketing.adobe.com/resources/help/en_US/sc/clickstream/datafeeds_reference.html)van de Kolom van Gegevens van de Klikstream.

## Stap 9: ID-servicecode testen en implementeren {#section-f857542bfc70496dbb9f318d6b3ae110}

U kunt als volgt testen en opstellen.

**Testen en verifiëren**

Als u de implementatie van uw id-service wilt testen, controleert u op het volgende:

* [AMCV-cookie](../introduction/cookies.md) in het domein waar u pagina&#39;s ontvangt.
* MID-waarde in de afbeeldingsaanvraag Analytics met [Adobe Debugger](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html).
* Zie ook: [Test en controleer de Experience Cloud Identity Service](../implementation-guides/test-verify.md).

Om server-kant het door:sturen te verifiëren, zie [hoe te uw server-kant het Door:sturen Implementatie](https://marketing.adobe.com/resources/help/en_US/reference/ssf-verify.html)verifiëren.

**Implementeren**

Implementeer de code nadat deze voor het testen is geslaagd.

Als u een respijtperiode hebt ingeschakeld:

* Zorg ervoor dat de opties Analytics ID (AID) en MID in de afbeeldingsaanvraag staan.
* Vergeet niet de respijtperiode uit te schakelen wanneer u voldoet aan de criteria voor stopzetting.

