---
description: Functies worden vrijgegeven, bijgewerkt of gewijzigd in de Experience Cloud Identity Service voor 2016.
keywords: ID Service
seo-description: Functies worden vrijgegeven, bijgewerkt of gewijzigd in de Experience Cloud Identity Service voor 2016.
seo-title: Opmerkingen bij de release 2016
title: Opmerkingen bij de release 2016
uuid: 7a5a314a-3ff8-4561-9c64-6c10d2223887
translation-type: tm+mt
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# Opmerkingen bij de release 2016 {#release-notes}

Functies worden vrijgegeven, bijgewerkt of gewijzigd in de Experience Cloud Identity Service voor 2016.

Deze wijzigingen worden ook vastgelegd in de opmerkingen bij de release [Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/). Zie de [opmerkingen bij](https://marketing.adobe.com/resources/help/en_US/whatsnew/?f=c_legacy_releases.html) eerdere releases voor oudere [!DNL Experience Cloud] aankondigingen.

## Versie 1.10 {#section-7d719b3213344a46858835042e0214ed}

november 2016

>[!IMPORTANT]
>
>* Versie 1.10 vereist [!UICONTROL AppMeasurement] 1.8.0.
>* Met Experience Cloud Identity Service Library 2.0.0+ wordt de synchronisatie van id&#39;s standaard gestart voor Adobe Media Optimizer. Zie [Id-synchronisatie en Identieke snelheden](/help/introduction/match-rates.md)begrijpen.


**Oplossingen en verbeteringen**

* Toegevoegde instructies op hoe te om de dienst van identiteitskaart in een server-zijmilieu uit te voeren.
* Toegevoegd `Visitor.overwriteCrossDomainMCIDAndAID`, een booleaanse functie waarmee u de Experience Cloud en Analytics ID&#39;s kunt overschrijven op andere domeinen die u bezit. Zie [Bezoeker-id](../library/function-vars/overwrite-visitor-id.md#reference-9db13d637ce44fb6a8d519de5743ccde)overschrijven.

* Tijdstempel toegevoegd `TS = UTC` als een eigenschap van de `visitor.appendVisitorIDsTo`functie. De dienst van identiteitskaart gebruikt timestamp om te bepalen of het IDs in opnieuw richt URL zou moeten gebruiken die op een 5 minieme verouderingsinterval wordt gebaseerd. Zie Functie [voor bezoekersidentiteitskaart](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce)toevoegen.

* Er is `Visitor.getLocationHint,` een nieuwe functie toegevoegd die een regio-id retourneert. Zie Gebied-id&#39;s [ophalen (Locatiehint)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).

* Toegevoegde `idSyncByURL` en `idSyncByDataSource`twee functies waarmee u handmatig een id-synchronisatie kunt implementeren in het iFrame voor publiceren van bestemming. See [ID Synchronization by URL or Data Source](../library/get-set/idsync.md#reference-b01b88c083434cf8abbeabd3c6956c48).

* Oplossing voor een probleem dat de aanroep van de functie AppMeasurement heeft geblokkeerd indien `disableThirdPartyCalls:true`.
* Oplossing voor een probleem dat ervoor zorgde dat de id-service geen Cloud-id (MID) voor verschillende domeinen kon doorgeven.

## Versie 1.9.0 {#section-04e1b4d4b10d40468f2116b8119998e7}

Oktober 2016

**Oplossingen en verbeteringen**

* Het probleem waarbij unieke gebruikers-id&#39;s (AAMUUID&#39;s) van Audience Manager als Experience Cloud-id&#39;s werden doorgegeven aan de id-service, is opgelost.
* Als de time-to-live (TTL) voor een AMCV-cookie is verlopen, retourneert de id-service deze informatie nog steeds naar de server zolang het cookie een Experience Cloud-id bevat. Na deze vraag, doet de dienst van identiteitskaart een asynchrone vraag om het koekje bij te werken. Dit helpt de prestaties te verbeteren omdat de id-service niet hoeft te wachten op een serverreactie. De toepassing kan bestaande AMCV-cookiewaarden gebruiken en vervolgens een update aanvragen.
* De id-service synchroniseert Experience Cloud ID&#39;s (MID&#39;s) automatisch met Adobe Media Optimizer en andere interne Adobe-domeinen rechtstreeks op de pagina. Automatische synchronisatie is ingeschakeld voor alle bestaande en nieuwe accounts. Hierdoor worden de overeenkomende snelheden voor Media Optimizer verbeterd. Is van toepassing op VisitorAPI.js versie 1.8 of hoger. Zie ook, [Begrijpend de Synchronisatie van identiteitskaart en Gelijke Tarieven](../introduction/match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab).

**Nieuwe en herziene documentatie**

**Nieuw:** Regio en gebruikers-id&#39;s [ophalen van de AMCV-cookie](../reference/regions.md#concept-15b2c8c894b846a48f1f61a353cfdf4e)

## Versie 1.8.0 {#section-69f2eb5b246b4c7aafe116b7a2a5448a}

september 2016

**Oplossingen en verbeteringen**

Toegevoegd `disableThirdPartyCalls` als een optionele Booleaanse markering die u in de `Visitor.getInstance` functie kunt instellen. Wanneer `disableThirdPartyCalls= true`, zal de dienst van identiteitskaart geen vraag aan andere domeinen maken. Standaard `disableThirdPartyCalls= false`. Zie [disableThirdPartyCalls](../library/function-vars/disablethirdpartycalls.md#reference-fba90b095e9746daad46e3abb790d18b).

## Versie 1.7.0 {#section-f7d59104de6644fca3691480383d4644}

augustus 2016

**Oplossingen en verbeteringen**

* Toegevoegd `idSyncAttachIframeOnWindowLoad` als een optionele booleaanse markering die u kunt instellen in de `Visitor.getInstance` functie. Wanneer `idSyncAttachIframeOnWindowLoad= true`de id-service het iFrame voor synchronisatie van de id laadt tijdens het laden van het venster. Standaard wordt de iFrame zo snel mogelijk geladen door de id-service. Deze markering *vervangt* `idSyncAttachIframeASAP`, die is afgekeurd. Zie [Variabelen](../library/function-vars/function-vars.md)van de Functie Visitor.getInstance.

* Toegevoegde functionaliteit voor ondersteuning van id&#39; [!DNL Experience Cloud] s voor bijhouden in verschillende domeinen, native apps en hybride apps voor webovergangen. Zie Helperfunctie [voor bezoekersidentiteitskaart toevoegen](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce).

* Toegevoegde functies aan bezoekerAPI.js-code die bepalen of de id-service de client-side of server-side [!DNL Experience Cloud] id van de bezoeker heeft gegenereerd of of er een time-out is opgetreden voor id-aanroepen. Zie [Timeout Tracking Functies](../library/get-set/timeout-functions.md#reference-912bae0f116540df8c5dc1c008656c23) en het [Volgen van cliënt-zijbezoeker ID Generatie](../library/get-set/client-side-id.md#reference-8244dc6d832c4bbaaa97528096bcc2a6).

**Nieuwe en herziene documentatie**

Revised: [Requirements for the Experience Cloud Identity Service](../reference/requirements.md)

**Bekende problemen**

Klanten die [!DNL Audience Manager] DIL-code en bezoekerAPI.js-code op dezelfde pagina gebruiken, moeten de DIL-variabele instellen `secureDataCollection= false`. Zie [secureDataCollection](https://marketing.adobe.com/resources/help/en_US/aam/?f=dil-secure-data-collection.html).

## Versie 1.6.0 {#section-3faaa14bf3934c6a99b8f79ee06fc0d2}

juli 2016

>[!IMPORTANT]
>
>Versie 1.6.0 van de [!DNL Experience Cloud] id-service *vereist* AppMeasurement voor JavaScript versie 1.6.2. Als u aan de dienstversie van identiteitskaart 1.6.0 bevordert, gelieve te controleren u de juiste versie van de Code AppMetings gebruikt.

<table id="table_5472AAFA0DD2495DB8D92DEBE44A07A9"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Functie </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Delen van bronnen tussen verschillende bronnen (CORS) </p> </td> 
   <td colname="col2"> <p>Met CORS kunnen browsers bronnen aanvragen van een ander domein dan het huidige domein. De Experience Cloud Identity Service ondersteunt CORS-standaarden om bronaanvragen voor bronnen van verschillende oorsprong aan de clientzijde mogelijk te maken. De dienst van identiteitskaart keert aan JSONP- verzoeken op browsers terug die geen CORS steunen. </p> <p>Zie: </p> 
    <ul id="ul_15386385108F4E07824041DD6F2DC11E"> 
     <li id="li_DB8D5AA4A7004DE4AE9CBC31A389F5BD"> <a href="../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758" format="dita" scope="local"> Ondersteuning voor CORS in de Experience Cloud Identity Service </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**Oplossingen en verbeteringen**

* Een `d_fieldgroup` parameter toegevoegd aan ID synchronisatieaanroepen aan `dpm.demdex.net`. Deze nieuwe parameter wordt gebruikt voor interne het oplossen van problemen en het zuiveren doeleinden.

* Een titelkenmerk toegevoegd aan het iFrame van de ID-service. Met een iFrame-titel kunnen schermlezers pagina-informatie verschaffen aan gebruikers die hulp nodig hebben bij het werken met online-inhoud. Het iFrame-titelkenmerk is ingesteld op `Adobe ID Syncing iFrame`.
* Toegevoegd `idSyncAttachIframeASAP: true` als een optionele markering die u kunt instellen in de `Visitor.getInstance` functie. Wanneer `true`, laadt de dienst van identiteitskaart de synchronisatie iFrame van identiteitskaart zo snel mogelijk. Dit is ontworpen om ervoor te zorgen dat id-synchronisatiesnelheden worden verbeterd. Standaard laadt de id-service het iFrame bij het laden van het venster. Zie [Variabelen](../library/function-vars/function-vars.md)van de Functie Visitor.getInstance.

* Oplossing voor een bug met een callback-functie die ertoe heeft geleid dat AppMeasurement vastliep in een oneindige lus.
* Veranderde het standaardinterval in 30.000 milliseconden (van 500 milliseconden). `loadTimeout` Zie [Variabelen](../library/function-vars/function-vars.md)van de Functie Visitor.getInstance.

**Nieuwe en herziene documentatie**

**Nieuw**

* [Implementeer de Experience Cloud Identity Service voor Analytics](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd)
* [Implementeer de Experience Cloud Identity Service voor Analytics, Audience Manager en Target](../implementation-guides/setup-aam-analytics-target.md#concept-e7e2dc0d0bbe481db93328b5604b4673)

**Gereviseerd**

* [Vereisten voor de Experience Cloud Identity Service](../reference/requirements.md)
* [De Experience Cloud Identity Service testen en verifiëren](../implementation-guides/test-verify.md)

## Versie 1.5.7 {#section-735b4989a5744a42aeb2d97602dbda62}

Juni 2016

<table id="table_5D604D0820C84EC996ACB99126C8A3DF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Functie </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Wijzigingen in het <span class="codeph"> kenmerk iframe.sandbox </span> </p> </td> 
   <td colname="col2"> <p>De iFrame is nu zo ingesteld dat <span class="codeph"> iframe.sandbox='allow-scripts allow-same-origin'; </span>. </p> <p>Het toestaan van slechts deze 2 tokens helpt veiligheid verbeteren en verleent de dienst van identiteitskaart de basisfunctionaliteit die voor de synchronisatie van identiteitskaart wordt vereist. </p> <p>Het kenmerk sandbox wordt niet ondersteund in Internet Explorer versie 9 of lager. Zie de sectie Kenmerken in deze <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe" format="https" scope="external"> iFrame-documentatie voor meer informatie </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>De Experience Cloud ID (MID) coderen </p> </td> 
   <td colname="col2"> <p>De id-service codeert de MID-waarde die door de server wordt geretourneerd of wanneer deze door de <span class="codeph"> functie bezoeker.setMarketingCloudVisitorID() </span> wordt ingesteld. Zie <a href="../introduction/cookies.md" format="dita" scope="local"> Cookies en de Experience Cloud-id voor meer informatie over de MID </a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Oplossingen**

De bezoeker-API forceert niet langer een extra hersynchronisatieaanroep met Audience Manager wanneer er geen oude Analytics-bezoeker-id is.

## Versie 1.5.x {#section-a62ae48275324058b57edf66ee5a579f}

Mei 2016

**Documentatieupdates**

* [SDK-vereisten voor Android en iOS](../reference/requirements.md#section-73b2446fba8e463888642c7d7dfd94f1)
* [Data Workbench en Experience Cloud Identity Service](../reference/dwb.md#task-72df50a051944a47b01b0c0bc3d1e1d8)
* [De Experience Cloud Identity Service testen en verifiëren](../implementation-guides/test-verify.md)

## Versie 1.5.x {#section-0cfeef085cff4cbc8dff6cbc6fc32920}

april 2016

**Documentatieupdates**

[Implementeer de Experience Cloud Identity Service voor Doel](../implementation-guides/setup-target.md#concept-9b5a802132574e1181927ddd00e5c5af)

## Versie 1.5.4 {#section-1a44ba147fb3440ea7dec551faee3528}

maart 2016

<table id="table_F4ED1F88709E4D3BA69C747879A4E18F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Functie </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Ondersteuning voor uitschakelen </p> </td> 
   <td colname="col2"> <p>De service <span class="keyword"> Experience Cloud </span> ID biedt ondersteuning voor bezoekersverzoeken om te weigeren. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> Synchronisatie-interval van id wijzigen </p> </td> 
   <td colname="col2"> <p>De <span class="keyword"> </span> dienst van identiteitskaart van de Wolk van de Ervaring maakt nu de synchronisatievraag van identiteitskaart op elke vraag aan de servers van de gegevensinzameling. Eerder heeft de id-service slechts 1 aanvraag gedaan bij de eerste oproep om een <span class="keyword"> Experience Cloud- </span> id op te halen. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Documentatieupdates**

* [Implementeer de Experience Cloud Identity Service voor Analytics](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd) : Nieuwe procedure die beschrijft hoe te opstelling de dienst van identiteitskaart met [!DNL Analytics].

* [Ervaar zelf de beslissingspunten](../reference/analytics-reference/migration-decisions.md#concept-ba44803eea3c4cc185232a510cec0257) voor migratie van de cloud-identiteitsservice: Herziene tekst voor de duidelijkheid. Als u met één domein werkt, kunt u migreren van een CNAME voor gegevensverzameling als u dit niet meer wilt beheren. Nochtans, is er geen vereiste om te veranderen als uw CNAME werkt.

## Versie 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

januari 2016

**Documentatieupdates**

<table id="table_C1A5DBED6B104C0FBA54EC663D3B0E86"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Onderwerp </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../reference/authenticated-state.md" format="dita" scope="local"> Klant-id's en verificatiestatussen </a> </p> </td> 
   <td colname="col2"> <p>Herziene tekst. Klantnamen moeten alleen als niet-gecodeerde waarden worden doorgegeven. Met coderings-id's worden dubbelgecodeerde id's gemaakt. </p> </td> 
  </tr> 
 </tbody> 
</table>

