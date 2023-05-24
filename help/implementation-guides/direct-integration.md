---
description: Met deze implementatie kunnen klanten de id-service gebruiken op apparaten die onze JavaScript- of SDK-code niet kunnen accepteren of bewerken. Dit geldt onder andere voor apparaten zoals gameconsoles, slimme tv's of andere toestellen die geschikt zijn voor internet. Zie deze sectie voor syntaxis, codevoorbeelden en definities.
keywords: ID-service
title: Directe integratie met de Experience Cloud Identity Service
exl-id: 29565b74-5fe7-41f7-b278-6a90559faab9
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 1%

---

# Directe integratie met de Experience Cloud Identity Service {#direct-integration-with-the-experience-cloud-id-service}

Met deze implementatie kunnen klanten de id-service gebruiken op apparaten die onze JavaScript- of SDK-code niet kunnen accepteren of bewerken. Dit geldt onder andere voor apparaten zoals gameconsoles, slimme tv&#39;s of andere toestellen die geschikt zijn voor internet. Zie deze sectie voor syntaxis, codevoorbeelden en definities.

## Syntaxis {#section-a4754afec5ad40b6be00d6f1011d68bb}

Apparaten die de VisitorAPI.js of SDK codebibliotheken niet kunnen gebruiken kunnen vraag rechtstreeks aan de servers van de gegevensinzameling (DCS) maken die door de dienst van identiteitskaart worden gebruikt. Om dit te doen, zou u roepen `dpm.demdex.net` en maak uw aanvraag op zoals hieronder wordt getoond. *Cursief* Hiermee wordt een tijdelijke aanduiding voor een variabele aangegeven.

![](assets/directSyntax.png)

In dit syntaxisvoorbeeld, `d_` prefix identificeert de zeer belangrijk-waardeparen in de vraag als systeem-vlakke variabele. U kunt er een paar doorgeven `d_` parameters aan de dienst van identiteitskaart, maar blijf geconcentreerd op de zeer belangrijk-waardeparen zoals aangetoond in de code hierboven. Zie voor meer informatie over andere variabelen [Ondersteunde kenmerken voor DCS API-aanroepen](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-keys.html).

De id-service ondersteunt HTTP- en HTTPS-aanroepen. Gebruik HTTPS om gegevens van een beveiligde pagina door te geven.

## Voorbeeldverzoek {#section-26302b8851704888b6f8e6b2071bcdb0}

Uw verzoek kan er ongeveer zo uitzien als hieronder weergegeven voorbeeld. Lange variabelen zijn ingekort.

![](assets/directExample.png)

## Monsterreactie {#section-89bc103b3e9e4a8b98e74c32897b1200}

De id-service retourneert gegevens in een JSON-object, zoals hieronder wordt weergegeven. Je reactie kan anders zijn.

```js
{
     "d_mid":"12345",
     "dcs_region":"6",
     "id_sync_ttl":"604800",
     "d_blob":"wxyz5432"
}
```

## Parameters voor aanvragen en antwoorden gedefinieerd {#section-4a9912b545364dc4acad4f1ea5ec641d}

**Parameters aanvragen**

<table id="table_C8FFA89AB74E4E31A6926CDE5CD54217"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Parameter </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> dpm.demdex.net</span> </p> </td> 
   <td colname="col2"> <p>Een bestaand domein dat wordt beheerd door <span class="keyword"> Adobe</span>. Zie <a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html" format="https" scope="external">Inzicht in calls naar het Demdex-domein</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_mid</span> </p> </td> 
   <td colname="col2"> <p>De Experience Cloud-bezoeker-id. Zie <a href="../introduction/cookies.md" format="dita" scope="local"> Cookies en de Experience Cloud Identity Service</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_orgid</span> </p> </td> 
   <td colname="col2"> <p>Je Experience Cloud Organisatie-id. Zie voor hulp bij het zoeken naar deze id: <a href="../reference/requirements.md" format="dita" scope="local"> Vereisten voor de Experience Cloud Identity Service</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_cid</span> </p> </td> 
   <td colname="col2"> <p>Een optionele parameter die de Data Provider ID (DPID), de Unique User ID (DPUUID) en een <a href="../reference/authenticated-state.md" format="dita" scope="local"> geverifieerde status-id</a> naar de id-service. Zoals getoond in de codesteekproef, scheidt DPID en DPUUID met het niet-druk controlekarakter, <span class="codeph"> %01</span>. </p> <p> <b>DPID en DPUUID</b> </p> <p>In de <span class="codeph"> d_cid</span> parameter, elke verwante combinatie DPID en DPUUID aan het zelfde toewijzen <span class="codeph"> d_cid</span> parameter. Hiermee kunt u meerdere id-sets in één aanvraag retourneren. Bovendien scheidt u de DPID, DPUUID en de optionele verificatiemarkering met het niet-afdrukbare besturingsteken. <span class="codeph"> %01</span>. In de onderstaande voorbeelden worden de provider en de gebruikers-id's gemarkeerd in <b>vet</b> tekst. </p> 
    <ul id="ul_2E19D837296B40E9ACD096495CF711C5"> 
     <li id="li_5B94B057654440B99B989BA60E4ED053">Syntaxis: <span class="codeph">...d_cid=DPID%01DPUUID%01authentication state..</span> </li> 
     <li id="li_B07833EF51D54F088574B7B7F9FB841A">Voorbeeld: <span class="codeph">...d_cid=123%01456%011...</span> </li> 
    </ul> <p> <b>Verificatiestatus</b> </p> <p>Dit is een optionele id in het dialoogvenster <span class="codeph"> d_cid</span> parameter. Uitgedrukt als een geheel getal, identificeert het gebruikers op basis van hun verificatiestatus, zoals hieronder wordt weergegeven: </p> 
    <ul id="ul_E2B36922B11C4AA2A9016B6E2DC9EDAA"> 
     <li id="li_31C018E3F9514B938C73EF40C436715F"> <span class="codeph"> 0</span> (Onbekend) </li> 
     <li id="li_1F125C3879324C2F8EF4613C0ECB5F02"> <span class="codeph"> 1</span> (Geverifieerd) </li> 
     <li id="li_EF6792D0115D407485079D5D7480D965"> <span class="codeph"> 2</span> (Afgemeld) </li> 
    </ul> <p>Als u een verificatiestatus wilt opgeven, stelt u deze markering in na de variabele gebruikersnaam (UUID). Scheid de UUID- en authenticatiemarkering met het niet-afdrukbare besturingsteken. <span class="codeph"> %01</span>. In de onderstaande voorbeelden worden de verificatie-id's gemarkeerd in <b>vet</b> tekst. </p> <p>Syntaxis: <span class="codeph">...d_cid=DPID%01DPUUID%01authentication state</span> </p> <p>Voorbeelden: </p> 
    <ul id="ul_4C1054CE860A4D9C8DD85C2A8020C47F"> 
     <li id="li_AD4000BF3E0146C0BD37B1EC513EC314">Onbekend: <span class="codeph">...d_cid=123%01456%010...</span> </li> 
     <li id="li_B037D424AADA4D41BF29381A9602AE61">Voor authentiek verklaard: <span class="codeph">...d_cid=123%01456%011...</span> </li> 
     <li id="li_0410FCB9E60D4DD08E7898D814E1C3C9">Afgemeld: <span class="codeph">...d_cid=123%01456%012...</span> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> dcs_region</span> </p> </td> 
   <td colname="col2"> <p>De dienst van identiteitskaart is geografisch verdeeld en lading-evenwichtig systeem. Identiteitskaart identificeert het gebied van het gegevenscentrum dat de vraag behandelt. Zie <a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html" format="https" scope="external"> Id's, locaties en hostnamen van DCS-regio's</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_cb</span> </p> </td> 
   <td colname="col2"> <p> <i>(Optioneel)</i> Een callback-parameter waarmee u een JavaScript-functie in de hoofdtekst van de aanvraag kunt uitvoeren. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_blob</span> </p> </td> 
   <td colname="col2"> <p>Een gecodeerd segment JavaScript-metagegevens. De groottebeperkingen beperken de blob tot 512 bytes of minder. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_ver</span> </p> </td> 
   <td colname="col2"> <p>Vereist. Hiermee wordt het API-versienummer ingesteld. Deze set laten staan als <span class="codeph"> d_ver=2</span>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Responsparameters**

Sommige responsparameters maken deel uit van de aanvraag en zijn gedefinieerd in de bovenstaande sectie.

<table id="table_58D0E8876DDC4A81B1F24F845E87EC18"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Parameter </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> id_sync_ttl</span> </p> </td> 
   <td colname="col2"> <p>Het re-synchronisatieinterval, dat in seconden wordt gespecificeerd. Het standaardinterval is 604.800 seconden (7 dagen). </p> </td> 
  </tr> 
 </tbody> 
</table>
