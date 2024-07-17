---
description: Stelt een time-outinterval in milliseconden in. Wordt gebruikt om andere oplossingen te vertellen (bijvoorbeeld Analytics, Audience Manager, Target, enz.) hoe lang om op een reactie van de dienst van identiteitskaart te wachten.
keywords: ID-service
title: loadTimeout
exl-id: 485264f4-ee24-4042-8be3-259e70462110
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# loadTimeout{#loadtimeout}

Stelt een time-outinterval in milliseconden in. Wordt gebruikt om andere oplossingen te vertellen (bijvoorbeeld Analytics, Audience Manager, Target, enz.) hoe lang om op een reactie van de dienst van identiteitskaart te wachten.

**Syntaxis:** ` loadTimeout: *` interval in milliseconden `*`

De standaardwaarde is 30.000 milliseconden (30 seconden). Wij adviseren sterk dat u *niet* de standaardwaarde verandert.

>[!NOTE]
>
>De vraag aan de dienst van identiteitskaart is asynchroon met betrekking tot andere, niet Adobe code op de pagina. Als u het time-outinterval verhoogt of verlaagt, verandert de snelheid waarmee de pagina inhoud weergeeft niet. Lange time-outintervallen kunnen echter wel van invloed zijn op de laadtijden van de pagina, zoals wordt gemeten met de algemene netwerkbewakingstools, maar dit heeft geen invloed op de rendertijd.

**Steekproef van de Code**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example sets the timeout to 10,000 milliseconds (10 seconds). 
   loadTimeout:10000 
});
```
