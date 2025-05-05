---
description: Deze instructies gelden voor klanten van Analytics en Audience Managers die de Experience Cloud Identity Service willen gebruiken en geen labels voor gegevensverzameling gebruiken. Nochtans, adviseren wij sterk dat u markeringen gebruikt om de dienst van identiteitskaart uit te voeren. Met labels wordt de implementatieworkflow gestroomlijnd en wordt automatisch de juiste plaatsing van code en de juiste volgorde gegarandeerd.
keywords: ID-service
title: Implementeer de dienst Identiteit Experience Cloud voor Analytics en Audience Manager
exl-id: e31720a1-5c89-4084-88f6-443994dbb2f4
source-git-commit: 26152f559150f5bd67d4802b8464446482f2e9a1
workflow-type: tm+mt
source-wordcount: '1175'
ht-degree: 0%

---

# Implementeer de dienst Identiteit Experience Cloud voor Analytics en Audience Manager{#implement-the-experience-cloud-id-service-for-analytics-and-audience-manager}

Deze instructies zijn voor klanten Analytics en van de Audience Manager die de Dienst van de Identiteit van het Experience Cloud willen gebruiken en [&#128279;](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en) geen markeringen van de Inzameling van 0&rbrace; Gegevens gebruiken.  Nochtans, adviseren wij sterk dat u markeringen gebruikt om de dienst van identiteitskaart uit te voeren. Met labels wordt de implementatieworkflow gestroomlijnd en wordt automatisch de juiste plaatsing van code en de juiste volgorde gegarandeerd.

>[!IMPORTANT]
>
>* [ leest de vereisten ](../reference/requirements.md) alvorens u begint.
>* Deze procedure vereist AppMeasurement. Klanten die s_code gebruiken kunnen deze procedure niet voltooien.
>* Vorm en test deze code in een ontwikkelomgeving alvorens het in productie uit te voeren.

## Stap 1: Plan voor server-zij door:sturen {#section-880797cc992d4755b29cada7b831f1fc}

Naast de hier beschreven stappen, zouden klanten die [!DNL Analytics] en [!DNL Audience Manager] gebruiken aan server-zijdoor:sturen moeten migreren. Server-kant door:sturen laat u DIL (de code van de de gegevensinzameling van de Audience Manager) verwijderen en het vervangen met de [ Module van het Beheer van de Auditie ](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-other-solutions/audience-management-module.html). Zie [ server-kant het door:sturen documentatie ](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/server-side-forwarding/ssf.html) voor meer informatie.

Het migreren aan server-zij door:sturen vereist planning en coördinatie. Dit proces omvat externe wijzigingen in uw sitecode en interne stappen die Adobe moet uitvoeren om uw account te kunnen aanbieden. Veel van deze migratieprocedures moeten parallel lopen en samen worden vrijgegeven. Het implementatiepad moet deze reeks gebeurtenissen volgen:

1. Werk met uw [!DNL Analytics] en [!DNL Audience Manager] contacten om uw dienst van identiteitskaart en server-kant het door:sturen migratie te plannen. Maak het selecteren van een volgende server een belangrijk deel van dit plan.

1. Voltooi de vorm op de [ integratie en provisioning plaats ](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=X8SVES) om begonnen te worden.

1. Voer de dienst van identiteitskaart en [!DNL Audience Management Module] gelijktijdig uit. Om correct te werken, moeten [!DNL Audience Management Module] (server-kant door:sturen) en de dienst van identiteitskaart voor de zelfde reeks pagina&#39;s tezelfdertijd worden vrijgegeven.

## Stap 2: Download de ID Service-code {#section-0780126cf43e4ad9b6fc5fe17bb3ef86}

De id-service vereist de codebibliotheek van `VisitorAPI.js` . Deze codebibliotheek downloaden:

1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Code Manager]** .

1. Klik in Codebeheer op **[!UICONTROL JavaScrpt (New)]** of **[!UICONTROL JavaScript (Legacy)]** . Hiermee worden gecomprimeerde codebibliotheken gedownload.

1. Decomprimeer het codebestand en open het `VisitorAPI.js` -bestand.

## Stap 3: Voeg de functie Visitor.getInstance aan de code van de Dienst van identiteitskaart toe {#section-9e30838b4d0741658a7a492153c49f27}

>[!IMPORTANT]
>
>* Eerdere versies van de id service-API hebben deze functie op een andere locatie geplaatst en een andere syntaxis vereist. Als u van een versie voorafgaand aan [ versie 1.4 ](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572) migreert, neem nota van de nieuwe die plaatsing en syntaxis hier wordt gedocumenteerd.
>* Code in ALL CAPS is een plaatsaanduiding voor werkelijke waarden. Vervang deze tekst door uw organisatie-id, URL van trackingserver of een andere benoemde waarde.

**Deel 1: Kopieer hieronder de functie Visitor.getInstance**

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

**Deel 2: Voeg functiecode aan het Bezoeker API.js- dossier** toe

Plaats de functie `Visitor.getInstance` aan het einde van het bestand na het codeblok. Het bewerkte bestand moet er als volgt uitzien:

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

## Stap 4: Voeg uw identiteitskaart van de Organisatie van het Experience Cloud aan Visitor.getInstance toe {#section-e2947313492546789b0c3b2fc3e897d8}

Vervang `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` in de functie `Visitor.getInstance` door de organisatie-id van het Experience Cloud. Als u uw organisatie-id niet kent, kunt u deze vinden op de pagina voor het beheer van Experiencen Cloud. De bewerkte functie kan er ongeveer zo uitzien als het onderstaande voorbeeld.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*verander niet* het geval van de karakters in uw organisatieidentiteitskaart De id is hoofdlettergevoelig en moet precies worden gebruikt zoals opgegeven.

## Stap 5: Voeg uw volgende servers aan Visitor.getInstance toe {#section-0dfc52096ac2427f86045aab9a0e0dfc}

Analytics gebruikt trackingservers voor gegevensverzameling.

**Deel 1: Vind uw het volgen server URLs**

Controleer uw `s_code.js` - of `AppMeasurement.js` -bestanden om de URL&#39;s van de trackingserver te zoeken. U wilt de URL&#39;s die door deze variabelen worden opgegeven:

* `s.trackingServer`
* `s.trackingServerSecure`

**Deel 2: Plaats volgende servervariabelen**

Om te bepalen welke volgende servervariabelen moeten worden gebruikt:

1. Beantwoord de vragen in de onderstaande beslissingsmatrix. Gebruik de variabelen die overeenkomen met uw antwoorden.
1. Vervang de plaatsaanduidingen van de trackingserver door de URL&#39;s van de trackingserver.
1. Verwijder ongebruikte het volgen server en de servervariabelen van het Experience Cloud uit de code.

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>Wanneer gebruikt, pas de server URLs van het Experience Cloud aan hun overeenkomstige volgende server URLs als dit aan:

* Experience Cloud-server-URL = URL van trackingserver
* Beveiligde URL van server voor Experience Cloud = beveiligde URL van server bijhouden

Als u niet zeker bent hoe te om uw het volgen server te vinden [ FAQ ](../faq-intro/faq.md) ziet en [ bevolkt correct de variabelen trackingServer en trackingServerSecure ](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).

## Stap 6: Werk uw AppMeasurement.js- dossier bij {#section-5517e94a09bc44dfb492ebca14b43048}

Deze stap vereist [!UICONTROL AppMeasurement]. U kunt niet doorgaan als u nog steeds s_code gebruikt.

Voeg de hieronder getoonde functie `Visitor.getInstance` toe aan uw `AppMeasurement.js` bestand. Plaats het in de sectie die configuraties zoals `linkInternalFilters`, `charSet`, `trackDownloads`, enz. bevat:

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

>[!IMPORTANT]
>
>U moet nu de [!DNL Audience Manager] DIL-code verwijderen en deze vervangen door de Audience Management Module. Zie [ Server-zij het Door:sturen ](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/server-side-forwarding/ssf.html) voor instructies uitvoeren.

***(Facultatief, maar geadviseerd)* creeer een douaneprep &#x200B;**

Stel een aangepaste proxy in `AppMeasurement.js` in om de dekking te meten. Voeg deze aangepaste proxy toe aan de functie `doPlugins` van het `AppMeasurement.js` -bestand:

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## Stap 7: API-code van bezoeker toevoegen aan de pagina {#section-c2bd096a3e484872a72967b6468d3673}

Plaats het bestand ` [!UICONTROL VisitorAPI.js]` binnen de tags `<head>` op elke pagina. Wanneer u het `VisitorAPI.js` -bestand op de pagina plaatst:

* Plaats deze aan het begin van de sectie `<head>` , zodat deze voor andere oplossingstags wordt weergegeven.
* Deze moet worden uitgevoerd vóór AppMeasurement en de code voor andere [!DNL Experience Cloud] -oplossingen.

## Stap 8: (Optioneel) Configureer een evaluatieperiode {#section-aceacdb7d5794f25ac6ff46f82e148e1}

Als om het even welk van deze gebruiksgevallen op uw situatie van toepassing zijn, vraag [&#128279;](https://helpx.adobe.com/marketing-cloud/contact-support.html) de Zorg van de Klant om een tijdelijke [ respijtperiode ](../reference/analytics-reference/grace-period.md) te vestigen.  Respijtperioden kunnen maximaal 180 dagen duren. U kunt een respijtperiode verlengen als dat nodig is.

**Gedeeltelijke Implementatie**

U hebt een respijtperiode nodig als u sommige pagina&#39;s hebt die de id-service gebruiken en sommige pagina&#39;s die dat niet doen, en deze allemaal in dezelfde analytische rapportsuite rapporteren. Dit komt vaak voor als u een algemene rapportsuite hebt die rapporten opstelt in verschillende domeinen.

Sluit de respijtperiode af nadat de id-service is geïmplementeerd op al uw webpagina&#39;s die in dezelfde rapportsuite rapporteren.

**s_vi de Vereisten van het Koekje**

U hebt een respijtperiode nodig als u nieuwe bezoekers een s_vi koekje na het migreren aan de dienst van identiteitskaart wilt hebben. Dit is algemeen als uw implementatie het s_vi koekje leest en het in een variabele opslaat.

Sluit de respijtperiode af nadat uw implementatie de MID kan vastleggen in plaats van het s_vi cookie te lezen.

Zie ook, [ Cookies en de Dienst van de Identiteit van het Experience Cloud ](../introduction/cookies.md).

**de Integratie van Gegevens van de ClikStream**

U hebt een respijtperiode nodig als u gegevens naar een intern systeem verzendt vanuit een Clickstream-gegevensfeed en die processen de kolommen `visid_high` en `visid_low` gebruiken.

Sluit de respijtperiode af nadat de kolommen `post_visid_high` en `post_visid_low` door het gegevensinvoerproces kunnen worden gebruikt.

Zie ook, [ de Verwijzing van de Kolom van Gegevens Clickstream ](https://experienceleague.adobe.com/docs/analytics/export/analytics-data-feed/data-feed-overview.html).

## Stap 9: Test en implementeer ID-servicecode {#section-f857542bfc70496dbb9f318d6b3ae110}

U kunt als volgt testen en opstellen.

**Test en verifieer**

Als u de implementatie van uw id-service wilt testen, controleert u op het volgende:

* [ het koekje van AMCV ](../introduction/cookies.md) in het domein waar u pagina&#39;s wordt ontvangen.
* MID waarde in het het beeldverzoek van de Analyse met [ debugger van de Adobe ](https://experienceleague.adobe.com/docs/analytics/implementation/validate/debugger.html).
* Zie ook, [ Test en verifieer de Dienst van de Identiteit van het Experience Cloud ](../implementation-guides/test-verify.md).

Om server-kant het door:sturen te verifiëren, zie [ hoe te om uw Server-kant het door:sturen Implementatie ](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/server-side-forwarding/ssf-verify.html) te verifiëren.

**opstellen**

Implementeer de code nadat deze voor het testen is geslaagd.

Als u een respijtperiode hebt ingeschakeld:

* Zorg ervoor dat de opties Analytics ID (AID) en MID in de afbeeldingsaanvraag staan.
* Vergeet niet de respijtperiode uit te schakelen wanneer u voldoet aan de criteria voor stopzetting.
