---
description: Deze voorbeelden hebben betrekking op twee veelvoorkomende gebruiksgevallen die verband houden met een directe integratie en de Experience Cloud-id (MID). De id is een unieke, permanente id voor bezoekers van uw site.
keywords: ID-service
title: Gebruiksscenario's voor directe integratie
exl-id: f2a55b90-8307-4242-b20a-6a3c367a251b
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# Gebruiksscenario&#39;s voor directe integratie {#direct-integration-use-cases}

Deze voorbeelden hebben betrekking op twee veelvoorkomende gebruiksgevallen die verband houden met een directe integratie en de Experience Cloud-id (ECID of MID). Deze id is een unieke, permanente id voor bezoekers van uw site.

>[!TIP]
>
>* Herzie en begrijp de [ syntaxis van de code en variabelen ](../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9) alvorens in de gebruiksgevallen te duiken.
>* Voor meer informatie over MID, zie [ Cookies en de Dienst van de Identiteit van het Experience Cloud ](../introduction/cookies.md).
>

## Hoofdlettergebruik 1: Ik heb een Experience Cloud-id (MID) maar wil mijn bezoeker-id&#39;s doorgeven en een verificatiestatus instellen {#section-a67d89a343754d1286d03cf08d34b806}

<table id="table_DA8840FCB51541109FE6DF20430E8924"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Hoofdelement gebruiken </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b> Voorwaarden </b> </p> </td> 
   <td colname="col2"> <p>Bij dit gebruiksgeval wordt ervan uitgegaan dat u: </p> 
    <ul id="ul_F20231F83EE84889B78971A64E758757"> 
     <li id="li_20F3E96493724CD2BAF4B20AEE5CBF23">Een id hebben voor de sitebezoeker. Laten we deze ID 1234 noemen. </li> 
     <li id="li_A358C58CC58C4FCBB7250F5ED108AA71">Deze bezoeker kent uw eigen unieke id. Laten we deze ID 9876 noemen. </li> 
     <li id="li_D93CE7182EBE4927A5C7A0BF414C03BC">Wilt u de MID (1234) koppelen aan uw eigen unieke id (9876). </li> 
     <li id="li_4611146E56624C2AB647733487A3F046"> <i> (Facultatief) </i> wil een authentificatiestatus op deze bezoeker plaatsen. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> Acties </b> </p> </td> 
   <td colname="col2"> <p>Gezien deze voorwaarden, maak een vraag aan de dienst van identiteitskaart die omvat: </p> 
    <ul id="ul_9ECB1A65266644E89E949C57D202D5A4"> 
     <li id="li_10A6F5A9C54D44A08F4F2E405E6019E2">MID (1234). </li> 
     <li id="li_4869572B40E54C54B88A2474DAC475A8">Uw gegevensaanbieder-id. Dit is een unieke id die aan uw bedrijf is toegewezen. Laten we deze ID 4444 noemen. </li> 
     <li id="li_05C8ED47488C4E289D84093127EC7B19">Uw id voor de bezoeker (9876). </li> 
     <li id="li_3D1556AD18C843828A362CC604A9F76B"> <i> (Facultatief) </i> identiteitskaart van A status om de authentificatiestatus voor deze bezoeker te bepalen. </li> 
    </ul> <p>En, als u toevallig om het even welke andere parameters hebt die in <a href="../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local"> worden vermeld directe integratiegids </a> (b.v., <span class="codeph"> d_blob </span> of <span class="codeph"> dcs_region </span>, enz.) het is goed om die ook binnen te laten . </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> Oplossing en codesteekproef </b> </p> </td> 
   <td colname="col2"> <p>Maak uw vraag aan de dienst van identiteitskaart als dit op: </p> <p> <span class="codeph"> https://dpm.demdex.net/id?d_mid=1234&amp;d_cid=4444%019876%011&amp;d_ver=2</span> </p> <p>Merk op hoe de steekproefvraag bevat: </p> 
    <ul id="ul_0667FBFD8D3C46BDBD027F484691EC97"> 
     <li id="li_FAB1FAE703DB48D1A32EE72684028964">MID: <span class="codeph"> d_mid=1234 </span> </li> 
     <li id="li_C97B74FF444F4BB4B4A5CB1CBBE52249">MID is gekoppeld aan uw unieke id voor de bezoeker: <span class="codeph"> d_mid=1234&amp;d_cid=444%019876%011 </span> </li> 
     <li id="li_D428DBF765234DD78DDF152C5EE8AB69">Identiteitskaart van de authentificatiestatus: <span class="codeph">...d_cid=444%019876%011 </span> (wenk: het is dat laatste cijfer). </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Gebruiksscenario 2: Ik heb geen MID en moet er een genereren {#section-8e81291f8b684de8b88fae4002ae0029}

<table id="table_666A92693F8A413096DF6A64770C1141"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Hoofdelement gebruiken </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b> Voorwaarden </b> </p> </td> 
   <td colname="col2"> <p>Bij dit gebruiksgeval wordt ervan uitgegaan dat u: </p> 
    <ul id="ul_BF3BD821907B46A4B2EFA63146D35722"> 
     <li id="li_E658AE0671D14558B65FDD8992F25996">Geen id voor de sitebezoeker. </li> 
     <li id="li_28A48BB3F71C4E4297F95A2D3E10AD7B">Moet een id aanvragen bij de id-service. </li> 
     <li id="li_E2C306B9308D41E5BFE2F23EF48F5A41">Ken uw <a href="../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26" format="dita" scope="local"> organisatie identiteitskaart </a>. Laten we deze 5555 noemen. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> Acties </b> </p> </td> 
   <td colname="col2"> <p>Gezien deze voorwaarden, doe een vraag aan de dienst van identiteitskaart die uw identiteitskaart van de Organisatie omvat. </p> <p>En, als u toevallig om het even welke andere parameters hebt die in <a href="../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local"> worden vermeld directe integratiegids </a> (b.v., <span class="codeph"> d_blob </span> of <span class="codeph"> dcs_region </span>, enz.) het is goed om die ook binnen te laten . </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> Oplossing en codesteekproef </b> </p> </td> 
   <td colname="col2"> <p>Maak uw vraag aan de dienst van identiteitskaart als dit op: </p> <p> <span class="codeph"> https://dpm.demdex.net/id?d_orgid=5555&amp;d_ver=2</span> </p> <p>Merk op hoe de steekproefvraag uw identiteitskaart van de Organisatie, <span class="codeph"> d_orgid=5555 </span> bevat. Het zou een <span class="keyword"> Experience Cloud </span> identiteitskaart voor deze bezoeker terugkeren. </p> </td> 
  </tr> 
 </tbody> 
</table>
