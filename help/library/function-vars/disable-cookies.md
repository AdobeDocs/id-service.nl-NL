---
description: Een optionele, Booleaanse markering die voorkomt dat de Experience Cloud Identity Service de cookie van de derde retourneert, namelijk demdex.net.
keywords: ID-service
title: disableThirdPartyCookies
exl-id: 19d12822-0e17-4a1c-8e9c-25a22e20a4a8
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 0%

---

# disableThirdPartyCookies{#disablethirdpartycookies}

Een optionele, Booleaanse markering die voorkomt dat de Experience Cloud Identity Service de cookie van de derde retourneert, namelijk demdex.net.

>[!NOTE]
>
>Deze configuratie was `idSyncDisable3rdPartySyncing` en hernoemd naar `disableThirdPartyCookies` in de release van 18 januari 2018 van v3.0.

**Syntaxis:** `disableThirdPartyCookies: true|false` (gebrek is `false`.) Voor `VisitorAPI.js` v3.0.0 of hoger.

Wanneer `disableThirdPartyCookies: true`, keert de dienst van identiteitskaart niet de derde terug, demdex.net koekje (zie [ Cookies en de Dienst van de Identiteit van het Experience Cloud ](../../introduction/cookies.md)). Als een sitebezoeker dit cookie al in zijn browser heeft, gebruikt de id-service dit niet om een nieuwe Experience Cloud-id (MID) te maken of een bestaande id te retourneren. In plaats daarvan maakt de id-service een nieuwe, willekeurige id in het cookie van de eerste partij. Zodra toegelaten, kunt u gegevens met de dienst van identiteitskaart verzamelen en het over verschillende Experience Cloud oplossingen delen.

**Steekproef van de Code**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCookies: true 
});
```
