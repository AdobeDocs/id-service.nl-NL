---
description: Vereist voor meerdelige domeinen van het hoogste niveau waarbij een van de laatste twee delen van de URL groter is dan 2 tekens.
keywords: ID Service
seo-description: Vereist voor meerdelige domeinen van het hoogste niveau waarbij een van de laatste twee delen van de URL groter is dan 2 tekens.
seo-title: cookieDomain
title: cookieDomain
uuid: a57e5477-c07b-4d54-8aea-8e8b152f1423
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# cookieDomain{#cookiedomain}

Vereist voor meerdelige domeinen van het hoogste niveau waarbij een van de laatste twee delen van de URL groter is dan 2 tekens.

**Syntaxis:** ` cookieDomain: " *`URL`*"` (Het `www` voorvoegsel is niet vereist.)

**Hoofdletters gebruiken**

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

