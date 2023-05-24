---
description: Roep deze de dienstfunctie van identiteitskaart aan om te bepalen als de dienst van identiteitskaart een cliënt-kant, Experience Cloud bezoekersidentiteitskaart (MID) produceerde. Beschikbaar in VisitorAPI.js versie 1.7.0 of hoger.
keywords: ID-service
title: isClientSideMarketingCloudVisitorID
exl-id: ed2672e7-da1a-4c02-9f4e-c14419ec9ec7
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 4%

---

# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}

Roep deze de dienstfunctie van identiteitskaart aan om te bepalen als de dienst van identiteitskaart een cliënt-kant, Experience Cloud bezoekersidentiteitskaart (MID) produceerde. Beschikbaar in VisitorAPI.js versie 1.7.0 of hoger.

**Syntaxis**

`var *`variableName`* = visitor.isClientSideMarketingCloudVisitorID()`

De volgende tabel bevat een overzicht en beschrijving van de reacties die door deze functie worden geretourneerd.

<table id="table_5D08A5DD6FD04F94818B0E8B790D3136"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Antwoord </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> true</span> </p> </td> 
   <td colname="col2"> <p>De id-service kan geen id van de <span class="keyword"> Experience Cloud</span> server. Het leidde tot lokale MID, in browser (cliënt-kant). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> false</span> </p> </td> 
   <td colname="col2"> <p>De dienst van identiteitskaart ontving een MID van <span class="keyword"> Experience Cloud</span> server. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> null</span> </p> </td> 
   <td colname="col2"> <p>De dienst van identiteitskaart deed geen vraag aan <span class="keyword"> Experience Cloud</span> server. </p> </td> 
  </tr> 
 </tbody> 
</table>
