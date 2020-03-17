---
description: Met deze variabele kunt u het standaardleveninterval voor het AMCV-cookie overschrijven.
keywords: ID Service
seo-description: Met deze variabele kunt u het standaardleveninterval voor het AMCV-cookie overschrijven.
seo-title: cookieLifetime
title: cookieLifetime
uuid: cd945db3-429a-4625-ac3f-69ac259377a3
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# cookieLifetime{#cookielifetime}

Met deze variabele kunt u het standaardleveninterval voor het AMCV-cookie overschrijven.

Standaard verlopen cookies van de [!DNL Experience Cloud] ID-service na 24 maanden. Stel het tijdsinterval in seconden in.

**Syntaxis:** ` cookieLifetime: *`levensduur in seconden`*`

**Codevoorbeeld**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example changes expiration period to 12-months. 
   cookieLifetime:31536000 
});
```

