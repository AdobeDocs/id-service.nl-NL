---
description: De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van de Experience Cloud voor 2016.
keywords: ID-service
title: Opmerkingen bij de release 2016
feature-set: Experience Cloud Services
feature: TK421
exl-id: f96b9869-6282-4090-b392-797608e25a51
source-git-commit: d027f7fca8cf62d6b5d80ec3c37049ddd1afdd70
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 2%

---

# Opmerkingen bij de release 2016 {#release-notes}

De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van de Experience Cloud voor 2016.

Deze wijzigingen worden ook vastgelegd in de [Opmerkingen bij de release Experience Cloud](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=nl).

## Versie 1.10 {#section-7d719b3213344a46858835042e0214ed}

november 2016

>[!IMPORTANT]
>
>* Versie 1.10 is vereist [!UICONTROL AppMeasurement] 1.8.0.
>* Met Experience Cloud Identity Service Library 2.0.0+, wordt de synchronisatie van id&#39;s standaard gestart voor Adobe Media Optimizer. Zie [Identiteitssynchronisatie en gelijke Tarieven begrijpen](/help/introduction/match-rates.md).


**Oplossingen en verbeteringen**

* Toegevoegde instructies op hoe te om de dienst van identiteitskaart in een server-zijmilieu uit te voeren.
* Toegevoegd `Visitor.overwriteCrossDomainMCIDAndAID`, een Booleaanse functie waarmee u de Experience Cloud- en Analyse-id&#39;s kunt overschrijven op andere domeinen die u bezit. Zie [Bezoeker-id overschrijven](../library/function-vars/overwrite-visitor-id.md#reference-9db13d637ce44fb6a8d519de5743ccde).

* Toegevoegd `TS = UTC` timestamp as a property of the `visitor.appendVisitorIDsTo`functie. De dienst van identiteitskaart gebruikt timestamp om te bepalen of het IDs in opnieuw richt URL zou moeten gebruiken die op een 5 minieme verouderingsinterval wordt gebaseerd. Zie [Functie van bezoeker-id toevoegen](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce).

* Toegevoegd `Visitor.getLocationHint,` een nieuwe functie die een regio-id retourneert. Zie [Gebied-id&#39;s ophalen (locatiehint)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).

* Toegevoegd `idSyncByURL` en `idSyncByDataSource`, 2 functies waarmee u handmatig een id-synchronisatie kunt implementeren in het iFrame voor publiceren van doelen. Zie [ID-synchronisatie op URL of gegevensbron](../library/get-set/idsync.md#reference-b01b88c083434cf8abbeabd3c6956c48).

* Oplossing voor een probleem dat de trackingaanroep van AppMeasurement blokkeerde als `disableThirdPartyCalls:true`.
* Oplossing voor een probleem dat ervoor zorgde dat de id-service de Experience Cloud-id (MID) niet kon doorgeven over verschillende domeinen.

## Versie 1.9.0 {#section-04e1b4d4b10d40468f2116b8119998e7}

Oktober 2016

**Oplossingen en verbeteringen**

* Het probleem waarbij unieke gebruikers-id&#39;s (AAMUUID&#39;s) van de Audience Manager als Experience Cloud-id&#39;s werden doorgegeven aan de id-service, is opgelost.
* Als time-to-live (TTL) voor een AMCV-cookie is verlopen, zal de id-service deze informatie nog steeds aan de server retourneren zolang het cookie een Experience Cloud-id bevat. Na deze vraag, doet de dienst van identiteitskaart een asynchrone vraag om het koekje bij te werken. Dit helpt de prestaties te verbeteren omdat de id-service niet hoeft te wachten op een serverreactie. De toepassing kan bestaande AMCV-cookiewaarden gebruiken en vervolgens een update aanvragen.
* De dienst van identiteitskaart synchroniseert Experience Cloud IDs (MIDs) met Adobe Media Optimizer en andere interne domeinen van Adobe direct op de pagina automatisch. Automatische synchronisatie is ingeschakeld voor alle bestaande en nieuwe accounts. Hierdoor worden de overeenkomende snelheden voor Media Optimizer verbeterd. Is van toepassing op VisitorAPI.js versie 1.8 of hoger. Zie ook: [Identiteitssynchronisatie en gelijke Tarieven begrijpen](../introduction/match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab).

**Nieuwe en herziene documentatie**

**Nieuw:** [Regio en gebruikers-id&#39;s ophalen van de AMCV-cookie](../reference/regions.md#concept-15b2c8c894b846a48f1f61a353cfdf4e)

## Versie 1.8.0 {#section-69f2eb5b246b4c7aafe116b7a2a5448a}

september 2016

**Oplossingen en verbeteringen**

Toegevoegd `disableThirdPartyCalls` als een optionele Booleaanse markering kunt u instellen in het dialoogvenster `Visitor.getInstance` functie. Wanneer `disableThirdPartyCalls= true`, zal de dienst van identiteitskaart geen vraag aan andere domeinen maken. Standaard, `disableThirdPartyCalls= false`. Zie [disableThirdPartyCalls](../library/function-vars/disablethirdpartycalls.md#reference-fba90b095e9746daad46e3abb790d18b).

## Versie 1.7.0 {#section-f7d59104de6644fca3691480383d4644}

augustus 2016

**Oplossingen en verbeteringen**

* Toegevoegd `idSyncAttachIframeOnWindowLoad` als een optionele booleaanse markering kunt u instellen in het dialoogvenster `Visitor.getInstance` functie. Wanneer `idSyncAttachIframeOnWindowLoad= true`, laadt de id-service het iFrame voor synchronisatie van de id tijdens het laden van het venster. Standaard wordt de iFrame zo snel mogelijk geladen door de id-service. Deze markering *vervangt* `idSyncAttachIframeASAP`, die afgekeurd is. Zie [Variabelen van de functie Visitor.getInstance](../library/function-vars/function-vars.md).

* Toegevoegde functionaliteit voor ondersteuning van tekstspatiëring [!DNL Experience Cloud] Id&#39;s in verschillende domeinen, native apps en hybride apps voor webovergangen. Zie [Helpfunctie voor bezoekersidentiteitskaart toevoegen](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce).

* Toegevoegde functies aan bezoekerAPI.js-code die bepalen of de id-service de bezoeker heeft gegenereerd [!DNL Experience Cloud] ID client-side of server-side of als ID-oproepen time-out hebben. Zie [Functies voor bijhouden van time-out](../library/get-set/timeout-functions.md#reference-912bae0f116540df8c5dc1c008656c23) en [Het volgen van Cliënt-zijBezoeker ID Generatie](../library/get-set/client-side-id.md#reference-8244dc6d832c4bbaaa97528096bcc2a6).

**Nieuwe en herziene documentatie**

Gereviseerd: [Vereisten voor de Experience Cloud Identity Service](../reference/requirements.md)

**Bekende problemen**

Klanten die [!DNL Audience Manager] DIL-code en bezoekerAPI.js-code op dezelfde pagina moeten de variabele DIL instellen `secureDataCollection= false`. Zie [secureDataCollection](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-overview.html).

## Versie 1.6.0 {#section-3faaa14bf3934c6a99b8f79ee06fc0d2}

juli 2016

>[!IMPORTANT]
>
>Versie 1.6.0 van het [!DNL Experience Cloud] ID-service *vereist* AppMeasurement voor JavaScript versie 1.6.2. Als u aan de dienstversie van identiteitskaart 1.6.0 bevordert, gelieve te zorgen u de juiste versie van de Code AppMetings gebruikt.

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
   <td colname="col2"> <p>Met CORS kunnen browsers bronnen aanvragen van een ander domein dan het huidige domein. De dienst van de Identiteit van de Experience Cloud steunt normen CORS om cliëntkant, dwars-oorsprong middelverzoeken toe te laten. De dienst van identiteitskaart keert aan JSONP- verzoeken op browsers terug die geen CORS steunen. </p> <p>Zie: </p> 
    <ul id="ul_15386385108F4E07824041DD6F2DC11E"> 
     <li id="li_DB8D5AA4A7004DE4AE9CBC31A389F5BD"> <a href="../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758" format="dita" scope="local"> CORS-ondersteuning in de Experience Cloud Identity Service </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**Oplossingen en verbeteringen**

* Toegevoegde `d_fieldgroup` parameter aan de synchronisatievraag van identiteitskaart `dpm.demdex.net`. Deze nieuwe parameter wordt gebruikt voor interne het oplossen van problemen en het zuiveren doeleinden.

* Een titelkenmerk toegevoegd aan het iFrame van de ID-service. Met een iFrame-titel kunnen schermlezers pagina-informatie verschaffen aan gebruikers die hulp nodig hebben bij het werken met online-inhoud. Het iFrame-titelkenmerk is ingesteld op `Adobe ID Syncing iFrame`.
* Toegevoegd `idSyncAttachIframeASAP: true` als een optionele markering kunt u instellen in het dialoogvenster `Visitor.getInstance` functie. Wanneer `true`De id-service laadt de iFrame voor ID-synchronisatie zo snel mogelijk. Dit is ontworpen om ervoor te zorgen dat id-synchronisatiesnelheden worden verbeterd. Standaard laadt de id-service het iFrame bij het laden van het venster. Zie [Variabelen van de functie Visitor.getInstance](../library/function-vars/function-vars.md).

* Oplossing voor een bug met een callback-functie die ertoe heeft geleid dat AppMeasurement vastliep in een oneindige lus.
* De standaardinstelling gewijzigd `loadTimeout` interval tot 30.000 milliseconden (van 500 milliseconden). Zie [Variabelen van de functie Visitor.getInstance](../library/function-vars/function-vars.md).

**Nieuwe en herziene documentatie**

**Nieuw**

* [Implementeer de Experience Cloud Identity Service voor Analytics](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd)
* [Voer de Dienst van de Identiteit van Experience Cloud voor Analytics, Audience Manager, en Doel uit](../implementation-guides/setup-aam-analytics-target.md#concept-e7e2dc0d0bbe481db93328b5604b4673)

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
   <td colname="col1"> <p>Wijzigingen in de <span class="codeph"> iframe.sandbox </span> attribute </p> </td> 
   <td colname="col2"> <p>Het iFrame is nu zo ingesteld dat <span class="codeph"> iframe.sandbox='allow-scripts allow-same-origin'; </span>. </p> <p>Het toestaan van slechts deze 2 tokens helpt veiligheid verbeteren en verleent de dienst van identiteitskaart de basisfunctionaliteit die voor de synchronisatie van identiteitskaart wordt vereist. </p> <p>Het kenmerk sandbox wordt niet ondersteund in Internet Explorer versie 9 of lager. Zie de sectie Kenmerken in deze <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe" format="https" scope="external"> iFrame-documentatie </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>De Experience Cloud-id (MID) coderen </p> </td> 
   <td colname="col2"> <p>De dienst van identiteitskaart codeert de MID waarde die van de server is teruggekeerd of wanneer het door wordt geplaatst <span class="codeph"> bezoeker.setMarketingCloudVisitorID() </span> functie. Voor meer informatie over MID, zie <a href="../introduction/cookies.md" format="dita" scope="local"> Cookies en de Experience Cloud-id </a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Oplossingen**

De bezoeker-API forceert niet langer een extra hersynchronisatieaanroep met Audience Manager wanneer er geen oude Analytics-bezoeker-id is.

## Versie 1.5.x {#section-a62ae48275324058b57edf66ee5a579f}

Mei 2016

**Documentatie-updates**

* [SDK-vereisten voor Android en iOS](../reference/requirements.md#section-73b2446fba8e463888642c7d7dfd94f1)
* [Data Workbench en Experience Cloud Identity Service](../reference/dwb.md#task-72df50a051944a47b01b0c0bc3d1e1d8)
* [De Experience Cloud Identity Service testen en verifiëren](../implementation-guides/test-verify.md)

## Versie 1.5.x {#section-0cfeef085cff4cbc8dff6cbc6fc32920}

april 2016

**Documentatie-updates**

[Voer de Dienst van de Identiteit Experience Cloud voor Doel uit](../implementation-guides/setup-target.md#concept-9b5a802132574e1181927ddd00e5c5af)

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
   <td colname="col2"> <p>De <span class="keyword"> Experience Cloud </span> De id-service ondersteunt aanvragen om te weigeren door bezoekers. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> Synchronisatie-interval van id wijzigen </p> </td> 
   <td colname="col2"> <p>De <span class="keyword"> Experience Cloud-id </span> De dienst maakt nu de synchronisatievraag van identiteitskaart op elke vraag aan de servers van de gegevensinzameling. Eerder deed de dienst van identiteitskaart slechts 1 verzoek op de eerste vraag om een <span class="keyword"> Experience Cloud </span> ID. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Documentatie-updates**

* [Implementeer de Experience Cloud Identity Service voor Analytics](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd) : Nieuwe procedure die beschrijft hoe te opstelling de dienst van identiteitskaart met [!DNL Analytics].

* [Experience Cloud-beslissingspunten voor identiteitsservicemigratie](../reference/analytics-reference/migration-decisions.md#concept-ba44803eea3c4cc185232a510cec0257) : Herziene tekst voor de duidelijkheid. Als u met één domein werkt, kunt u migreren van een CNAME voor gegevensverzameling als u dit niet meer wilt beheren. Nochtans, is er geen vereiste om te veranderen als uw CNAME werkt.

## Versie 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

januari 2016

**Documentatie-updates**

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
