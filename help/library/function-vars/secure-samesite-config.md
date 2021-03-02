---
description: Een configuratie binnen ECID die kan worden gebruikt voor de ondersteuning van AMCV-cookies op Google AMP-pagina's.
keywords: ID-service
seo-description: Een configuratie binnen ECID die kan worden gebruikt voor de ondersteuning van AMCV-cookies op Google AMP-pagina's.
seo-title: Beveiligde en SameSite-configuraties
title: Beveiligde en SameSite-configuraties
translation-type: tm+mt
source-git-commit: 702d20f3989f7749fb173496765d94c3a5af46dc
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 1%

---


# Beveiligde en SameSite-configuraties

Met deze configuratie kunt u de instellingen voor uw cookies wijzigen en [AMCV-cookies](../../introduction/cookies.md) op Google AMP-pagina&#39;s ondersteunen.

De Adobe-bezoeker-id-service stelt ECID-cookies in met de standaardinstelling voor de browser van `SameSite = Lax`, die niet toegankelijk is als de pagina in een iframe zoals een Google AMP-pagina wordt geladen. Als u toegang wilt tot ECID-cookies, gebruikt u de onderstaande configuraties om de SameSite-instelling bij te werken naar `SameSite = None`.

>[!NOTE]
>
>Bij het toepassen van `SameSite = None` moeten cookies worden ingesteld op `Secure`, zodat gegevens alleen via HTTPS-verbindingen kunnen worden doorgegeven.

**Implementatie**:

Als u Adobe Experience Platform Launch gebruikt, dient u de extensie van uw Experience Cloud-id te upgraden naar versie 5.1.0 en `secureCookie: true` en `sameSiteCookie: none` te configureren.

Als u geen Experience Platform Launch gebruikt, werkt u bij naar de nieuwste bibliotheek van Visitor 5.1.0 en volgt u de onderstaande configuraties terwijl u de Visitor-instantie initialiseert:

**Codevoorbeeld**

```js
var visitor = Visitor.getInstance("IMSORG_ID", {

     secureCookie: true,

     sameSiteCookie: "None"

});
```
