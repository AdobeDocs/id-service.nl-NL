---
description: Retourneert de eventuele oudere Analytics-id die in het s_vi-cookie is opgeslagen voordat de Experience Cloud Identity Service werd geïmplementeerd. Er wordt een lege tekenreeks geretourneerd als aan een bezoeker nooit een Analytics-id is toegewezen.
keywords: ID Service
seo-description: Retourneert de eventuele oudere Analytics-id die in het s_vi-cookie is opgeslagen voordat de Experience Cloud Identity Service werd geïmplementeerd. Er wordt een lege tekenreeks geretourneerd als aan een bezoeker nooit een Analytics-id is toegewezen.
seo-title: getAnalyticsVisitorID
title: getAnalyticsVisitorID
uuid: 6bb8ddfc-9fc1-4105-b377-d9b4d247a0f8
translation-type: tm+mt
source-git-commit: c4c0b791230422f17292b72fd45ba5689a60adae

---


# getAnalyticsVisitorID{#getanalyticsvisitorid}

Retourneert de eventuele oudere Analytics-id die in het s_vi-cookie is opgeslagen voordat de Experience Cloud Identity Service werd geïmplementeerd. Er wordt een lege tekenreeks geretourneerd als aan een bezoeker nooit een Analytics-id is toegewezen.

**Syntaxis**`var analyticsID = visitor.getAnalyticsVisitorID()`

Deze functie wordt meestal gebruikt met aangepaste oplossingen waarvoor de bezoeker-id moet worden gelezen. Het wordt niet gebruikt door een standaardimplementatie. `getAnalyticsVisitorID` werkt ook met callback-functies om [!DNL Analytics] id&#39;s te lezen en deze naar uw systeem of toepassing te brengen.

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
>Als u een [!DNL Analytics] [!DNL Analytics] klant bent, moet u ook controleren op de id en deze naar uw functie verzenden. U wilt bijvoorbeeld beide id&#39;s wanneer u de bezoekersidentiteitskaart in een verborgen formulierelement doorgeeft aan een servertoepassing die de API voor het invoegen van gegevens gebruikt. In dit geval moet u de id&#39;s [!DNL Experience Cloud] en [!DNL Analytics] bezoekers verzamelen en retourneren. Zie [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md).

**De parameter &quot;aid&quot; is een oudere waarde**

De `aid` parameter wordt in een queryreeks weergegeven onder 2 verschillende toestanden.

**Zaak 1**

U zult de `aid` parameter in een vraagkoord zien wanneer:

* De [!DNL Experience Cloud] id-service wordt correct geïmplementeerd.
* De gebruiker die een site bezoekt, heeft een bestaande [!DNL Analytics] id opgeslagen in zijn [s_vi cookie](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html).

**Zaak 2**

U zult de `aid` parameter in een vraagkoord zien wanneer uw organisatie een [respijtperiode](../../reference/analytics-reference/grace-period.md) alvorens de dienst van identiteitskaart volledig uit te voeren gebruikt. Als de gebruiker die uw site bezoekt nieuw is en u geen respijtperiode gebruikt, krijgt de bezoeker de parameter `mid` ( [!DNL Experience Cloud] ID).

>[!MORELIKETHIS]
>
>* [Analysecookies](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_analytics.html)

