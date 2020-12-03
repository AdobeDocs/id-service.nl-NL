---
description: Een optionele, Booleaanse vlag die voorkomt dat de Experience Cloud Identity Service het cookie demdex.net van een derde retourneert.
keywords: ID Service
seo-description: Een optionele, Booleaanse vlag die voorkomt dat de Experience Cloud Identity Service het cookie demdex.net van een derde retourneert.
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7ed5aa16-44ca-4702-878a-1a208ca95270
translation-type: tm+mt
source-git-commit: 584b6240c3e0286111689499ca5df5d98aa9fab2
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 1%

---


# disableThirdPartyCookies{#disablethirdpartycookies}

Een optionele, Booleaanse vlag die voorkomt dat de Experience Cloud Identity Service het cookie demdex.net van een derde retourneert.

>[!NOTE]
>
>Aan deze configuratie is `idSyncDisable3rdPartySyncing` en de naam is gewijzigd `disableThirdPartyCookies` in de release van 18 januari 2018 van v3.0.

**Syntaxis:** `disableThirdPartyCookies: true|false` (standaardwaarde is `false`.) Voor `VisitorAPI.js` v3.0.0 of hoger.

Wanneer `disableThirdPartyCookies: true`, keert de dienst van identiteitskaart niet de derde, demdex.net koekje terug (zie [Cookies en de Dienst](../../introduction/cookies.md) van de Identiteit van de Experience Cloud). Als een sitebezoeker deze cookie al in zijn browser heeft, gebruikt de id-service deze niet om een nieuwe Experience Cloud-id (MID) te maken of een bestaande id te retourneren. In plaats daarvan maakt de id-service een nieuwe, willekeurige id in het cookie van de eerste partij. Zodra toegelaten, kunt u gegevens met de dienst van identiteitskaart verzamelen en het over verschillende oplossingen van Experience Cloud delen.

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

