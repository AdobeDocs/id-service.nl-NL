---
description: Een optionele, Booleaanse vlag die bepaalt hoe de Experience Cloud Identity Service het iFrame voor de synchronisatie van id laadt.
keywords: ID-service
title: idSyncAttachIframeOnWindowLoad
exl-id: 44c45378-f007-4d87-913a-d6bb9961948c
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '77'
ht-degree: 2%

---

# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

Een optionele, Booleaanse vlag die bepaalt hoe de Experience Cloud Identity Service het iFrame voor de synchronisatie van id laadt.

**Syntaxis:** ` `idSyncAttachIframeOnWindowLoad= true|false&quot;(standaardwaarde is `false`.)

Wanneer `idSyncAttachIframeOnWindowLoad: true` De id-service laadt het iFrame voor synchronisatie van de id tijdens het laden van het venster. Standaard laadt de id-service iFrame voor synchronisatie van id&#39;s zo snel mogelijk in plaats van dat het venster wordt geladen.

**Codevoorbeeld**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example loads ID sync iFrame on window load instad of ASAP. 
   idSyncAttachIframeOnWindowLoad: true 
});
```
