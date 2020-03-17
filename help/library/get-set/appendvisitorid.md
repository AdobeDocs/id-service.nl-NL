---
description: Met deze functie kunt u de Experience Cloud-id van een bezoeker delen over verschillende domeinen wanneer browsers cookies van derden blokkeren. Om deze functie te gebruiken, moet u de dienst van identiteitskaart hebben uitgevoerd en de bron en bestemmingsdomeinen bezitten. Beschikbaar in VisitorAPI.js versie 1.7.0 of hoger.
keywords: ID Service
seo-description: Met deze functie kunt u de Experience Cloud-id van een bezoeker delen over verschillende domeinen wanneer browsers cookies van derden blokkeren. Om deze functie te gebruiken, moet u de dienst van identiteitskaart hebben uitgevoerd en de bron en bestemmingsdomeinen bezitten. Beschikbaar in VisitorAPI.js versie 1.7.0 of hoger.
seo-title: appendVisitorIDsTo (Cross-Domain Tracking)
title: appendVisitorIDsTo (Cross-Domain Tracking)
uuid: 06b453ee-73c5-4625-82d9-877ad2b4f702
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# appendVisitorIDsTo (Cross-Domain Tracking){#appendvisitoridsto-cross-domain-tracking}

Met deze functie kunt u de Experience Cloud-id van een bezoeker delen over verschillende domeinen wanneer browsers cookies van derden blokkeren. Om deze functie te gebruiken, moet u de dienst van identiteitskaart hebben uitgevoerd en de bron en bestemmingsdomeinen bezitten. Beschikbaar in VisitorAPI.js versie 1.7.0 of hoger.

Inhoud:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> Bezoekers bijhouden op verschillende domeinen wanneer browsers cookies van derden blokkeren </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> Voorbeeld van code bezoeker-id toevoegen </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-168e313df6054af0a7e27b9fa0d69640" format="dita" scope="local"> Dynamic Tag Management (DTM) en SDK-ondersteuning </a> </li> 
</ul>

## Bezoekers bijhouden op verschillende domeinen wanneer browsers cookies van derden blokkeren {#section-7251d88befd440b4b79520e33c5aa44a}

De id-service schrijft een cookie van de eerste en de andere leverancier naar de browser wanneer een persoon uw site bezoekt (zie [Cookies en de Experience Cloud Identity Service](../../introduction/cookies.md) ). Het cookie van de eerste partij bevat de MID, een unieke id voor die bezoeker. Het cookie van de andere fabrikant bevat een andere id die door de ID-service wordt gebruikt om de id te genereren. Wanneer een browser dit cookie van derden blokkeert, kan de id-service het volgende niet:

* Regenereer de unieke id voor die sitebezoeker wanneer deze naar een ander domein navigeert.
* Bezoekers bijhouden in verschillende domeinen die eigendom zijn van uw organisatie.

Implementeer ` Visitor.appendVisitorIDsTo( *`URL om dit probleem op te lossen`*)`. Met deze eigenschap kunnen bezoekers van sites in meerdere domeinen door de ID-service worden getraceerd, zelfs als hun browsers cookies van derden blokkeren. Het werkt als volgt:

* Wanneer een bezoeker naar andere domeinen bladert, voegt de ` Visitor.appendVisitorIDsTo( *`URL`*)` de MID toe als een queryparameter in de URL die van het oorspronkelijke domein naar het doeldomein wordt omgeleid.
* De ID-servicecode op het doeldomein extraheert de MID uit de URL in plaats van een aanvraag naar Adobe voor de id van die bezoeker te verzenden. Deze aanvraag bevat de cookie-id van een andere fabrikant, die in dit geval niet beschikbaar is.
* De de dienstcode van identiteitskaart op de bestemmingspagina gebruikt overgegaan MID om de bezoeker te volgen.

Zie het codevoorbeeld voor meer informatie.

## Voorbeeld van code bezoeker-id toevoegen {#section-62d55f7f986542b0b9238e483d50d7b0}

In het volgende voorbeeld kunt u aan de slag met ` Visitor.appendVisitorIDsTo( *`url`*)`. Wanneer uw JavaScript-code correct is geïmplementeerd, kan deze er ongeveer als volgt uitzien.

```js
//Code on Domain A 
var destinationURL = "www.destination.com"; 
 
//Call the ID service 
var visitor = Visitor.getInstance(...); 
 
//Append visitor IDs to the destination URL 
var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(destinationURL); 
     //Result of appendVisitorIDsTo includes destination URL, Experience Cloud ID (MCMID), and Analytics ID (MCAID) 
     "www.destination.com?adobe_mc=MCMID=1234|MCAID=5678 
<draft-comment>
  |TS=123675879 
</draft-comment>" 
 
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
   <td colname="col2"> <p> <a href="https://helpx.adobe.com/dtm/kb/how-to-set-marketing-cloud-id-service-helper-function-in-adobe-d.html" format="https" scope="external"> De appendVisitorIDTo-functie instellen in DTM </a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>SDK</b> </p> </td> 
   <td colname="col2"> 
    <ul id="ul_9D7933FF68EE4C71BAE999B3747F8398"> 
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://marketing.adobe.com/resources/help/en_US/mobile/android/mc_methods.html" format="https" scope="external"> Servicemethoden Android </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://marketing.adobe.com/resources/help/en_US/mobile/ios/mc_methods.html" format="https" scope="external"> iOS ID-servicemethoden </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

