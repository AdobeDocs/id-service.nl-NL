---
description: Een optionele, Booleaanse markering die id-synchronisatie uitschakelt.
keywords: ID Service
seo-description: Een optionele, Booleaanse markering die id-synchronisatie uitschakelt.
seo-title: disableIdSyncs
title: disableIdSyncs
uuid: 8bea1de8-53c8-4a15-bcf5-f0869763a32e
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# disableIdSyncs{#disableidsyncs}

Een optionele, Booleaanse markering die id-synchronisatie uitschakelt.

>[!NOTE]
>
>Aan deze configuratie is `idSyncDisableSyncs` en de naam is gewijzigd `disableIdSyncs` in de release van 18 januari 2018 van v3.0.

**Syntaxis:** `disableIdSyncs: true|false` (standaardwaarde is `false`.)

**Codevoorbeeld**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableIdSyncs: true 
});
```

