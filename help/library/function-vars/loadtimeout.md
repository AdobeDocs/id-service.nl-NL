---
description: Stelt een time-outinterval in milliseconden in. Wordt gebruikt om andere oplossingen te vertellen (bijvoorbeeld Analytics, Audience Manager, Target, enz.) hoe lang om op een reactie van de dienst van identiteitskaart te wachten.
keywords: ID Service
seo-description: Stelt een time-outinterval in milliseconden in. Wordt gebruikt om andere oplossingen te vertellen (bijvoorbeeld Analytics, Audience Manager, Target, enz.) hoe lang om op een reactie van de dienst van identiteitskaart te wachten.
seo-title: loadTimeout
title: loadTimeout
uuid: f627e044-bd73-49a4-8a90-6d19aa566751
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# loadTimeout{#loadtimeout}

Stelt een time-outinterval in milliseconden in. Wordt gebruikt om andere oplossingen te vertellen (bijvoorbeeld Analytics, Audience Manager, Target, enz.) hoe lang om op een reactie van de dienst van identiteitskaart te wachten.

**Syntaxis:** ` loadTimeout: *`interval in milliseconden`*`

De standaardwaarde is 30.000 milliseconden (30 seconden). We raden u ten zeerste aan de standaardwaarde *niet* te wijzigen.

>[!NOTE]
>
>Oproepen aan de dienst van identiteitskaart zijn asynchroon met betrekking tot andere, niet code van Adobe op de pagina. Als u het time-outinterval verhoogt of verlaagt, verandert de snelheid waarmee de pagina inhoud weergeeft niet. Lange time-outintervallen kunnen echter wel van invloed zijn op de laadtijden van de pagina, zoals wordt gemeten met de algemene netwerkbewakingstools, maar dit heeft geen invloed op de rendertijd.

**Codevoorbeeld**

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

