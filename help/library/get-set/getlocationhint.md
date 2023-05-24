---
description: Retourneert de Experience Cloud Identity Service region-id. Een regio-id (of locatiehint) is een numerieke id voor de geografische locatie van een bepaald datacenter van de ID-service. U hebt de regio-id nodig om API-aanroepen van de server naar de Audience Manager te kunnen uitvoeren.
keywords: ID-service
title: getLocationHint
exl-id: 0213f828-a985-4201-8a38-0a4b170ed057
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 1%

---

# getLocationHint{#getlocationhint}

Retourneert de Experience Cloud Identity Service region-id. Een regio-id (of locatiehint) is een numerieke id voor de geografische locatie van een bepaald datacenter van de ID-service. U hebt de regio-id nodig om API-aanroepen van de server naar de Audience Manager te kunnen uitvoeren.

**Syntaxis:** ` var *`variabelenaam`* = visitor.getLocationHint()`

Voor een lijst met regio-id&#39;s en bijbehorende locaties raadpleegt u [Id&#39;s, locaties en hostnamen van DCS-regio&#39;s](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html).

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
