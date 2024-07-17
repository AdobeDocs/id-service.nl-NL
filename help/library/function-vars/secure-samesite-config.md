---
description: Een configuratie binnen ECID die kan worden gebruikt om AMCV-cookies op Google AMP-pagina's te ondersteunen.
keywords: ID-service
title: Beveiligde en SameSite-configuraties
exl-id: c3bc44fc-5adc-4eae-8169-9d731d148458
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# Beveiligde en SameSite-configuraties

Deze configuratie staat u toe om de montages voor uw koekjes te veranderen en [ koekjes van AMCV ](../../introduction/cookies.md) op de pagina&#39;s van AMP van Google te steunen.

De Adobe bezoeker-id-service stelt ECID-cookies in met de standaardinstelling van `SameSite = Lax` voor de browser. Deze instelling is niet toegankelijk als de pagina in een iframe wordt geladen, zoals een Google AMP-pagina. Als u toegang wilt tot ECID-cookies, gebruikt u de onderstaande configuraties om de SameSite-instelling bij te werken naar `SameSite = None` .

>[!NOTE]
>
>Wanneer u `SameSite = None` toepast, moeten cookies worden ingesteld op `Secure` , zodat gegevens alleen via HTTPS-verbindingen kunnen worden doorgegeven.

**Implementatie**:

Als u Adobe Experience Platform Launch gebruikt, moet u de extensie van uw Experience Cloud-id upgraden naar versie 5.1.0 en `secureCookie: true` en `sameSiteCookie: none` configureren.

Als u geen Experience Platform Launch gebruikt, werkt u bij naar de nieuwste bibliotheek van Visitor 5.1.0 en volgt u de onderstaande configuraties terwijl u de Visitor-instantie initialiseert:

**Steekproef van de Code**

```js
var visitor = Visitor.getInstance("IMSORG_ID", {

     secureCookie: true,

     sameSiteCookie: "None"

});
```
