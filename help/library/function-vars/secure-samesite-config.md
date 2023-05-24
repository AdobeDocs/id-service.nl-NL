---
description: Een configuratie binnen ECID die kan worden gebruikt om AMCV-cookies op Google AMP-pagina's te ondersteunen.
keywords: ID-service
title: Beveiligde en SameSite-configuraties
exl-id: c3bc44fc-5adc-4eae-8169-9d731d148458
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 1%

---

# Beveiligde en SameSite-configuraties

Met deze configuratie kunt u de instellingen voor uw cookies en ondersteuning wijzigen [AMCV-cookies](../../introduction/cookies.md) op AMP-pagina&#39;s van Google.

Met de service Adobe-bezoeker-id worden ECID-cookies ingesteld met de standaardinstelling van de browser van `SameSite = Lax`, die niet toegankelijk is als de pagina wordt geladen in een iframe zoals een Google AMP-pagina. Voor toegang tot ECID-cookies gebruikt u de onderstaande configuraties om de SameSite-instelling bij te werken naar `SameSite = None`.

>[!NOTE]
>
>Bij toepassen `SameSite = None`, cookies moeten zijn ingesteld op `Secure`, zodat gegevens alleen via HTTPS-verbindingen kunnen worden doorgegeven.

**Implementatie**:

Als u Adobe Experience Platform Launch gebruikt, dient u de extensie van uw Experience Cloud-id te upgraden naar versie 5.1.0 en de configuratie `secureCookie: true` en `sameSiteCookie: none`.

Als u geen Experience Platform Launch gebruikt, werkt u bij naar de nieuwste bibliotheek van Visitor 5.1.0 en volgt u de onderstaande configuraties terwijl u de Visitor-instantie initialiseert:

**Codevoorbeeld**

```js
var visitor = Visitor.getInstance("IMSORG_ID", {

     secureCookie: true,

     sameSiteCookie: "None"

});
```
