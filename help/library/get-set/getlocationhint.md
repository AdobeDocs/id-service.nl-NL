---
description: Retourneert de Experience Cloud Identity Service region-id. Een regio-id (of locatiehint) is een numerieke id voor de geografische locatie van een bepaald datacenter van de ID-service. U hebt de regio-id nodig om API-aanroepen van de server naar de Audience Manager te kunnen uitvoeren.
keywords: ID Service
seo-description: Retourneert de Experience Cloud Identity Service region-id. Een regio-id (of locatiehint) is een numerieke id voor de geografische locatie van een bepaald datacenter van de ID-service. U hebt de regio-id nodig om API-aanroepen van de server naar de Audience Manager te kunnen uitvoeren.
seo-title: getLocationHint
title: getLocationHint
uuid: cdc312b7-d270-4a5c-a2bb-0fbb37f1e2f4
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---


# getLocationHint{#getlocationhint}

Retourneert de Experience Cloud Identity Service region-id. Een regio-id (of locatiehint) is een numerieke id voor de geografische locatie van een bepaald datacenter van de ID-service. U hebt de regio-id nodig om API-aanroepen van de server naar de Audience Manager te kunnen uitvoeren.

**Syntaxis:** ` var *`variabelenaam`* = visitor.getLocationHint()`

Voor een lijst van gebied IDs en overeenkomstige plaatsen, zie [DCS Gebied IDs, Locaties, en de Namen](https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html)van de Gastheer.

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

