---
description: Een optionele, Booleaanse vlag die voorkomt dat de Experience Cloud Identity Service het cookie demdex.net van een derde retourneert.
keywords: ID-service
title: disableThirdPartyCookies
exl-id: 19d12822-0e17-4a1c-8e9c-25a22e20a4a8
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 1%

---

# disableThirdPartyCookies{#disablethirdpartycookies}

Een optionele, Booleaanse vlag die voorkomt dat de Experience Cloud Identity Service het cookie demdex.net van een derde retourneert.

>[!NOTE]
>
>Deze configuratie was `idSyncDisable3rdPartySyncing` en hernoemd naar `disableThirdPartyCookies` in de release van 18 januari 2018 van v3.0.

**Syntaxis:** `disableThirdPartyCookies: true|false` (standaardwaarde is  `false`.) Voor `VisitorAPI.js` v3.0.0 of hoger.

Wanneer `disableThirdPartyCookies: true`, de dienst van identiteitskaart niet de derde terugkeert, demdex.net koekje (zie [Cookies en de Dienst van de Identiteit van de Experience Cloud](../../introduction/cookies.md)). Als een sitebezoeker deze cookie al in zijn browser heeft, gebruikt de id-service deze niet om een nieuwe Experience Cloud-id (MID) te maken of een bestaande id te retourneren. In plaats daarvan maakt de id-service een nieuwe, willekeurige id in het cookie van de eerste partij. Zodra toegelaten, kunt u gegevens met de dienst van identiteitskaart verzamelen en het over verschillende oplossingen van Experience Cloud delen.

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
