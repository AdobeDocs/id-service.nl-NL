---
description: Een optionele, Booleaanse vlag die bepaalt hoe de Experience Cloud Identity Service het iFrame voor de synchronisatie van id laadt.
keywords: ID Service
seo-description: Een optionele, Booleaanse vlag die bepaalt hoe de Experience Cloud Identity Service het iFrame voor de synchronisatie van id laadt.
seo-title: idSyncAttachIframeOnWindowLoad
title: idSyncAttachIframeOnWindowLoad
uuid: aa2c2fa4-2cab-4e08-8d35-729a6c3e459a
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 2%

---


# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

Een optionele, Booleaanse vlag die bepaalt hoe de Experience Cloud Identity Service het iFrame voor de synchronisatie van id laadt.

**Syntaxis:** ` `idSyncAttachIframeOnWindowLoad= true|false&quot;(standaardwaarde is `false`.)

Wanneer `idSyncAttachIframeOnWindowLoad: true` de id-service het iFrame voor synchronisatie van de id laadt tijdens het laden van het venster. Standaard laadt de id-service iFrame voor synchronisatie van id&#39;s zo snel mogelijk in plaats van dat het venster wordt geladen.

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

