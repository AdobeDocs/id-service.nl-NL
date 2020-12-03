---
description: Dit is een asynchrone API die herkenningstekens voor Analytics, de dienst van identiteitskaart, de optieoptie van de gegevensinzameling, geografische plaats, en meta-gegevens "blob"inhoud door gebrek terugkeert. U kunt ook bepalen welke id's u wilt retourneren met de optionele bezoeker.FIELDS-enum.
keywords: ID Service
seo-description: Dit is een asynchrone API die herkenningstekens voor Analytics, de dienst van identiteitskaart, de optieoptie van de gegevensinzameling, geografische plaats, en meta-gegevens "blob"inhoud door gebrek terugkeert. U kunt ook bepalen welke id's u wilt retourneren met de optionele bezoeker.FIELDS-enum.
seo-title: getVisitorValues
title: getVisitorValues
uuid: 7fb831b3-cf7e-40e2-a219-07fec28ad49c
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---


# getVisitorValues{#getvisitorvalues}

Dit is een asynchrone API die herkenningstekens voor Analytics, de dienst van identiteitskaart, de optieoptie van de gegevensinzameling, geografische plaats, en meta-gegevens &quot;blob&quot;inhoud door gebrek terugkeert. U kunt ook bepalen welke id&#39;s u wilt retourneren met de optionele bezoeker.FIELDS-enum.

Inhoud:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-5aebe3907b2b46e997f45a1d1ed35c09" format="dita" scope="local"> Syntaxis </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-36a31683558742a5915db3a391e09f7b" format="dita" scope="local"> Hoofdlettergebruik 1: De standaardgegevensset aanvragen </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-467b2f4e513344c89b7332b05f6f59f3" format="dita" scope="local"> Hoofdlettergebruik 2: Een aangepaste gegevensset aanvragen </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5" format="dita" scope="local"> Responsparameters gedefinieerd </a> </li> 
</ul>

## Syntaxis {#section-5aebe3907b2b46e997f45a1d1ed35c09}

Deze functie gebruikt de volgende syntaxis (cursief staat voor een tijdelijke aanduiding voor een variabele): ` var *``* = visitor.getVisitorValues (callback, [visitor.FIELDS. *`valuesID`*, visitor.FIELDS. *`typeID type`*]);`

In de functieparameters:

* ` *`callback`*` vertegenwoordigt uw eigen callback code die teruggekeerde IDs ontvangt.
* *(Optioneel)* Het ` visitor.FIELDS. *`id-type`*` is een opsomming waarmee u kunt opgeven welke [id-waarden](../../library/get-set/getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5) deze functie moet retourneren.

Zie de volgende gebruiksgevallen en definities voor meer informatie.

## Hoofdlettergebruik 1: De standaardgegevensset aanvragen {#section-36a31683558742a5915db3a391e09f7b}

Deze code retourneert de standaardgegevensset. Uw verzoek en antwoord kunnen er ongeveer als volgt uitzien.

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{...}); 
   
//Add your callback to the GET method to return IDs and data. 
visitor.getVisitorValues(visitorIdsCallback);
```

In de standaardvoorbeeldreactie zijn sommige waarden voor demonstratiedoeleinden ingekort.

```js
//Formatted IDs in JSON response 
{ 
    MCMID: 'mid-1234', 
    MCOPTOUT: 'isoptedout-true', 
    MCAID: 'aid-1234', 
    MCAAMLH: 7, 
    MCAAMB: 'hgfe54236786oygj' 
}
```

## Hoofdlettergebruik 2: Een aangepaste gegevensset aanvragen {#section-467b2f4e513344c89b7332b05f6f59f3}

Deze code gebruikt een optionele array om een specifieke set id&#39;s te retourneren met behulp van de `visitor.FIELDS` enum. In dit geval willen we alleen de Experience Cloud-id (MCID) en de Analytics ID (MCAID) van de bezoeker. Uw verzoek en antwoord kunnen er ongeveer als volgt uitzien.

```js
//Call the ID service 
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here", { ... });

// Add an optional array to specify which IDs you want to return. 
visitor.getVisitorValues(visitorIdsCallback, [visitor.FIELDS.MCMID, visitor.FIELDS.MCAID]);
```

De aangepaste voorbeeldreactie retourneert alleen de id&#39;s die in de aanvraag zijn opgegeven.

```js
//Formatted IDs in JSON response 
{ 
    MCMID: 'mid-1234', 
    MCAID: 'aid-4321' 
}
```

## Responsparameters gedefinieerd {#section-4c4c300167694c6fbff1d6c612f372b5}

In de volgende tabel worden de responsparameters weergegeven en gedefinieerd. Dit zijn ook alle waarden in de `visitor.FIELDS` opsomming. Nota, keert deze methode en leeg koord terug als er geen waarden voor een bepaalde variabele zijn.

<table id="table_32D0FEEA76CE4F298EED4B8F5C644232"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Waarde </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAAMB </span> </p> </td> 
   <td colname="col2"> <p>De gecodeerde metagegevens van de <span class="keyword"> Audience Manager worden </span> de blob genoemd. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAAMLH </span> </p> </td> 
   <td colname="col2"> <p>The data collection region ID. Dit is een numerieke id voor de geografische locatie van een bepaald datacenter van de ID-service. </p> <p>Zie <a href="https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html" format="https" scope="external"> ID's van DCS-regio's, Locaties en hostnamen </a> en <a href="../../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c" format="dita" scope="local"> getLocationHint </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAID </span> </p> </td> 
   <td colname="col2"> <p>De <span class="keyword"> Analytics- </span> id van de bezoeker. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCMID </span> </p> </td> 
   <td colname="col2"> <p>De Experience Cloud-id van de bezoeker. </p> <p>See <a href="../../introduction/cookies.md" format="dita" scope="local"> Cookies and the Experience Cloud Identity Service </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCOPTOUT </span> </p> </td> 
   <td colname="col2"> <p>Een markering die aangeeft of een bezoeker zich heeft teruggetrokken uit de gegevensverzameling. </p> <p>Waarden zijn: </p> <p> 
     <ul id="ul_E82431DE12B449F8822499364B363798"> 
      <li id="li_2BAB7C15A38A408E8FC4B85E70B66E46"> <span class="codeph"> 'isoptedout-true' </span>: Een bezoeker heeft ervoor gekozen geen gegevens meer te verzamelen. </li> 
      <li id="li_BB80AE4CEBC44166BC04428B212FEF51"> <span class="codeph"> 'isoptedout-false' </span>: Een bezoeker heeft de gegevensverzameling niet verlaten. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

