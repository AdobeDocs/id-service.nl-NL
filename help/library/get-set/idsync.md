---
description: Met de ID-servicefuncties idSyncByURL en idSyncByDataSource kunt u handmatig een id-synchronisatie implementeren in de iFrame voor doelpublicatie. Deze zijn beschikbaar in VisitorAPI.js versies 1.10, of hoger.
keywords: ID-service
title: ID-synchronisatie met URL of Data Source
exl-id: a22e6b47-00ff-4b51-9958-ddeccc1e507e
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 1%

---

# ID-synchronisatie met URL of Data Source{#id-synchronization-by-url-or-data-source}

Met de ID-servicefuncties idSyncByURL en idSyncByDataSource kunt u handmatig een id-synchronisatie implementeren in de iFrame voor doelpublicatie. Deze zijn beschikbaar in VisitorAPI.js versies 1.10, of hoger.

## Syntaxis, eigenschappen en macro&#39;s {#section-90ac61617482463aaf4c57009b830332}

**Syntaxis**

<table id="table_ADC7501511914805A6A6B24B2DFEBA51"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Code </th> 
   <th colname="col2" class="entry"> Gebruikersnamen synchroniseren </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> bezoeker.idSyncByURL(); </span> </p> </td> 
   <td colname="col2"> <p>Tussen verschillende gegevenspartners en <span class="keyword"> Audience Manager </span> via een aangepaste id-sync-URL. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> bezoeker.idSyncByDataSource(); </span> </p> </td> 
   <td colname="col2"> <p>Wanneer u de DPID en DPUUID al kent en deze naar <span class="keyword"> Audience Manager </span> wilt verzenden in de standaard-id-synchronisatie-URL-indeling. </p> <p></p> </td> 
  </tr> 
 </tbody> 
</table>

**Eigenschappen**

In de volgende tabel worden de eigenschappen weergegeven en gedefinieerd die voor beide functies beschikbaar zijn.

<table id="table_5343BE784E694C67B09A0A8878CF8001"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Naam </th> 
   <th colname="col2" class="entry"> Type </th> 
   <th colname="col3" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> dpid </span> </td> 
   <td colname="col2"> String </td> 
   <td colname="col3"> <p>ID gegevensaanbieder toegewezen door Audience Manager. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> dpuuid </span> </td> 
   <td colname="col2"> String </td> 
   <td colname="col3"> <p>De unieke id van de gegevensaanbieder voor de gebruiker. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> minutesToLive </span> </td> 
   <td colname="col2"> Getal </td> 
   <td colname="col3"> <p> <i> (Facultatief) </i> plaatst de koekjesvervaltijd. Moet een geheel getal zijn. De standaardwaarde is 20160 minuten (14 dagen). </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> url </span> </td> 
   <td colname="col2"> String </td> 
   <td colname="col3"> <p>Doel-URL. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Macro&#39;s**

Beide functies accepteren de volgende macro&#39;s:

* `%TIMESTAMP%`: genereert een tijdstempel (in milliseconden). Wordt gebruikt voor het busten van cache.
* `%DID%`: voegt de Audience Manager-id voor de gebruiker in.
* `%HTTP_PROTO%`: stelt het communicatieprotocol in (`http` of `https`).

## Voorbeeldcode en uitvoer {#section-0115615c37584a19a2ab11e917c4e7e9}

Beide functies retourneren `Successfully queued` als dit gelukt is. Ze retourneren een foutbericht als dat niet het geval is.

### visitor.idSyncByURL

**Code van de Steekproef**

```javascript
   //Instatiate Visitor
    var visitor = Visitor.getInstance
    ("MARKETING-CLOUD-ORG-ID-HERE",{}); 
   // Fires url with macros replaced 
    visitor.idSyncByURL({ 
    dpid: '24', // must be a string 
    url: '//su.addthis.com/red/usync?pid=16&puid=%DID%&url=%HTTP_PROTO%://
    dpm.demdex.net/ibs:dpid=420&dpuuid={{uid}}', 
    minutesToLive: 20160 // optional, defaults to 20160 minutes (14 days) });
```

**Uitvoer van de Steekproef**

```
http://su.addthis.com/red/usync?pid=16&puid=28777806459181003670799219185178493848&url=http%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D
```

### visitor.idSyncByDataSource

**Code van de Steekproef**

```javascript
  //Instantiate Visitor
   var visitor = Visitor.getInstance
   ("MARKETING-CLOUD-ORG-ID-HERE",{}); 
  // Fires 'http:/https:' + '//dpm.demdex.net/ibs:dpid=&dpuuid='
   visitor.idSyncByDataSource({ 
     dpid: '24', // must be a string
     dp     minutesToLive: 20160 // optional, defaults to 20160 minutes (14 days) });
```

**Uitvoer van de Steekproef**

```
http://dpm.demdex.net/ibs:dpid=24&dpuuid=98765
```

>[!MORELIKETHIS]
>
>* [ DIL idSync ](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-instance-methods.html?lang=nl-NL#idsync)
