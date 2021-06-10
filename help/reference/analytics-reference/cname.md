---
description: Als u een hoofdinvoersite hebt waarop klanten kunnen worden geïdentificeerd voordat ze andere domeinen bezoeken, kan een CNAME het bijhouden van gegevens naar andere domeinen toestaan in browsers die cookies van derden (zoals Safari) niet accepteren.
keywords: volgorde van activiteiten;ID-service
title: Overzicht van CNAME-implementatie
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# Overzicht van CNAME-implementatie{#cname-implementation-overview}

De implementaties van CNAME staan u toe om het inzamelingsdomein aan te passen dat door Adobe wordt gebruikt zodat zij uw eigen domein aanpassen. Op deze manier kan Adobe cookies van de eerste partij op de server instellen in plaats van op de client via JavaScript. In het verleden golden voor deze eersteklas cookies aan de serverzijde geen beperkingen die waren opgelegd in het kader van het ITP-beleid (Intelligent Tracking Prevention) van Apple. Nochtans, in November 2020, [!DNL Apple] bijgewerkt hun beleid zodat deze beperkingen ook werden toegepast op koekjes die via CNAME worden geplaatst. Momenteel geldt dat zowel cookies die via CNAME op de server zijn ingesteld als cookies die via Javascript op de client zijn ingesteld, beperkt zijn tot een vervaldatum van 7 dagen of 24 uur onder ITP. Voor meer informatie over het beleid ITP, zie dit [!DNL Apple] document [over het volgen preventie](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp).

Terwijl een implementatie CNAME geen voordelen in termen van koekjesleven verstrekt, kunnen er sommige andere voordelen zoals ad blokkers en minder gemeenschappelijke browsers zijn die gegevens verhinderen worden verzonden naar domeinen die zij als Trackers classificeren. In die gevallen kan het gebruik van een CNAME ervoor zorgen dat de gegevensverzameling niet wordt onderbroken voor gebruikers die deze gereedschappen gebruiken.