---
description: Deze eigenschap overschrijft de Experience Cloud- en analytische id's van een bezoeker wanneer deze van het ene domein naar het andere navigeren. Als u een id wilt overschrijven, moet u eigenaar zijn van de id-service en deze service op elk domein hebben geïmplementeerd. Met deze code kunt u geen id's overschrijven in domeinen die u niet beheert.
keywords: ID-service
title: overwriteCrossDomainMCIDAndAID
exl-id: 726261b1-c8d0-4b12-b0cb-52d7e21e7fac
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 1%

---

# overwriteCrossDomainMCIDAndAID{#overwritecrossdomainmcidandaid}

Deze eigenschap overschrijft de Experience Cloud- en analytische id&#39;s van een bezoeker wanneer deze van het ene domein naar het andere navigeren. Als u een id wilt overschrijven, moet u eigenaar zijn van de id-service en deze service op elk domein hebben geïmplementeerd. Met deze code kunt u geen id&#39;s overschrijven in domeinen die u niet beheert.

**Syntaxis:** `Visitor.overwriteCrossDomainMCIDAndAID: true|false` (standaardwaarde is  `false`)

**Codevoorbeeld**

Uw JavaScript-code kan er ongeveer als volgt uitzien.

```js
//Call the ID service 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE", { 
     ... 
 
     //Set overwrite property 
     overwriteCrossDomainMCIDAndAID: true 
}); 
```

**Gevallen gebruiken**

Als u sitebezoekers wilt bijhouden, schrijft de id-service een [!DNL Experience Cloud]-id (of MID) naar een browsercookie. De volgende lijst maakt een lijst en beschrijft de gemeenschappelijke gebruiksgevallen waar u een bestaand MID zou kunnen willen overschrijven die door de dienst van identiteitskaart in een ander domein wordt geplaatst.

<table id="table_FC1AF6551D6646E0BF1C4FB7C1316EBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Gebruiksscenario </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Ontvangers op verschillende bestemmingspagina's van domeinen identificeren</b> </p> </td> 
   <td colname="col2"> <p>Laten we zeggen dat je de Domeinen A en B hebt. In dit geval kunt u <span class="codeph"> Visitor.overwriteCrossDomainMCIDAndAID instellen: true </span> wanneer: </p> <p> 
     <ul id="ul_FB4704BFE7134F1688E34BF1A36627B7"> 
      <li id="li_FF71FD1FB9DD4702B675A140FAD2B481">Elk domein heeft een eigen landingspagina. </li> 
      <li id="li_78F75469D32D473B93148B46D35E67F1">Een bezoeker heeft al een cookie (en een MID) ingesteld van een vorig bezoek aan Domein B. </li> 
      <li id="li_305CE5138EEB43D3BF9CE38D1E7FFA04">U wilt een bezoeker constant identificeren als zij bij Domein B van Domein A komen. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Bezoekers identificeren op doorlopende en conversiepagina's</b> </p> </td> 
   <td colname="col2"> <p>Laten we zeggen dat je de Domeinen A en B hebt. In dit geval kunt u <span class="codeph"> Visitor.overwriteCrossDomainMCIDAndAID instellen: true </span> wanneer: </p> 
    <ul id="ul_7BEBFD523A2F47AFB6963536E43692D0"> 
     <li id="li_71586080489340E2A6C0B263F231E3DE">Domein A is een openingspagina. </li> 
     <li id="li_4E3D3CB380EE4F1BAC4CD752194AE8DE">Domein B is een afzonderlijke conversie-, boekings- of andere end-of-workflow-pagina. </li> 
     <li id="li_FB393B16CFAC4D2D9B2328EBA4573C1A">Een bezoeker heeft reeds een koekje (en een MID) die van een vorig bezoek aan Domein B wordt geplaatst en u weet deze minder wenselijke cliënt-kant MIDs eerder dan server-kant MIDs zijn. </li> 
     <li id="li_36FC138530A4476A995C0F9FD73C41DE">U wilt een bezoeker constant identificeren als zij bij Domein B van Domein A komen. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Bezoekers van mobiele apps naar webbrowsers identificeren</b> </p> </td> 
   <td colname="col2"> <p>Dit gebruik is iets anders. Hierbij moeten gebruikers worden geïdentificeerd wanneer zij van een mobiele app naar uw website gaan. In dit geval heeft uw bezoeker al een id lokaal ingesteld door een mobiele app en is er een andere id ingesteld in een cookie op uw website. U kunt <span class="codeph"> Visitor.overwriteCrossDomainMCIDAndAID instellen: true </span> om de in het browsercookie ingestelde MID te overschrijven met de MID die door de mobiele app is ingesteld. </p> </td> 
  </tr> 
 </tbody> 
</table>
