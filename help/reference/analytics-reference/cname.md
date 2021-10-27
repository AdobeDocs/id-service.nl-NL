---
description: Als u een hoofdinvoersite hebt waarop klanten kunnen worden geïdentificeerd voordat ze andere domeinen bezoeken, kan een CNAME het bijhouden van gegevens naar andere domeinen toestaan in browsers die cookies van derden (zoals Safari) niet accepteren.
keywords: volgorde van activiteiten;ID-service
title: Overzicht van CNAME-implementatie
exl-id: f95dda3c-7bb2-4c7d-a25a-a4d20b58fe27
source-git-commit: 61f9f1888430ff0fdbb90a8cf6561bf23d204a45
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# Overzicht van CNAME-implementatie{#cname-implementation-overview}

De implementaties van CNAME staan u toe om het inzamelingsdomein aan te passen dat door Adobe wordt gebruikt zodat zij uw eigen domein aanpassen. Deze domeinen worden ook bedoeld als eerstepartijinzamelingsdomeinen. Met deze implementaties kan Adobe cookies van de eerste partij instellen op de server in plaats van op de client met behulp van JavaScript. In het verleden golden voor deze eersteklas cookies aan de serverzijde geen beperkingen die waren opgelegd in het kader van het beleid van Apple inzake intelligente traceringspreventie (ITP). In november 2020 [!DNL Apple] hun beleid bijgewerkt zodat deze beperkingen ook werden toegepast op cookies die via CNAME zijn ingesteld. Momenteel geldt dat beide cookies die via CNAME aan de serverzijde zijn ingesteld en cookies die via Javascript aan de clientzijde zijn ingesteld, beperkt zijn tot een vervaldatum van 7 dagen of 24 uur onder ITP. Voor meer informatie over het beleid ITP, zie dit [!DNL Apple] document [over traceringspreventie](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp).

Terwijl een implementatie CNAME geen voordelen in termen van koekjesleven verstrekt, kunnen er sommige andere voordelen zijn. Deze voordelen zijn onder andere adverteerders en minder gangbare browsers die voorkomen dat gegevens worden verzonden naar domeinen die ze als trackers classificeren. In deze gevallen kunt u met een CNAME voorkomen dat de gegevensverzameling wordt onderbroken voor gebruikers die deze gereedschappen gebruiken.

Bovendien staat de implementaties van CNAME u toe om te specificeren **[!UICONTROL Choose custom RDC type]** Hiermee bepaalt u waar de treffers van de gebruikers in eerste instantie worden gerouteerd. De meeste klanten gebruiken geen aangepaste RDC-typen.
