---
description: Deze configuraties laten verschillende instanties van de de dienstcode van identiteitskaart die in een iFrame en op de ouderpagina wordt uitgevoerd met elkaar communiceren. Zij worden ontworpen helpen problemen met 2 specifieke gebruiksgevallen oplossen waar u of niet de ouderpagina/het domein kunt controleren en u hebt de dienstcode van identiteitskaart die in iFrame van een domein laadt dat u controle hebt. Ze zijn beschikbaar in VisitorAPI.js code versie 2.2 of hoger.
keywords: ID-service
title: whitelistParentDomain en whitelistIframeDomains
exl-id: 0ed1da79-7129-4f5f-b7ad-901348a13866
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 3%

---

# whitelistParentDomain en whitelistIframeDomains{#whitelistparentdomain-and-whitelistiframedomains}

Deze configuraties laten verschillende instanties van de de dienstcode van identiteitskaart die in een iFrame en op de ouderpagina wordt uitgevoerd met elkaar communiceren. Zij worden ontworpen helpen problemen met 2 specifieke gebruiksgevallen oplossen waar u of niet de ouderpagina/het domein kunt controleren en u hebt de dienstcode van identiteitskaart die in iFrame van een domein laadt dat u controle hebt. Ze zijn beschikbaar in VisitorAPI.js code versie 2.2 of hoger.

Inhoud:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-f645198bbaba4fba8961acb6e88d1470" format="dita" scope="local"> Syntaxis </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-09d0049fe88a473baa69d404c50bf8ae" format="dita" scope="local"> Codevoorbeeld </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-fc2eeb93546b406fae3b102dbcd11de7" format="dita" scope="local"> Gevallen gebruiken  </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2" format="dita" scope="local"> Configuratieveiligheid en -beveiliging  </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-30c6a9f4dcdc4265a1149260b97cc057" format="dita" scope="local"> Ondersteunde API-methoden voor bezoekers  </a> </li> 
</ul>

## Syntaxis {#section-f645198bbaba4fba8961acb6e88d1470}

Beide configuratieelementen worden vereist wanneer u deze code gebruikt.

<table id="table_237108A4D40F4AAC981D0060BA68F881"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Configuratiesyntaxis </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> whitelistParentDomain: "  <span class="varname"> Domeinnaam van bovenliggende pagina  </span>"  </span> </p> </td> 
   <td colname="col2"> <p>Accepteert één domeinnaam die als tekenreeks wordt doorgegeven. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> whitelistIframeDomains: [  <span class="varname"> "iFrame domain","iFrame domain","iFrame domain"  </span>]  </span> </p> </td> 
   <td colname="col2"> <p>Accepteert een of meer iFrame-domeinnamen die worden doorgegeven als een array. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Codevoorbeeld {#section-09d0049fe88a473baa69d404c50bf8ae}

Uw geconfigureerde [!UICONTROL ID service]-code zou er ongeveer hetzelfde uitzien als dit voorbeeld.

```js
//Instantiate Visitor 
var visitor = Visitor.getInstance("Insert Experience Cloud Organization ID here",{ 
 ... 
 //Add parent page domain name and iFrame domain names 
 whitelistParentDomain: "parentpageA.com", 
 whitelistIframeDomains: ["iFrameDomain1.com","iFrameDomain2.com"], 
 ... 
 } 
);
```

## Gevallen {#section-fc2eeb93546b406fae3b102dbcd11de7} gebruiken

Deze configuraties helpen het probleem op te lossen van het plaatsen van een de dienstkoekje van identiteitskaart en het toewijzen van een bezoekersidentiteitskaart wanneer browsers derdekoekjes blokkeren en als één van beiden van deze voorwaarden van toepassing is:

* U bestuurt de bovenliggende pagina of het bovenliggende domein al dan niet.
* ID-servicecode is niet geïnstalleerd op de bovenliggende pagina, maar is geïmplementeerd in een iFrame.

>[!TIP]
>
>U kunt deze configuraties ook willen uitvoeren wanneer u video in een iFrame met [Videohartslag](https://docs.adobe.com/content/help/nl-NL/media-analytics/using/media-overview.html) dient. Voor een goede werking van het videolettertype is een id-service-id (de MID) vereist.

**Hoofdlettergebruik 1: Browser blokkeert de Koekjes van de Derde en de Dienst van identiteitskaart wordt uitgevoerd op iFrame en de Pagina van de Ouder**

<table id="table_B479AA96DBE64685A253A6DF98D81B31"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Gebruiksscenario-element </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Voorwaarden</b> </p> </td> 
   <td colname="col2"> <p>Dit gebruiksgeval omvat de volgende voorwaarden: </p> <p> 
     <ul id="ul_DC748846585745B0AB74398D82BDA53A"> 
      <li id="li_6E04CF0B6A204B4D8856656B0C9EF2A5">Bedrijf A implementeert de dienst van identiteitskaart op hun homepage. </li> 
      <li id="li_B53AE0F0C69844E7B6C4D3464C57883B">Bedrijf A implementeert de id-service in iFrame op hun startpagina. </li> 
      <li id="li_07E0A6D7BEB140E4B9FB6C7B9629B860">Bedrijf A bezit de ouderpagina en iFrame en heeft de dienst van identiteitskaart in beide plaatsen uitgevoerd. </li> 
      <li id="li_76967BD69DDB40A8A9C915DADC58AC62">Een klant laadt de bovenliggende pagina in een browser die cookies van derden blokkeert. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Resultaten</b> </p> </td> 
   <td colname="col2"> <p>Onder deze voorwaarden kan de id-service: </p> <p> 
     <ul id="ul_12356701501E40DFA57903494FFE58F7"> 
      <li id="li_B57EDF1B0762486F95FA6526C047390C">Werkt goed op de bovenliggende pagina. Het vraagt en plaatst het koekje AMCV en wijst een unieke identiteitskaart aan de plaatsbezoeker toe. </li> 
      <li id="li_BA9F42C759E747EAAE14DD3FBB6130A5">Werkt niet in het iFrame. De reden hiervoor is dat de browser het iFrame ziet als een derdedomein en dat de id-service het AMCV-cookie niet kan instellen. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Oplossing</b> </p> </td> 
   <td colname="col2"> <p>Wijzig de id-service <span class="codeph"> Visitor.getInstance </span> in het iFrame met deze whitelandconfiguraties. Geef de bovenliggende en onderliggende domeinen in de code op. Met deze configuraties kan de ID-servicecode in het iFrame de ID-servicecode op de bovenliggende pagina controleren op een bezoeker-id. </p> <p>Als de ID-servicecode in het iFrame geen bovenliggende pagina voor reacties ontvangt, genereren deze configuraties een lokale bezoeker-id. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Hoofdlettergebruik 2: Een id aanvragen van een iFrame dat is ingesloten in een bovenliggende pagina die u niet bestuurt of die de id-service niet gebruikt**

<table id="table_1F21710F9D5F493BA6BA5974F2966DF4"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Gebruiksscenario-element </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Voorwaarden</b> </p> </td> 
   <td colname="col2"> <p>Dit gebruiksgeval omvat de volgende voorwaarden: </p> <p> 
     <ul id="ul_356E8FB0B1D14F46A844FE5281967E28"> 
      <li id="li_1285D945361842268B46FB492A3B5AA5">Bedrijf A gebruikt de id-service niet. </li> 
      <li id="li_880D6D473F8342FF9BB49FCE111FD61A">Bedrijf A laadt een iFrame op de pagina. Dit iFrame is eigendom van Bedrijf B en laadt in een afzonderlijk domein dan Bedrijf A. </li> 
      <li id="li_7988F0272B094FE0B398006AD4E6F81B">De browser blokkeert cookies van derden. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Resultaten</b> </p> </td> 
   <td colname="col2"> <p>Onder deze voorwaarden kan de id-service: </p> <p> 
     <ul id="ul_A92D90896E5A42C5804AC5CE83E8EB25"> 
      <li id="li_9734EA9C5D9D4F908DE783188C9E5530">Werkt niet in het iFrame. De reden hiervoor is dat de browser het iFrame ziet als een derdedomein en dat de id-service het AMCV-cookie niet kan instellen. </li> 
      <li id="li_3F4BE9048E774902A867D67E5A80674D">Kan geen bezoekersidentiteitskaart van de ouderpagina krijgen omdat Bedrijf A deze dienst niet gebruikt. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Oplossing</b> </p> </td> 
   <td colname="col2"> <p>Wijzig de id-service <span class="codeph"> Visitor.getInstance </span> in het iFrame met deze whitelandconfiguraties. Geef de bovenliggende en onderliggende domeinen in de code op. Met deze configuraties kan de ID-servicecode in het iFrame de ID-servicecode op de bovenliggende pagina controleren op een bezoeker-id. </p> <p>Als de ID-servicecode in het iFrame geen bovenliggende pagina voor reacties ontvangt, genereren deze configuraties een lokale bezoeker-id. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Configuratiebeveiliging {#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2}

U kunt deze configuraties veilig implementeren omdat:

* De dienst van identiteitskaart die op ouderdomein en het iFrame domein wordt uitgevoerd moet de zelfde organisatieidentiteitskaart gebruiken Deze witte lijstconfiguraties zullen niet werken wanneer organisatie IDs op de ouder of in iFrame verschillend zijn.
* Deze configuraties communiceren alleen met het domein en de iFrames die in de code zijn opgegeven.
* De communicatie tussen iFrame en de bovenliggende pagina heeft een specifieke indeling. Als de id-service op de bovenliggende pagina geen aanvraag in de verwachte indeling ontvangt, mislukt dit deelproces.

## Ondersteunde API-methoden voor bezoekers {#section-30c6a9f4dcdc4265a1149260b97cc057}

De dienst van identiteitskaart steunt een beperkte reeks openbare API methodes wanneer u deze witte lijstconfiguraties implementeert. De ondersteunde methoden variëren afhankelijk van de hierboven beschreven gebruiksscenario&#39;s.

<table id="table_0FF9E529FD1C43A8A3B2B0D789C8E83C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Gebruiksscenario </th> 
   <th colname="col2" class="entry"> Ondersteunde methoden </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Zaak 1</b> </p> </td> 
   <td colname="col2"> <p> 
     <ul id="ul_99FAC8608F4C4B39805EEAA6297DB771"> 
      <li id="li_B13F6C4119F44F17963794B1E2046B1F"> <span class="codeph"> getMarketingCloudID  </span> </li> 
      <li id="li_9C1B5C00A17F467CAB7EFE5F0D040777"> <span class="codeph"> getAudienceManagerLocationHint  </span> </li> 
      <li id="li_30D4608F4C3849659FCBA97D88A10F0C"> <span class="codeph"> getAudienceManagerBlob  </span> </li> 
      <li id="li_BA359596C80147EEA89CABCE83F123CA"> <span class="codeph"> getSupplementalDataID  </span> </li> 
      <li id="li_26774089B6854CD6A3216043B6EEA01B"> <span class="codeph"> getCustomerIDs  </span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Zaak 2</b> </p> </td> 
   <td colname="col2"> <p> 
     <ul id="ul_CCAD7E362E7F4DAB9D5C3E166EEE6BDD"> 
      <li id="li_1F0B006BAD044ECBA5604625DE411E84"> <span class="codeph"> getSupplementalDataID  </span> </li> 
      <li id="li_C6022223C8314B9C923202207C7472EA"> <span class="codeph"> getMarketingCloudVisitorID  </span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
