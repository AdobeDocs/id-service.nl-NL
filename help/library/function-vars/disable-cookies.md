---
description: Een optionele, Booleaanse vlag die voorkomt dat de Experience Cloud Identity Service het cookie demdex.net van derden retourneert.
keywords: ID Service
seo-description: Een optionele, Booleaanse vlag die voorkomt dat de Experience Cloud Identity Service het cookie demdex.net van derden retourneert.
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7ed5aa16-44ca-4702-878a-1a208ca95270
translation-type: tm+mt
source-git-commit: 584b6240c3e0286111689499ca5df5d98aa9fab2

---


# disableThirdPartyCookies{#disablethirdpartycookies}

Een optionele, Booleaanse vlag die voorkomt dat de Experience Cloud Identity Service het cookie demdex.net van derden retourneert.

>[!NOTE]
>
>Aan deze configuratie is `idSyncDisable3rdPartySyncing` en de naam is gewijzigd `disableThirdPartyCookies` in de release van 18 januari 2018 van v3.0.

**Syntaxis:** `disableThirdPartyCookies: true|false` (standaardwaarde is `false`.) Voor `VisitorAPI.js` v3.0.0 of hoger.

Als `disableThirdPartyCookies: true`de id-service de cookie van de derde, demdex.net, niet retourneert (zie [Cookies en de Experience Cloud Identity Service](../../introduction/cookies.md) ). Als een sitebezoeker deze cookie al in zijn browser heeft, gebruikt de id-service deze niet om een nieuwe Experience Cloud ID (MID) te maken of een bestaande ID te retourneren. In plaats daarvan maakt de id-service een nieuwe, willekeurige id in het cookie van de eerste partij. Als deze optie is ingeschakeld, kunt u gegevens verzamelen met de id-service en deze delen met verschillende Experience Cloud-oplossingen.

**Codevoorbeeld**

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

