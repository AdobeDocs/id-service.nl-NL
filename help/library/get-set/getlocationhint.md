---
description: Retourneert de Experience Cloud Identity Service region ID. Een regio-id (of locatiehint) is een numerieke id voor de geografische locatie van een bepaald datacenter van de ID-service. U hebt de regio-id nodig om API-aanroepen van de server naar Audience Manager te kunnen uitvoeren.
keywords: ID Service
seo-description: Retourneert de Experience Cloud Identity Service region ID. Een regio-id (of locatiehint) is een numerieke id voor de geografische locatie van een bepaald datacenter van de ID-service. U hebt de regio-id nodig om API-aanroepen van de server naar Audience Manager te kunnen uitvoeren.
seo-title: getLocationHint
title: getLocationHint
uuid: cdc312b7-d270-4a5c-a2bb-0fbb37f1e2f4
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# getLocationHint{#getlocationhint}

Retourneert de Experience Cloud Identity Service region ID. Een regio-id (of locatiehint) is een numerieke id voor de geografische locatie van een bepaald datacenter van de ID-service. U hebt de regio-id nodig om API-aanroepen van de server naar Audience Manager te kunnen uitvoeren.

**Syntaxis:** naam ` var *`variabele`* = visitor.getLocationHint()`

Voor een lijst van gebied IDs en overeenkomstige plaatsen, zie [DCS Gebied IDs, Locaties, en de Namen](https://marketing.adobe.com/resources/help/en_US/aam/dcs-regions.html)van de Gastheer.

**Codevoorbeeld**

De functie voor locatiehint leest de regio-id uit het AMCV-cookie. Als de regio-id al is ingesteld in het AMCV-cookie, gebeurt de callback onmiddellijk. Als gebied identiteitskaart niet wordt geplaatst, zal de functie op een reactie van de server wachten alvorens gebiedsidentiteitskaart tot callback over te gaan. Uw code kan er ongeveer als volgt uitzien.

```js
//callback function 
var callback = function ( 
<i>region ID here</i>){ 
//do whatever your function does with the region ID 
}; 
 
//Get the region ID 
visitor.getLocationHint(callback, true); 
```

