---
description: Deze instructies gelden voor klanten met Analytics, Audience Manager en Target die de Experience Cloud Identity Service willen gebruiken en geen gebruik maken van Dynamic Tag Management (DTM). Wij raden u echter sterk aan DTM te gebruiken om de id-service te implementeren. DTM stroomlijnt de implementatieworkflow en zorgt automatisch voor de juiste plaatsing van code en de juiste volgorde van code.
keywords: ID-service
title: Voer de Dienst van de Identiteit van Experience Cloud voor Analytics, Audience Manager, en Doel uit
exl-id: d55baa11-e8ec-4c30-b6bc-caccf4c284ba
source-git-commit: 070390ec0534c9066d717fe52ff572f34c110137
workflow-type: tm+mt
source-wordcount: '1491'
ht-degree: 0%

---

# Voer de Dienst van de Identiteit van Experience Cloud voor Analytics, Audience Manager, en Doel uit {#implement-the-experience-cloud-id-service-for-analytics-audience-manager-and-target}

Deze instructies gelden voor klanten met Analytics, Audience Manager en Target die de Experience Cloud Identity Service willen gebruiken en geen gebruik maken van Dynamic Tag Management (DTM). Wij raden u echter sterk aan DTM te gebruiken om de id-service te implementeren. DTM stroomlijnt de implementatieworkflow en zorgt automatisch voor de juiste plaatsing van code en de juiste volgorde van code.

>[!IMPORTANT]
>
>De id-service lezen [vereisten](../reference/requirements.md) voordat u begint en noteert u de volgende specifieke vereisten voor deze implementatie:
>
>* Klanten die s_code gebruiken kunnen deze procedure niet voltooien. Voer een upgrade uit naar mbox-code v61 om deze procedure te voltooien.
>* Deze code configureren en testen in een ontwikkelomgeving *voor* die u in productie toepast.


## Stap 1: Plan voor server-kant door:sturen {#section-880797cc992d4755b29cada7b831f1fc}

Naast de hier beschreven stappen, klanten die [!DNL Analytics] en [!DNL Audience Manager] zou aan server-kant door:sturen moeten migreren. Door:sturen aan de serverzijde kunt u DIL (de code van de de gegevensinzameling van de Audience Manager) verwijderen en het vervangen met [Module voor publieksbeheer](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-other-solutions/audience-management-module.html). Zie de [server-kant het door:sturen documentatie](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/server-side-forwarding/ssf.html) voor meer informatie .

Het migreren aan server-zij door:sturen vereist planning en coördinatie. Dit proces omvat externe wijzigingen in uw sitecode en interne stappen die Adobe moet uitvoeren om uw account te kunnen instellen. Veel van deze migratieprocedures moeten parallel lopen en samen worden vrijgegeven. Het implementatiepad moet deze reeks gebeurtenissen volgen:

1. Werk met uw [!DNL Analytics] en [!DNL Audience Manager] contacten om uw dienst van identiteitskaart en server-kant het door:sturen migratie te plannen. Maak het selecteren van een volgende server een belangrijk deel van dit plan.

1. Vul het formulier in op het tabblad [integratie- en inrichtingssite](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=X8SVES) om aan de slag te gaan.

1. Voer de dienst van identiteitskaart en uit [!DNL Audience Management Module] tegelijkertijd. Om goed te werken, [!DNL Audience Management Module] (server-kant door:sturen) en de dienst van identiteitskaart moet voor de zelfde reeks pagina&#39;s en tezelfdertijd worden vrijgegeven.

## Stap 2: De ID-servicecode downloaden {#section-0780126cf43e4ad9b6fc5fe17bb3ef86}

De id-service vereist de `VisitorAPI.js` codebibliotheek. Deze codebibliotheek downloaden:

1. Ga naar **[!UICONTROL Admin > Code Manager]**.
1. Klik in Codebeheer op **[!UICONTROL JavaScrpt (New)]** of **[!UICONTROL JavaScript (Legacy)]**. Hiermee worden gecomprimeerde codebibliotheken gedownload.

1. Het codebestand decomprimeren en het dialoogvenster `VisitorAPI.js` bestand.

## Stap 3: Voeg de functie Visitor.getInstance aan de code van de Dienst van identiteitskaart toe {#section-9e30838b4d0741658a7a492153c49f27}

>[!IMPORTANT]
>
>* Eerdere versies van de id service-API hebben deze functie op een andere locatie geplaatst en een andere syntaxis vereist. Als u migreert op basis van een eerdere versie dan [versie 1.4](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572), let op de nieuwe plaatsing en syntaxis die hier wordt gedocumenteerd.
>* Code in ALL CAPS is een plaatsaanduiding voor werkelijke waarden. Vervang deze tekst door uw organisatie-id, URL van trackingserver of een andere benoemde waarde.


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

Plaats de `Visitor.getInstance` aan het einde van het bestand na het codeblok. Het bewerkte bestand moet er als volgt uitzien:

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

## Stap 4: Voeg uw Experience Cloud Organisatie-id toe aan Visitor.getInstance {#section-e2947313492546789b0c3b2fc3e897d8}

In de `Visitor.getInstance` functie, vervangen `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` met uw Experience Cloud-organisatie-id. Als u uw organisatie-id niet kent, kunt u deze vinden op de pagina voor beheer van de Experience Cloud. Uw bewerkte functie kan er ongeveer zo uitzien als het onderstaande voorbeeld.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*Niet gebruiken* Wijzig het hoofdlettergebruik van de tekens in uw organisatie-id. De id is hoofdlettergevoelig en moet precies worden gebruikt zoals opgegeven.

## Stap 5: Voeg uw volgende servers aan Visitor.getInstance toe {#section-0dfc52096ac2427f86045aab9a0e0dfc}

Analytics gebruikt trackingservers voor gegevensverzameling.

**Deel 1: URL&#39;s van de volgende server zoeken**

Controleer uw `s_code.js` of `AppMeasurement.js` bestanden om de URL&#39;s van de trackingserver te zoeken. U wilt de URL&#39;s die door deze variabelen worden opgegeven:

* `s.trackingServer`
* `s.trackingServerSecure`

**Deel 2: Servervariabelen voor bijhouden instellen**

Om te bepalen welke volgende servervariabelen moeten worden gebruikt:

1. Beantwoord de vragen in de onderstaande beslissingsmatrix. Gebruik de variabelen die overeenkomen met uw antwoorden.
1. Vervang de plaatsaanduidingen van de trackingserver door de URL&#39;s van de trackingserver.
1. Verwijder ongebruikte het volgen server en de servervariabelen van de Experience Cloud uit de code.

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>Wanneer gebruikt, pas de server URLs van de Experience Cloud aan hun overeenkomstige volgende server URLs als dit aan:

* Experience Cloud server-URL = URL van trackingsserver
* Beveiligde URL van Experience Cloud-server = beveiligde URL van server bijhouden

Als u niet zeker bent hoe te om uw het volgen server te vinden zie [Veelgestelde vragen](../faq-intro/faq.md) en [De variabelen trackingServer en trackingServerSecure correct vullen](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).

## Stap 6: Werk het bestand AppMeasurement.js bij {#section-5517e94a09bc44dfb492ebca14b43048}

Deze stap vereist [!UICONTROL AppMeasurement]. U kunt niet doorgaan als u nog steeds s_code gebruikt.

Voeg de `Visitor.getInstance` hieronder weergegeven functie `AppMeasurement.js` bestand. Plaats het in de sectie die configuraties zoals bevat `linkInternalFilters`, `charSet`, `trackDownloads`, enz. :

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

>[!IMPORTANT]
>
>Op dit punt dient u de [!DNL Audience Manager] DIL code en vervang het door de Module van het Beheer van de Publiek. Zie [Server-Side Forwarding implementeren](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/server-side-forwarding/ssf.html) voor instructies.

***(Optioneel, maar aanbevolen)* Een aangepaste proxy maken **

Aangepaste proxy instellen in `AppMeasurement.js` om de dekking te meten. Deze aangepaste proxy toevoegen aan de `doPlugins` functie van uw `AppMeasurement.js` bestand:

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## Stap 7: API-code van bezoeker toevoegen aan de pagina {#section-c2bd096a3e484872a72967b6468d3673}

Plaats de ` [!UICONTROL VisitorAPI.js]` in het `<head>` -tags op elke pagina. Wanneer u `VisitorAPI.js` bestand naar uw pagina:

* Zet het aan het begin van `<head>` wordt weergegeven vóór andere oplossingstags.
* Deze moet worden uitgevoerd vóór AppMeturement en de code voor andere [!DNL Experience Cloud] oplossingen.

## Stap 8: (Optioneel) Configureer een respijtperiode {#section-aceacdb7d5794f25ac6ff46f82e148e1}

Als een van deze gebruiksgevallen op uw situatie van toepassing is, vraag dan [Klantenservice](https://helpx.adobe.com/marketing-cloud/contact-support.html) een tijdelijke [respijtperiode](../reference/analytics-reference/grace-period.md). Respijtperioden kunnen maximaal 180 dagen duren. U kunt een respijtperiode verlengen als dat nodig is.

**Gedeeltelijke implementatie**

U hebt een respijtperiode nodig als u sommige pagina&#39;s hebt die de id-service gebruiken en sommige pagina&#39;s die dat niet doen, en deze allemaal in dezelfde analytische rapportsuite rapporteren. Dit komt vaak voor als u een algemene rapportsuite hebt die rapporten opstelt in verschillende domeinen.

Sluit de respijtperiode af nadat de id-service is geïmplementeerd op al uw webpagina&#39;s die in dezelfde rapportsuite rapporteren.

**S_vi Cookie-vereisten**

U hebt een respijtperiode nodig als u nieuwe bezoekers een s_vi koekje na het migreren aan de dienst van identiteitskaart wilt hebben. Dit is algemeen als uw implementatie het s_vi koekje leest en het in een variabele opslaat.

Sluit de respijtperiode af nadat uw implementatie de MID kan vastleggen in plaats van het s_vi cookie te lezen.

Zie ook: [Cookies en de Experience Cloud Identity Service](../introduction/cookies.md).

**De Integratie van Gegevens Clickstream**

U hebt een respijtperiode nodig als u gegevens naar een intern systeem verzendt vanuit een Clickstream-gegevensinvoer en die processen het `visid_high` en `visid_low` kolommen.

De respijtperiode beëindigen nadat het proces voor het invoeren van gegevens de `post_visid_high` en `post_visid_low` kolommen.

Zie ook: [Referentie kolom Clickstream](https://experienceleague.adobe.com/docs/analytics/export/analytics-data-feed/data-feed-overview.html).

## Stap 9: Testen en verifiëren {#section-f857542bfc70496dbb9f318d6b3ae110}

De [!DNL Experience Cloud] oplossingen in deze implementatie retourneren-id&#39;s in de vorm van sleutelwaardeparen. Elke oplossing gebruikt verschillende toetsen (bijvoorbeeld de [!DNL Analytics] SDID vs. [!DNL Target] mboxMCSDID) om dezelfde id te bevatten. Als u uw implementatie wilt testen, laadt u uw pagina&#39;s in een ontwikkelomgeving. Gebruik de browserconsole of software die HTTP-aanvragen en -reacties controleert om de hieronder vermelde id&#39;s te controleren. De ID-service is correct geïmplementeerd wanneer de onderstaande sleutelwaardeparen dezelfde id-waarden retourneren.

>[!TIP]
>
>U kunt de [Adobe Foutopsporing](https://experienceleague.adobe.com/docs/analytics/implementation/validate/debugger.html) of de [Charles HTTP-proxy](https://www.charlesproxy.com/) om deze oplossing-specifieke IDs te controleren. Nochtans, zou u zich vrij moeten voelen om welk hulpmiddel of debugger het beste voor u te gebruiken.

**Alle oplossingen**

Controleren op:

* [AMCV cookie](../introduction/cookies.md) in het domein waar u pagina wordt gehost.
* [!DNL Experience Cloud] ID (MID) met de [!DNL Adobe] foutopsporing of uw voorkeurshulpprogramma voor foutopsporing.

Voor extra controles die u helpen bepalen als de dienst van identiteitskaart behoorlijk werkt, zie [De Experience Cloud Identity Service testen en verifiëren](../implementation-guides/test-verify.md).

**Analytics**

Controleer in de JavaScript-aanvraag of de id van de SDID aanwezig is. De SDID van Analytics moet overeenkomen met de Target mboxMCSDID.

Als uw tests een identiteitskaart terugkeren, wijst dat op één van beiden van het volgende:

* U bent een terugkerende bezoeker in het migratieproces van verouderde [!DNL Analytics] ID&#39;s.
* U hebt een [respijtperiode](../reference/analytics-reference/grace-period.md) ingeschakeld.

Wanneer u een HULP ziet, controleer zijn waarde tegen [!DNL Target] mboxMCAVID. Deze waarden zijn identiek wanneer de dienst van identiteitskaart correct is uitgevoerd.

**Audience Manager**

Om server-kant het door:sturen te testen, zie [Hoe te om uw server-kant te verifiëren die implementatie door:sturen](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/server-side-forwarding/ssf-verify.html).

**Target**

Controleren op:

* mboxMCGVID
* mboxMCSDID (De mboxMCSDID moet overeenkomen met de Analytics SDID.)

Als uw tests een mboxMCAVID terugkeren, wijst dat op één van beiden van het volgende:

* U bent een terugkerende bezoeker in het migratieproces van verouderde [!DNL Analytics] ID&#39;s.
* U hebt een respijtperiode ingeschakeld.

Wanneer u een mboxMCAVID ziet, controleer zijn waarde tegen [!DNL Analytics] STEUN Deze waarden zijn identiek wanneer de dienst van identiteitskaart correct is uitgevoerd.

**Implementatie**

## Stap 10: Implementeren {#section-4188fa95e7dc455a986b48a6c517c1c9}

Implementeer de code nadat deze voor het testen is geslaagd.

Als u een respijtperiode hebt ingeschakeld:

* Zorg ervoor dat de opties Analytics ID (AID) en MID in de afbeeldingsaanvraag staan.
* Vergeet niet de respijtperiode uit te schakelen wanneer u voldoet aan de [criteria voor stopzetting](../implementation-guides/setup-aam-analytics-target.md#section-aceacdb7d5794f25ac6ff46f82e148e1).
