---
description: Met de ID-servicefuncties idSyncByURL en idSyncByDataSource kunt u handmatig een id-synchronisatie implementeren in de iFrame voor doelpublicatie. Deze zijn beschikbaar in VisitorAPI.js versies 1.10, of hoger.
keywords: ID Service
seo-description: Met de ID-servicefuncties idSyncByURL en idSyncByDataSource kunt u handmatig een id-synchronisatie implementeren in de iFrame voor doelpublicatie. Deze zijn beschikbaar in VisitorAPI.js versies 1.10, of hoger.
seo-title: Id-synchronisatie op URL of databron
title: Id-synchronisatie op URL of databron
uuid: ff83d910-8375-4295-9f2a-e14c15eee09a
translation-type: tm+mt
source-git-commit: c4c0b791230422f17292b72fd45ba5689a60adae

---


# Id-synchronisatie op URL of databron{#id-synchronization-by-url-or-data-source}

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
   <td colname="col2"> <p>Tussen verschillende gegevenspartners en de Manager van het <span class="keyword"> Publiek </span> door een de synchronisatie URL van identiteitskaart te gebruiken. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> bezoeker.idSyncByDataSource(); </span> </p> </td> 
   <td colname="col2"> <p>Als u de DPID en DPUUID al kent en u deze naar <span class="keyword"> Audience Manager wilt verzenden </span> in de standaard-id-sync-URL-indeling. </p> <p> 
     <draft-comment>
       Wanneer u de gebruikersnaam al kent en wilt verzenden naar Audience Manager. 
     </draft-comment> </p> </td> 
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
   <td colname="col3"> <p>Id van gegevensaanbieder die is toegewezen door Audience Manager. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> dpuuid </span> </td> 
   <td colname="col2"> String </td> 
   <td colname="col3"> <p>De unieke id van de gegevensaanbieder voor de gebruiker. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> minutesToLive </span> </td> 
   <td colname="col2"> Getal </td> 
   <td colname="col3"> <p> <i>(Optioneel)</i> Hiermee stelt u de vervaltijd van het cookie in. Moet een geheel getal zijn. De standaardwaarde is 20160 minuten (14 dagen). </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> url </span> </td> 
   <td colname="col2"> String </td> 
   <td colname="col3"> <p>Doel-URL. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Macros**

Beide functies accepteren de volgende macro&#39;s:

* `%TIMESTAMP%`: Genereert een tijdstempel (in milliseconden). Wordt gebruikt voor het busten van cache.
* `%DID%`: Voegt de Manager-id voor het publiek in voor de gebruiker.
* `%HTTP_PROTO%`: Hiermee stelt u het communicatieprotocol (`http` of `https`) in.

## Voorbeeldcode en uitvoer {#section-0115615c37584a19a2ab11e917c4e7e9}

Beide functies worden geretourneerd `Successfully queued` als dit lukt. Ze retourneren een foutbericht als dat niet het geval is.

### bezoeker.idSyncByURL

**Voorbeeldcode**

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

**Voorbeelduitvoer**

```
http://su.addthis.com/red/usync?pid=16&puid=28777806459181003670799219185178493848&url=http%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D
```

### bezoeker.idSyncByDataSource

**Voorbeeldcode**

```javascript
  //Instantiate Visitor
   var visitor = Visitor.getInstance
   ("MARKETING-CLOUD-ORG-ID-HERE",{}); 
  // Fires 'http:/https:' + '//dpm.demdex.net/ibs:dpid=&dpuuid='
   visitor.idSyncByDataSource({ 
     dpid: '24', // must be a string
     dpuuid: '98765', // must be a string 
     minutesToLive: 20160 // optional, defaults to 20160 minutes (14 days) });
```

**Voorbeelduitvoer**

```
http://dpm.demdex.net/ibs:dpid=24&dpuuid=98765
```

>[!MORELIKETHIS]
>
>* [DIL idSync](https://docs.adobe.com/content/help/en/audience-manager/user-guide/dil-api/dil-instance-methods.html#idsync)
