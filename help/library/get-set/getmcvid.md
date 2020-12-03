---
description: getMarketingCloudVisitorID retourneert de Experience Cloud-bezoeker-id.
keywords: ID Service
seo-description: getMarketingCloudVisitorID retourneert de Experience Cloud-bezoeker-id.
seo-title: getMarketingCloudVisitorID
title: getMarketingCloudVisitorID
uuid: 93e16220-b5b3-4d81-9189-30031bc15129
translation-type: tm+mt
source-git-commit: 4a5fbc971dc950c65e5c8f92dffdfe5dde528b54
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---


# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID retourneert de Experience Cloud-bezoeker-id.

**Syntaxis:** ` var *`variabelenaam`* = visitor.getMarketingCloudVisitorID()`

Deze methode wordt meestal gebruikt met aangepaste oplossingen waarvoor de bezoeker-id moet worden gelezen. Het wordt niet gebruikt door een standaardimplementatie. `getMarketingCloudVisitorID` werkt ook met callback-functies om [!DNL Analytics] id&#39;s te lezen en deze naar uw systeem of toepassing te brengen.

```js
//callback function 
var useMarketingCloudID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get the Experience Cloud ID and pass it to the function 
var mcID = visitor.getMarketingCloudVisitorID(useMarketingCloudID)
```

>[!TIP]
>
>Als u een [!DNL Analytics] [!DNL Analytics] klant bent, moet u ook controleren op de id en deze naar uw functie verzenden. U wilt bijvoorbeeld beide id&#39;s wanneer u de bezoekersidentiteitskaart in een verborgen formulierelement doorgeeft aan een servertoepassing die de API voor het invoegen van gegevens gebruikt. In dit geval moet u de id&#39;s [!DNL Experience Cloud] en [!DNL Analytics] bezoekers verzamelen en retourneren. Zie [Bezoeker-id](../../library/get-set/getanalyticsvisitorid.md)voor analysemogelijkheden ophalen.

