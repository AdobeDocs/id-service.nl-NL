---
description: Roep deze de dienstfunctie van identiteitskaart aan om te bepalen als de dienst van identiteitskaart een cliënt-kant, Experience Cloud bezoekersidentiteitskaart (MID) produceerde. Beschikbaar in VisitorAPI.js versie 1.7.0 of hoger.
keywords: ID Service
seo-description: Roep deze de dienstfunctie van identiteitskaart aan om te bepalen als de dienst van identiteitskaart een cliënt-kant, Experience Cloud bezoekersidentiteitskaart (MID) produceerde. Beschikbaar in VisitorAPI.js versie 1.7.0 of hoger.
seo-title: isClientSideMarketingCloudVisitorID
title: isClientSideMarketingCloudVisitorID
uuid: 1c39ac60-1d2b-4ed4-a2ea-30d680e61e10
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 3%

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
   <td colname="col2"> <p>De id-service kan geen id van de <span class="keyword"> Experience Cloud</span> -server ontvangen of heeft deze niet ontvangen. Het leidde tot lokale MID, in browser (cliënt-kant). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> false</span> </p> </td> 
   <td colname="col2"> <p>De id-service heeft een id ontvangen van de <span class="keyword"> Experience Cloud</span> -server. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> null</span> </p> </td> 
   <td colname="col2"> <p>De dienst van identiteitskaart deed geen vraag aan de server van <span class="keyword"> Experience Cloud</span> . </p> </td> 
  </tr> 
 </tbody> 
</table>

