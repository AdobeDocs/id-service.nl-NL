---
description: Een overzicht van hoe de dienst van de Identiteit van de Experience Cloud met erfenisAnalytics ID werkt.
keywords: ID-service
title: Analyses en Experience Cloud-id-verzoeken
exl-id: 8c682159-e23a-4641-9ffd-e0028dc2f305
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 13%

---

# Analyses en Experience Cloud-id-verzoeken{#analytics-and-experience-cloud-id-requests}

Een overzicht van hoe de dienst van de Identiteit van de Experience Cloud met erfenisAnalytics ID werkt.

## Samenvatting {#section-64d8523ff7634cb987d0c6480f587dd3}

Historisch gezien is de Experience Cloud Identity Service nauw geïntegreerd in Adobe Analytics. Het blijft een integraal onderdeel van Analytics, maar vervult nu belangrijke functies voor andere oplossingen en functies in de [!DNL Experience Cloud]. Vanwege deze historische nalatenschap werkt het controleren op of schrijven van een Analytics ID iets anders dan bij het algemene proces dat in [Hoe de Dienst van de Identiteit van de Experience Cloud verzoekt en plaatst IDs...](../../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a). Voor meer informatie over de volgorde van bewerkingen voor het controleren van id&#39;s raadpleegt u [Analyse- en Experience Cloud-id&#39;s instellen](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6).

## De AMCV-cookie is niet ingesteld in de browser {#section-cccf10cd775e4a95a7e98d3c3c0ff9a9}

Als de cookie [!DNL Experience Cloud] (AMCV) niet aanwezig is, dan genereert een aanroep van een id-service aan [!DNL Adobe] een reactie die varieert afhankelijk van de aanwezigheid of afwezigheid van een oudere Analytics-id. De oudere [!DNL Analytics]-id wordt opgeslagen in de cookie [s_vi](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html). In de onderstaande tabel wordt beschreven hoe id&#39;s naar de cookie AMCV worden geschreven op basis van de status van de cookie s_vi.

<table id="table_DC85FECE26DD424E841BA1059AF1E57F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> s_vi Cookie-status </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b> s_vi cookie niet ingesteld</b> </p> </td> 
   <td colname="col2"> <p>De id-service wijst bezoekers een <span class="keyword"> Experience Cloud</span> ID (MID). De id identificeert uw bezoekers aan <span class="keyword"> Analyse</span> en andere <span class="keyword"> Experience Cloud</span> oplossingen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>s_vi cookie is ingesteld</b> </p> </td> 
   <td colname="col2"> <p>Wanneer een bezoeker van een site met een s_vi cookie de Experience Cloud Identity Service voor het eerst aantreft, geldt deze service: </p> 
    <ul id="ul_BE584810280D4874AF802A9247011787"> 
     <li id="li_AA395B09A3174AF78F3EC10053E2E4F5">Schrijft de <span class="keyword"> Analyse</span> Id opgeslagen in het s_vi cookie naar het AMCV cookie. Dit is geschreven als de <span class="keyword"> Analyse</span> ID (HULP). Deze handeling <i>niet</i> heeft invloed op het aantal bezoekers. <span class="keyword"> Analyse</span> gebruikers blijven identificeren met hun oude id's. </li> 
     <li id="li_8735DE21FEA542BA8024109B8FE1E2ED">Schrijft de id naar het AMCV-cookie. Het MID identificeert gebruikers over verschillende oplossingen. </li> 
    </ul> <p> <p>Opmerking: Met een <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> respijtperiode</a>, bevat de reactie van het datacenter altijd een oudere id die is opgeslagen in het s_vi-cookie. Tijdens de evaluatieperiode wordt de oudere id naar het AMCV-cookie geschreven als de HULP-waarde. </p> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Gebruikers die door het s_fid-cookie worden geïdentificeerd, krijgen hun oudere FID-waarde niet gemigreerd naar het AMCV-cookie. Met een s_fid-cookie worden gebruikers gemigreerd alsof er geen s_vi-cookie aanwezig is (zie boven) en worden ze weergegeven als nieuwe bezoekers van uw site. Zie [Analysecookies](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html) voor meer informatie .

## De AMCV-cookie wordt ingesteld in de browser {#section-01c088fc565c4b24ba1722c7cc240310}

Als het AMCV-cookie aanwezig is, gebruikt Analytics de MID als de [!DNL Analytics] id if there is no legacy [!DNL Analytics] ID-waarde in het cookie.
