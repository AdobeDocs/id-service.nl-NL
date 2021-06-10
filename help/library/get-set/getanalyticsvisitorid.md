---
description: Retourneert de (eventuele) bestaande Analytics-id die in het s_vi-cookie is opgeslagen voordat de Experience Cloud Identity Service werd geïmplementeerd. Er wordt een lege tekenreeks geretourneerd als aan een bezoeker nooit een Analytics-id is toegewezen.
keywords: ID-service
title: getAnalyticsVisitorID
exl-id: 82973de4-4257-4aab-9268-4ab124a01ee2
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 3%

---

# getAnalyticsVisitorID{#getanalyticsvisitorid}

Retourneert de (eventuele) bestaande Analytics-id die in het s_vi-cookie is opgeslagen voordat de Experience Cloud Identity Service werd geïmplementeerd. Er wordt een lege tekenreeks geretourneerd als aan een bezoeker nooit een Analytics-id is toegewezen.

**Syntaxis** `var analyticsID = visitor.getAnalyticsVisitorID()`

Deze functie wordt meestal gebruikt met aangepaste oplossingen waarvoor de bezoeker-id moet worden gelezen. Het wordt niet gebruikt door een standaardimplementatie. `getAnalyticsVisitorID` werkt ook met callback functies om  [!DNL Analytics] IDs te lezen en hen in uw systeem of toepassing te brengen.

**Voorbeeldcode**

```js
//callback function 
var useAnalyticsVisitorID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get Analytics ID and pass it to the function 
var analyticsID = visitor.getAnalyticsVisitorID(useAnalyticsVisitorID)
```

>[!TIP]
>
>Als u een [!DNL Analytics] klant bent, controleert en verzendt ook [!DNL Analytics] identiteitskaart aan uw functie. U wilt bijvoorbeeld beide id&#39;s wanneer u de bezoekersidentiteitskaart in een verborgen formulierelement doorgeeft aan een servertoepassing die de API voor het invoegen van gegevens gebruikt. In dit geval dient u de [!DNL Experience Cloud]- en [!DNL Analytics]-bezoeker-id&#39;s te verzamelen en te retourneren. Zie [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md).

**De parameter &quot;aid&quot; is een oudere waarde**

De parameter `aid` verschijnt in een vraagkoord onder 2 verschillende reeksen voorwaarden.

**Zaak 1**

U zult de `aid` parameter in een vraagkoord zien wanneer:

* De [!DNL Experience Cloud] ID-service wordt op de juiste wijze geïmplementeerd.
* De gebruiker die een site bezoekt, heeft een bestaande [!DNL Analytics]-id opgeslagen in het [s_vi-cookie](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-analytics.html#section-5d50a078de444d12b7d927d68ff3b679).

**Zaak 2**

U zult de `aid` parameter in een vraagkoord zien wanneer uw organisatie [respijtperiode](../../reference/analytics-reference/grace-period.md) alvorens de dienst van identiteitskaart volledig uit te voeren gebruikt. Als de gebruiker die uw site bezoekt nieuw is en u geen respijtperiode gebruikt, krijgt de bezoeker de parameter `mid` ( [!DNL Experience Cloud] ID).

>[!MORELIKETHIS]
>
>* [Analysecookies](https://docs.adobe.com/content/help/nl-NL/core-services/interface/ec-cookies/cookies-privacy.html)

