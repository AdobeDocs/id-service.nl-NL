---
description: Met deze functie kunt u de Experience Cloud-id van een bezoeker in verschillende domeinen delen wanneer browsers cookies van derden blokkeren. Om deze functie te gebruiken, moet u de dienst van identiteitskaart hebben uitgevoerd en de bron en bestemmingsdomeinen bezitten. Beschikbaar in VisitorAPI.js versie 1.7.0 of hoger.
keywords: ID-service
title: appendVisitorIDsTo (Cross-Domain Tracking)
exl-id: 3e4f4e2c-e658-4124-bd0e-59c63127bdde
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 1%

---

# appendVisitorIDsTo (Cross-Domain Tracking){#appendvisitoridsto-cross-domain-tracking}

Met deze functie kunt u de Experience Cloud-id van een bezoeker in verschillende domeinen delen wanneer browsers cookies van derden blokkeren. Om deze functie te gebruiken, moet u de dienst van identiteitskaart hebben uitgevoerd en de bron en bestemmingsdomeinen bezitten. Beschikbaar in VisitorAPI.js versie 1.7.0 of hoger.

Inhoud:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> Bezoekers bijhouden op verschillende domeinen wanneer browsers cookies van derden blokkeren  </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> Voorbeeld van code bezoeker-id toevoegen  </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-168e313df6054af0a7e27b9fa0d69640" format="dita" scope="local"> Dynamic Tag Management (DTM) en SDK-ondersteuning  </a> </li> 
</ul>

## Bezoekers bijhouden op verschillende domeinen wanneer browsers cookies van derden blokkeren {#section-7251d88befd440b4b79520e33c5aa44a}

De dienst van identiteitskaart schrijft een eerste en derdekoekje aan browser wanneer een persoon uw plaats bezoekt (zie [Cookies en de Dienst van de Identiteit van de Experience Cloud](../../introduction/cookies.md)). Het cookie van de eerste partij bevat de MID, een unieke id voor die bezoeker. Het cookie van de andere fabrikant bevat een andere id die door de ID-service wordt gebruikt om de id te genereren. Wanneer een browser dit cookie van derden blokkeert, kan de id-service het volgende niet:

* Regenereer de unieke id voor die sitebezoeker wanneer deze naar een ander domein navigeert.
* Bezoekers bijhouden in verschillende domeinen die eigendom zijn van uw organisatie.

Implementeer ` Visitor.appendVisitorIDsTo( *`url`*)` om dit probleem op te lossen. Met deze eigenschap kunnen bezoekers van sites in meerdere domeinen door de ID-service worden getraceerd, zelfs als hun browsers cookies van derden blokkeren. Het werkt als volgt:

* Wanneer een bezoeker naar andere domeinen bladert, voegt de ` Visitor.appendVisitorIDsTo( *`url`*)` de MID toe als een queryparameter in de URL die van het oorspronkelijke domein naar het doeldomein wordt omgeleid.
* De de dienstcode van identiteitskaart op het bestemmingsdomein haalt MID uit URL in plaats van het verzenden van een verzoek naar Adobe voor identiteitskaart van die bezoeker. Deze aanvraag bevat de cookie-id van een andere fabrikant, die in dit geval niet beschikbaar is.
* De de dienstcode van identiteitskaart op de bestemmingspagina gebruikt overgegaan MID om de bezoeker te volgen.

Zie het codevoorbeeld voor meer informatie.

## Voorbeeld van code bezoeker-id toevoegen {#section-62d55f7f986542b0b9238e483d50d7b0}

Het volgende voorbeeld kan u helpen begonnen worden met ` Visitor.appendVisitorIDsTo( *`url`*)`. Wanneer uw JavaScript-code correct is geïmplementeerd, kan deze er ongeveer als volgt uitzien.

```js
//Code on Domain A 
var destinationURL = "www.destination.com"; 
 
//Call the ID service 
var visitor = Visitor.getInstance(...); 
 
//Append visitor IDs to the destination URL 
var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(destinationURL); 
     //Result of appendVisitorIDsTo includes destination URL, Experience Cloud ID (MCMID), and Analytics ID (MCAID) 
     "www.destination.com?adobe_mc=MCMID=1234|MCAID=5678"
//Redirect to the destination
```

## Dynamic Tag Management (DTM) en SDK-ondersteuning {#section-168e313df6054af0a7e27b9fa0d69640}

<table id="table_6E7152B4FD2B4C4D8C9477C68204C4FF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Ondersteuning voor </th> 
   <th colname="col2" class="entry"> Zie </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>DTM</b> </p> </td> 
   <td colname="col2"> <p> <a href="https://helpx.adobe.com/dtm/kb/how-to-set-marketing-cloud-id-service-helper-function-in-adobe-d.html" format="https" scope="external"> De appendVisitorIDTo-functie instellen in DTM  </a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>SDK</b> </p> </td> 
   <td colname="col2"> 
    <ul id="ul_9D7933FF68EE4C71BAE999B3747F8398"> 
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/mc-methods.html" format="https" scope="external"> Servicemethoden Android  </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/mc-methods.html" format="https" scope="external"> iOS ID-servicemethoden  </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
