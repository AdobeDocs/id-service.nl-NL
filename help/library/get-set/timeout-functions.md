---
description: Roep deze de dienstfuncties van identiteitskaart aan om de onderbrekingsstatus voor de Dienst van de Identiteit van Experience Cloud, Analytics, of het verzoek van identiteitskaart van de Audience Manager te bepalen. Beschikbaar in VisitorAPI.js versie 1.7.0 of hoger.
keywords: ID-service
title: callTimeOut Methods
exl-id: ff3a2c5e-a0a8-4257-b538-0e4ce454b4e8
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 3%

---

# callTimeOut Methods{#calltimeout-methods}

Roep deze de dienstfuncties van identiteitskaart aan om de onderbrekingsstatus voor de Dienst van de Identiteit van Experience Cloud, Analytics, of het verzoek van identiteitskaart van de Audience Manager te bepalen. Beschikbaar in VisitorAPI.js versie 1.7.0 of hoger.

## Time-outfuncties {#section-e08228ef5f9b45c9a84139bbb763164a}

<table id="table_B3ACE584B3224D838070D32A8462EF28"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Oplossing of service </th> 
   <th colname="col2" class="entry"> Functiesyntaxis </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Experience Cloud Identity Service </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var  <span class="varname"> variableName</span> = bezoeker.MCIDCallTimedOut()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Analytics</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var  <span class="varname"> variableName</span> = bezoeker.AnalyticsIDCallTimedOut()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Audience Manager</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var  <span class="varname"> variableName</span> = bezoeker.AAMIDCallTimedOut()</span> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Functiereacties {#section-ff73aaca58b74e10a0953c49a3387160}

<table id="table_5D08A5DD6FD04F94818B0E8B790D3136"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Antwoord </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> TRUE</span> </p> </td> 
   <td colname="col2"> <p>De dienst van identiteitskaart verzond een verzoek en uit het verzoek getimede. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> FALSE</span> </p> </td> 
   <td colname="col2"> <p>De id-service heeft een aanvraag verzonden en een geslaagde reactie van de server ontvangen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> NULL</span> </p> </td> 
   <td colname="col2"> <p>De id-service heeft geen aanvraag verzonden. </p> </td> 
  </tr> 
 </tbody> 
</table>
