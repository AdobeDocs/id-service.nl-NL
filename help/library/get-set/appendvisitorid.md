---
description: Met deze functie kunt u de Experience Cloud-id van een bezoeker in verschillende domeinen delen wanneer browsers cookies van derden blokkeren. Om deze functie te gebruiken, moet u de dienst van identiteitskaart hebben uitgevoerd en de bron en bestemmingsdomeinen bezitten. Beschikbaar in VisitorAPI.js versie 1.7.0 of hoger.
keywords: ID-service
title: appendVisitorIDsTo (Cross-Domain Tracking)
exl-id: 3e4f4e2c-e658-4124-bd0e-59c63127bdde
source-git-commit: c035f0af76f70322e4d79ed842502b26c3f155ac
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# appendVisitorIDsTo (Cross-Domain Tracking){#appendvisitoridsto-cross-domain-tracking}

Met deze functie kunt u de Experience Cloud-id van een bezoeker in verschillende domeinen delen wanneer browsers cookies van derden blokkeren. Om deze functie te gebruiken, moet u de dienst van identiteitskaart hebben uitgevoerd en de bron en bestemmingsdomeinen bezitten. Beschikbaar in VisitorAPI.js versie 1.7.0 of hoger.

Inhoud:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> Bezoekers bijhouden op verschillende domeinen wanneer browsers cookies van derden blokkeren </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> Voorbeeld van code bezoeker-id toevoegen </a> </li> 
 </a> </li> 
</ul>

<!-- <li> <a href="../../library/get-set/appendvisitorid.md#section-168e313df6054af0a7e27b9fa0d69640" format="dita" scope="local"> Dynamic Tag Management (DTM) and SDK Support -->

## Bezoekers bijhouden op verschillende domeinen wanneer browsers cookies van derden blokkeren {#section-7251d88befd440b4b79520e33c5aa44a}

De dienst van identiteitskaart schrijft een eerste en derdekoekje aan browser wanneer een persoon uw plaats (zie [ Cookies en de Dienst van de Identiteit van het Experience Cloud ](../../introduction/cookies.md)) bezoekt. Het cookie van de eerste partij bevat de MID, een unieke id voor die bezoeker. Het cookie van de andere fabrikant bevat een andere id die door de ID-service wordt gebruikt om de id te genereren. Wanneer een browser dit cookie van derden blokkeert, kan de id-service het volgende niet:

* Regenereer de unieke id voor die sitebezoeker wanneer deze naar een ander domein navigeert.
* Bezoekers bijhouden in verschillende domeinen die eigendom zijn van uw organisatie.

Om dit probleem op te lossen, voer ` Visitor.appendVisitorIDsTo( *` url `*)` uit. Met deze eigenschap kunnen bezoekers van sites in meerdere domeinen door de ID-service worden getraceerd, zelfs als hun browsers cookies van derden blokkeren. Het werkt als volgt:

* Aangezien een bezoeker aan uw andere domeinen doorbladert, voegt ` Visitor.appendVisitorIDsTo( *` url `*)` MID als vraagparameter in URL toe die van het originele domein aan het bestemmingsdomein opnieuw richt.
* De de dienstcode van identiteitskaart op het bestemmingsdomein haalt MID uit URL in plaats van het verzenden van een verzoek naar Adobe voor identiteitskaart van die bezoeker. Deze aanvraag bevat de cookie-id van een andere fabrikant, die in dit geval niet beschikbaar is.
* De de dienstcode van identiteitskaart op de bestemmingspagina gebruikt overgegaan MID om de bezoeker te volgen.

Zie het codevoorbeeld voor meer informatie.

## Voorbeeld van code bezoeker-id toevoegen {#section-62d55f7f986542b0b9238e483d50d7b0}

Met de volgende voorbeeldcode kunt u aan de slag met de functie `appendVisitorIDsTo` :

>[!TIP]
>
>Deze code kan in de redacteur van de Code van de Douane worden geplaatst die deel van de uitbreiding van Adobe Analytics of bij de bovenkant van [ AppMeasurement.js ](https://experienceleague.adobe.com/docs/analytics/implementation/js/overview.html) uitmaakt.

```js
var adbeDomains = ["marketo.com", "figma.com", "workfront.com"];
var visitor = Visitor.getInstance("9E1005A551ED61CA0A490D45@AdobeOrg", {
  trackingServer: "sstats.adobe.com",
  trackingServerSecure: "sstats.adobe.com",
  marketingCloudServer: "sstats.adobe.com",
  marketingCloudServerSecure: "sstats.adobe.com"
});
adbeDomains.forEach(function(domain) {
  var domainRegex = RegExp(domain);
  if (!domainRegex.test(location.hostname)) {
    hrefSelector = '[href*="' + domain + '"]';
    document.querySelectorAll(hrefSelector).forEach(function(href) {
      href.addEventListener('mousedown', function(event) {
        var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(event.currentTarget.href)
        event.currentTarget.href = destinationURLWithVisitorIDs.replace(/MCAID%3D.*%7CMCORGID/, 'MCAID%3D%7CMCORGID');
      });
    });
  }
});
```

<!-- >[!IMPORTANT]
>
>In order for the values passed in the URL via appendVisitorsIDsTo to be picked up, the [ovewriteCrossDomainMCIDAndAID](../function-vars/overwrite-visitor-id.md) variable must be set to true.

The following example can help you get started with ` Visitor.appendVisitorIDsTo( *`url`*)`. When implemented properly, your JavaScript code could look similar to the following example.

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
``` -->

<!-- ## Dynamic Tag Management (DTM) and SDK Support {#section-168e313df6054af0a7e27b9fa0d69640}

<table id="table_6E7152B4FD2B4C4D8C9477C68204C4FF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Support for </th> 
   <th colname="col2" class="entry"> See </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>DTM</b> </p> </td> 
   <td colname="col2"> <p> <a href="https://helpx.adobe.com/dtm/kb/how-to-set-marketing-cloud-id-service-helper-function-in-adobe-d.html" format="https" scope="external"> Set the appendVisitorIDTo Function in DTM </a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>SDK</b> </p> </td> 
   <td colname="col2"> 
    <ul id="ul_9D7933FF68EE4C71BAE999B3747F8398"> 
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/mc-methods.html" format="https" scope="external"> Android ID Service Methods </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/mc-methods.html" format="https" scope="external"> iOS ID Service Methods </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table> -->
