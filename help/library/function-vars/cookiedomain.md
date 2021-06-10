---
description: Vereist voor meerdelige domeinen van het hoogste niveau waarbij een van de laatste twee delen van de URL groter is dan 2 tekens.
keywords: ID-service
title: cookieDomain
exl-id: 280416ad-372a-4a59-a938-0f49c0ce300f
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '56'
ht-degree: 10%

---

# cookieDomain{#cookiedomain}

Vereist voor meerdelige domeinen van het hoogste niveau waarbij een van de laatste twee delen van de URL groter is dan 2 tekens.

**Syntaxis:** ` cookieDomain: " *`URL`*"`  (Het  `www` voorvoegsel is niet vereist.)

**Gebruiksscenario**

* Vereist: `www.example.com.uk`
* Niet vereist: `www.example.co.uk`

**Codevoorbeeld**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   cookieDomain:"example.com.uk" 
});
```
