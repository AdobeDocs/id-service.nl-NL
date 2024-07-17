---
description: Met deze variabele kunt u het standaardleveninterval voor het AMCV-cookie overschrijven.
keywords: ID-service
title: cookieLifetime
exl-id: bdbabdcd-a87b-412c-8c2f-3f39820f939a
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 0%

---

# cookieLifetime{#cookielifetime}

Met deze variabele kunt u het standaardleveninterval voor het AMCV-cookie overschrijven.

[!DNL Experience Cloud] ID-servicecookies verlopen standaard na 24 maanden. Stel het tijdsinterval in seconden in.

**Syntaxis:** ` cookieLifetime: *` leven in seconden `*`

**Steekproef van de Code**

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
