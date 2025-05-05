---
description: Retourneert de (eventuele) bestaande Analytics-id die in het s_vi-cookie is opgeslagen voordat de Experience Cloud Identity Service werd geïmplementeerd. Er wordt een lege tekenreeks geretourneerd als aan een bezoeker nooit een Analytics-id is toegewezen.
keywords: ID-service
title: getAnalyticsVisitorID
exl-id: 82973de4-4257-4aab-9268-4ab124a01ee2
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---

# getAnalyticsVisitorID{#getanalyticsvisitorid}

Retourneert de (eventuele) bestaande Analytics-id die in het s_vi-cookie is opgeslagen voordat de Experience Cloud Identity Service werd geïmplementeerd. Er wordt een lege tekenreeks geretourneerd als aan een bezoeker nooit een Analytics-id is toegewezen.

**Syntaxis** `var analyticsID = visitor.getAnalyticsVisitorID()`

Deze functie wordt meestal gebruikt met aangepaste oplossingen waarvoor de bezoeker-id moet worden gelezen. Het wordt niet gebruikt door een standaardimplementatie. `getAnalyticsVisitorID` werkt ook met callback-functies om [!DNL Analytics] ID&#39;s te lezen en deze naar uw systeem of toepassing te brengen.

**Code van de Steekproef**

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
>Als u een [!DNL Analytics] -klant bent, controleert u ook of de [!DNL Analytics] -id is opgeslagen en verzendt u deze naar uw functie. U wilt bijvoorbeeld beide id&#39;s wanneer u de bezoekersidentiteitskaart in een verborgen formulierelement doorgeeft aan een servertoepassing die de API voor het invoegen van gegevens gebruikt. In dit geval moet u de gebruikers-id&#39;s [!DNL Experience Cloud] en [!DNL Analytics] verzamelen en retourneren. Zie [ getMarketingCloudVisitorID ](../../library/get-set/getmcvid.md).

**de &quot;hulp&quot;Parameter is een Verouderde Waarde**

De parameter `aid` wordt in een queryreeks weergegeven onder twee verschillende toestanden.

**Geval 1**

De parameter `aid` wordt in een queryreeks weergegeven wanneer:

* De [!DNL Experience Cloud] ID-service wordt correct geïmplementeerd.
* De gebruiker die een plaats bezoekt heeft een reeds bestaande [!DNL Analytics] identiteitskaart die in hun [ s_vi koekje ](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html?lang=nl-NL#section-5d50a078de444d12b7d927d68ff3b679) wordt opgeslagen.

**Geval 2**

U zult de `aid` parameter in een vraagkoord zien wanneer uw organisatie a [ respijtperiode ](../../reference/analytics-reference/grace-period.md) alvorens de dienst van identiteitskaart volledig uit te voeren gebruikt. Als de gebruiker die uw site bezoekt nieuw is en u geen respijtperiode gebruikt, krijgt de bezoeker de parameter `mid` ( [!DNL Experience Cloud] ID).

>[!MORELIKETHIS]
>
>* [ Cookies van Analytics ](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-privacy.html?lang=nl-NL)
