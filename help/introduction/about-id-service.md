---
description: De rol van de Experience Cloud Identity Service in de Adobe Experience Cloud.
keywords: ID-service
title: Overzicht
exl-id: d907e299-bde0-4b5f-8c16-867a4eaa8be1
source-git-commit: 2c87022baeb09a8767d0d9627bf2b607c51b2503
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Over de id-service{#aboutidservice}

De rol van de Experience Cloud Identity Service in de Adobe Experience Cloud.

<!--
mcvid-functionality.xml
-->

## De identiteitsdienst van het Experience Cloud: Een stichtend element van de Diensten van de Kern {#section-2de0eb1d65664e92a4d8bbb167b84bde}

De Dienst van de Identiteit van het Experience Cloud laat het gemeenschappelijke identificatiekader voor de Diensten van de Kern van de Experience Cloud, oplossingen, en klantenattributen en publiek toe. Dit werkt door een unieke, permanente id toe te wijzen aan een sitebezoeker. Wanneer uw organisatie de id-service implementeert, kunt u met deze id dezelfde sitebezoeker en de bijbehorende gegevens identificeren in verschillende Experience Cloud-oplossingen.

![](assets/ecid-new.png)

Ook, kan de dienst van identiteitskaart de verschillende oplossing-specifieke IDs (b.v., Analytics HULP) vervangen. En, door de [ IDs van de Klant en de Status van de Authentificatie ](../reference/authenticated-state.md) functionaliteit, laat de dienst van identiteitskaart u in uw eigen klant IDs tot [!DNL Experience Cloud] overgaan. Houd er echter rekening mee dat de id-service alleen werkt met de oplossingen waarop u al bent geabonneerd. Het zal geen toegang tot andere producten verlenen als u niet voor hen wordt geregistreerd.

De id-service is een integraal onderdeel van vele functies, verbeteringen en services die momenteel en in de toekomst in [!DNL Experience Cloud] worden gebruikt. Momenteel, steunt de dienst van identiteitskaart [ Analytics ](http://www.adobe.com/marketing-cloud/web-analytics.html), [ Audience Manager ](http://www.adobe.com/marketing-cloud/data-management-platform.html), en [ Doel ](http://www.adobe.com/marketing-cloud/testing-targeting.html). En dit is vereist als u wilt deelnemen aan de [!DNL Adobe Experience Cloud] Device Co-op. Als u de id-service niet hebt geïmplementeerd, is het nu tijd om een migratiestrategie te overwegen.

## Overzicht van functies {#section-96555473455c4bf8924c2d56ff4f3255}

Samenvattend, de dienst van identiteitskaart:

* Hiermee maakt u een algemene sleutel of id die kan worden gebruikt om profielen en identiteiten te koppelen.
* Identificeert een apparaat op unieke wijze over veelvoudige oplossingen.
* Plaatst een eerstepartijkoekje in het domein van de klant om het volgen op het zelfde domein te verzekeren. Zie [ Experience Cloud ](../introduction/cookies.md).
* Ontvangt aliassen en identiteitskaart- afbeeldingen van [!DNL Experience Cloud] klanten en partners.
* Beheert de synchronisatie van id&#39;s binnen de [!DNL Experience Cloud] .
* Ondersteunt synchronisatie van id&#39;s met verschillende derden in het ecosysteem van de advertentietechnologie.
