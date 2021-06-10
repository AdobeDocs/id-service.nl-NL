---
description: Browsers gebruiken het Delen van bronnen van oorsprong over de hele wereld (CORS) om bronnen van een ander domein dan het huidige domein aan te vragen. De dienst van de Identiteit van de Experience Cloud steunt normen CORS die deze cliënt-kant, dwars-oorsprong middelverzoeken toelaten. De dienst van identiteitskaart keert aan JSONP- verzoeken op oudere browsers terug of browsers die geen CORS steunen.
keywords: ID-service
title: CORS-ondersteuning in de Experience Cloud Identity Service
exl-id: 0e8ffe85-8d1f-42a0-aae3-a2b3b28c7bce
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# CORS-ondersteuning in de Experience Cloud Identity-service {#cors-support-in-the-experience-cloud-id-service}

Browsers gebruiken het Delen van bronnen van oorsprong over de hele wereld (CORS) om bronnen van een ander domein dan het huidige domein aan te vragen. De dienst van de Identiteit van de Experience Cloud steunt normen CORS die deze cliënt-kant, dwars-oorsprong middelverzoeken toelaten. De dienst van identiteitskaart keert aan JSONP- verzoeken op oudere browsers terug of browsers die geen CORS steunen.

## Problemen met Beleid van dezelfde oorsprong en de Verzoeken van de Dienst van identiteitskaart {#section-6608cf46d27143eeaeabacaa6aa14e8e}

Beleid van dezelfde oorsprong is beveiligingsbesturingselementen of beperkingen die door een webbrowser worden afgedwongen. Wanneer afgedwongen op dit niveau, bepaalt Webbrowser zelf als een verzoek om middelen die van één pagina aan een andere worden gemaakt wordt toegelaten of geblokkeerd. Om te bepalen als een verzoek een zelfde-oorsprong verzoek is, vergelijkt browser:

* Uniform Resource Identifiers (URI&#39;s)
* Hostnamen (bijvoorbeeld http://www.my-webpage-example.com)
* Poortnummers (bijvoorbeeld poort 80 en 440 voor HTTP- en HTTPS-aanvragen)

Browser staat een verzoek toe om te slagen als beide pagina&#39;s deze kenmerken delen en middelverzoeken blokkeert als zij niet.

## CORS lost problemen met zelfde-Oorspronkelijk Beleid {#section-76c87ec3295d447bab220c84f138c235} op

CORS biedt een veilige, effectieve manier om bronnen op verschillende domeinen aan te vragen. De specificatie CORS omvat een reeks kopballen van HTTP die browsers gebruiken om, middelverzoeken te verzenden te ontvangen en te evalueren. Het evalueren van een middelverzoek wordt genoemd a *`preflight check`*. Met deze controle kunnen browsers en servers bepalen welke aanvragen zijn toegestaan of geblokkeerd. De Preflight-controle is transparant voor de app, API of het script dat om een resource vraagt. Twee kopballen die in het proces van het middelverzoek belangrijk zijn omvatten:

* `Origin`: Een aanvraagkopbal die de bron van een verzoek identificeert.
* `Access-Control-Allow-Origin`: Een antwoordheader die aangeeft of een bron kan worden gedeeld met de aanvrager.

Laten we eens kijken hoe deze koppen werken. In dit voorbeeld zeggen we dat we een bedrijf voor financiële services hebben dat de [!DNL Experience Cloud] ID-service op hun site heeft geïmplementeerd, www.finance-website.com. De volgende lijst bepaalt hoe de CORS verzoek en reactiekopballen toegang tot een middel controleren.

<table id="table_B004ACF52B5A4D33B1DCF7EA77BE4E6D"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Actie </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Verzoek</b> </p> </td> 
   <td colname="col2"> <p>Wanneer de pagina van het financieringsbedrijf wordt geladen, vraagt de browser om <span class="codeph"> dpm.demdex.net</span>. Dit is een vraag aan het domein van de servers van de gegevensinzameling (DCS) die door de dienst van identiteitskaart wordt gebruikt. Deze domeinoverschrijdende aanvraag bevat de header: </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Oorsprong:https://www.finance-website.com</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Antwoord</b> </p> </td> 
   <td colname="col2"> <p>De reactie van het domein DCS omvat deze kopballen die de plaatstoegang van het financieringsbedrijf tot vereiste middelen verlenen: </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Toegang-controle-toestaan-Oorsprong: https://www.finance-website.com</span> </li> 
      <li> <span class="codeph"> Toegang-controle-toestaan-Referenties: true</span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

Zie ook [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa).

## Andere voordelen van het gebruik van CORS {#section-6f44f30694c44f95bf9854b8a2af8449}

In de onderstaande tabel worden enkele voordelen beschreven die CORS biedt aan klanten die de id-service gebruiken.

<table id="table_AEB51A263D454F90B66E8C8D0513CF79"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Voordeel </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><b>Meer beveiliging</b> </p> </td> 
   <td colname="col2"> <p>CORS gebruikt <a href="https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest" format="https" scope="external"> XMLHttpRequest</a> om gegevens aan te vragen en over te brengen. Deze methode is veiliger dan een JSONP- verzoek. Het zorgt ervoor dat er geen manier is om arbitraire JavaScript uit te voeren, die in de reactie van DCS zou kunnen worden bevat. De antwoordlading van CORS XMLHttpRequest wordt geparseerd door de dienst JavaScript van identiteitskaart en niet eenvoudig uitgevoerd in een callback functie. </p> <p> <p>Opmerking: Voor het accepteren van cookies heeft het <span class="codeph"> XMLHttpRequest</span>-object de eigenschap <span class="codeph"> withCredentials</span> ingesteld op <span class="codeph"> true</span>. Deze eigenschap wordt ondersteund in Chrome, Firefox, Internet Explorer (v10+), Opera en Safari. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>Prestatieverbeteringen</b> </p> </td> 
   <td colname="col2"> <p>CORS helpt de prestaties te verbeteren omdat: </p> 
    <ul id="ul_EC3A178003A94D70883B914050D7C464"> 
     <li id="li_F8B44352BFBB46CDBD07AE40B9F2D0EC">De browser beheert bronverzoeken. Het aanvraagproces is transparant voor de id-service. </li> 
     <li id="li_C63E43A4CAB84210AB6A39100E5864BE">In tegenstelling tot asynchrone JSONP- verzoeken, schrapt browser niet de-rangschikking en rijCORS- verzoeken. </li> 
     <li id="li_1A2A15F591B84D1BAED3CFAB391EEBEC">De id-service reageert permissief. Dit betekent dat wanneer een URL wordt doorgegeven als <span class="codeph"> Origin</span>, de id-service de pagina toegang geeft tot de vereiste bronnen. </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
