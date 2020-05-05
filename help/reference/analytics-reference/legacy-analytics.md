---
description: Een overzicht van hoe de Experience Cloud Identity Service werkt met de verouderde Analytics ID.
keywords: ID Service
seo-description: Een overzicht van hoe de Experience Cloud Identity Service werkt met de verouderde Analytics ID.
seo-title: Verzoeken voor Analyses en Experience Cloud ID
title: Verzoeken voor Analyses en Experience Cloud ID
uuid: 28beed16-7ef9-4824-8e82-853930756eca
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Verzoeken voor Analyses en Experience Cloud ID{#analytics-and-experience-cloud-id-requests}

Een overzicht van hoe de Experience Cloud Identity Service werkt met de verouderde Analytics ID.

## Samenvatting {#section-64d8523ff7634cb987d0c6480f587dd3}

De Experience Cloud Identity Service is altijd nauw geïntegreerd in Adobe Analytics. Het blijft een integraal onderdeel van Analytics, maar vervult nu belangrijke functies voor andere oplossingen en functies in het [!DNL Experience Cloud]programma. Vanwege deze historische nalatenschap werkt het controleren op of schrijven van een Analytics-id iets anders dan met het algemene proces dat wordt beschreven in [How the Experience Cloud Identity Service Requests and Sets IDs...](../../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a). Zie Analytics en Experience Cloud ID&#39;s [instellen voor meer informatie over de volgorde van bewerkingen voor het controleren van id&#39;s](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6).

## De AMCV-cookie is niet ingesteld in de browser {#section-cccf10cd775e4a95a7e98d3c3c0ff9a9}

Als de cookie [!DNL Experience Cloud] (AMCV) niet aanwezig is, dan genereert een aanroep van een id-service aan [!DNL Adobe] een reactie die varieert afhankelijk van de aanwezigheid of afwezigheid van een oudere Analytics-id. De oudere [!DNL Analytics]-id wordt opgeslagen in de cookie [s_vi](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-analytics.html). In de onderstaande tabel wordt beschreven hoe id&#39;s naar de cookie AMCV worden geschreven op basis van de status van de cookie s_vi.

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
   <td colname="col2"> <p>De id-service wijst bezoekers een <span class="keyword"> Experience Cloud</span> ID (MID) toe. Het MID identificeert uw bezoekers voor <span class="keyword"> Analytics</span> en andere oplossingen van de <span class="keyword"> Ervaring Cloud</span> . </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>s_vi cookie is ingesteld</b> </p> </td> 
   <td colname="col2"> <p>Wanneer een bezoeker van een site met een s_vi-cookie eerst de Experience Cloud Identity Service aantreft, geldt deze service: </p> 
    <ul id="ul_BE584810280D4874AF802A9247011787"> 
     <li id="li_AA395B09A3174AF78F3EC10053E2E4F5">Schrijft de <span class="keyword"> Analytics</span> -id die in het s_vi-cookie is opgeslagen naar het AMCV-cookie. Dit wordt geschreven als <span class="keyword"> Analytics</span> ID (AID). Deze actie heeft <i>geen</i> invloed op het aantal bezoekers. <span class="keyword"> Analytics</span> zal gebruikers met hun erfenis IDs blijven identificeren. </li> 
     <li id="li_8735DE21FEA542BA8024109B8FE1E2ED">Schrijft de id naar het AMCV-cookie. Het MID identificeert gebruikers over verschillende oplossingen. </li> 
    </ul> <p> <p>Opmerking: Met een <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> respijtperiode</a>bevat de respons van het datacenter altijd een oudere id die is opgeslagen in het s_vi-cookie. Tijdens de evaluatieperiode wordt de oudere id naar het AMCV-cookie geschreven als de HULP-waarde. </p> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Gebruikers die door het s_fid-cookie worden geïdentificeerd, krijgen hun oudere FID-waarde niet gemigreerd naar het AMCV-cookie. Met een s_fid-cookie worden gebruikers gemigreerd alsof er geen s_vi-cookie aanwezig is (zie boven) en worden ze weergegeven als nieuwe bezoekers van uw site. Zie [Analytics Cookies](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-analytics.html) voor meer informatie.

## De AMCV-cookie wordt ingesteld in de browser {#section-01c088fc565c4b24ba1722c7cc240310}

Als het AMCV-cookie aanwezig is, gebruikt Analytics de MID als de [!DNL Analytics] -id als er geen oudere [!DNL Analytics] id-waarde in het cookie staat.
