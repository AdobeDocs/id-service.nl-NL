---
description: Retourneert de (eventuele) bestaande Analytics-id die in het s_vi-cookie is opgeslagen voordat de Experience Cloud Identity Service werd geïmplementeerd. Er wordt een lege tekenreeks geretourneerd als aan een bezoeker nooit een Analytics-id is toegewezen.
keywords: ID-service
title: getAnalyticsVisitorID
exl-id: 82973de4-4257-4aab-9268-4ab124a01ee2
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# getAnalyticsVisitorID{#getanalyticsvisitorid}

Retourneert de (eventuele) bestaande Analytics-id die in het s_vi-cookie is opgeslagen voordat de Experience Cloud Identity Service werd geïmplementeerd. Er wordt een lege tekenreeks geretourneerd als aan een bezoeker nooit een Analytics-id is toegewezen.

**Syntaxis** `var analyticsID = visitor.getAnalyticsVisitorID()`

Deze functie wordt meestal gebruikt met aangepaste oplossingen waarvoor de bezoeker-id moet worden gelezen. Het wordt niet gebruikt door een standaardimplementatie. `getAnalyticsVisitorID` werkt ook met callback functies om te lezen [!DNL Analytics] ID&#39;s en breng ze naar uw systeem of toepassing.

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
>Als je een [!DNL Analytics] klant, controleren en verzenden ook [!DNL Analytics] ID aan uw functie. U wilt bijvoorbeeld beide id&#39;s wanneer u de bezoekersidentiteitskaart in een verborgen formulierelement doorgeeft aan een servertoepassing die de API voor het invoegen van gegevens gebruikt. In dit geval dient u de [!DNL Experience Cloud] en [!DNL Analytics] bezoeker-id&#39;s. Zie [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md).

**De parameter &quot;aid&quot; is een oudere waarde**

De `aid` wordt in een queryreeks weergegeven onder 2 verschillende sets voorwaarden.

**Zaak 1**

U ziet de `aid` parameter in een queryreeks als:

* De [!DNL Experience Cloud] De dienst van identiteitskaart wordt opgesteld correct.
* De gebruiker die een site bezoekt, heeft al een [!DNL Analytics] ID opgeslagen in hun [s_vi cookie](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html#section-5d50a078de444d12b7d927d68ff3b679).

**Zaak 2**

U ziet de `aid` parameter in een vraagkoord wanneer uw organisatie een [respijtperiode](../../reference/analytics-reference/grace-period.md) voordat u de id-service volledig implementeert. Als de gebruiker die uw site bezoekt nieuw is en u geen respijtperiode gebruikt, krijgt de bezoeker de `mid` ( [!DNL Experience Cloud] ID).

>[!MORELIKETHIS]
>
>* [Analysecookies](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-privacy.html)

