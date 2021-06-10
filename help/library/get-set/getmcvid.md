---
description: getMarketingCloudVisitorID retourneert de Experience Cloud-bezoeker-id.
keywords: ID-service
title: getMarketingCloudVisitorID
exl-id: bd81cc0b-0511-492d-beb8-8ba2fe5d4323
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 0%

---

# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID retourneert de Experience Cloud-bezoeker-id.

**Syntaxis:naam** ` var *`variabele`* = visitor.getMarketingCloudVisitorID()`

Deze methode wordt meestal gebruikt met aangepaste oplossingen waarvoor de bezoeker-id moet worden gelezen. Het wordt niet gebruikt door een standaardimplementatie. `getMarketingCloudVisitorID` werkt ook met callback functies om  [!DNL Analytics] IDs te lezen en hen in uw systeem of toepassing te brengen.

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
>Als u een [!DNL Analytics] klant bent, controleert en verzendt ook [!DNL Analytics] identiteitskaart aan uw functie. U wilt bijvoorbeeld beide id&#39;s wanneer u de bezoekersidentiteitskaart in een verborgen formulierelement doorgeeft aan een servertoepassing die de API voor het invoegen van gegevens gebruikt. In dit geval dient u de [!DNL Experience Cloud]- en [!DNL Analytics]-bezoeker-id&#39;s te verzamelen en te retourneren. Zie [Bezoeker voor analysemogelijkheden-ID](../../library/get-set/getanalyticsvisitorid.md) ophalen.
