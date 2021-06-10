---
description: De rol van de Experience Cloud Identity Service in de Adobe Experience Cloud.
title: Overzicht van Experience Cloud ID-service
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# Overzicht van Experience Cloud ID-service

Met [!UICONTROL Experience Cloud Identity Service] wordt het gemeenschappelijke identificatiekader ingeschakeld voor Experience Cloud Core Services-oplossingen (zoals klantkenmerken en doelgroepen) in de Experience Platform Identity Service.

>[!NOTE]
>
> U zou verwijzingen naar de dienst van identiteitskaart als acroniemen of vroegere namen, zoals ECID, de Dienst van identiteitskaart van de Marketing Cloud (MID), en de Dienst van identiteitskaart van de Bezoeker kunnen zien. Deze verwijzen naar [!UICONTROL Experience Cloud Identity Service]. Mogelijk ziet u ook [!UICONTROL Experience Platform Identity Service]. Ter verduidelijking:

* [!UICONTROL Experience Platform Identity Service]: De service die identiteiten koppelt. Het is de apparaat-verbinden dienst voor op mensen-gebaseerd ervaringsbeheer.
* [!UICONTROL Experience Cloud ID Service] (ECID): De unieke, permanente id die aan een sitebezoeker is toegewezen. Het is een specifieke entiteit die door de Dienst van de Identiteit van het Platform kan worden gebruikt.

Wanneer uw organisatie de id-service implementeert, kunt u met deze id dezelfde sitebezoeker en de bijbehorende gegevens identificeren in verschillende Experience Cloud-oplossingen.

![](assets/ecid-new.png)

Ook, kan de dienst van identiteitskaart de verschillende oplossing-specifieke IDs (b.v., Analytics HULP) vervangen. En via de [Klanten-id&#39;s en verificatiestatus](/help/reference/authenticated-state.md)-functionaliteit kunt u met de id-service uw eigen klant-id&#39;s doorgeven aan de Experience Cloud. Houd er echter rekening mee dat de id-service alleen werkt met de oplossingen waarop u al bent geabonneerd. Het zal geen toegang tot andere producten verlenen als u niet voor hen wordt geregistreerd.

De id-service is een integraal onderdeel van vele huidige en toekomstige functies, verbeteringen en services voor Experience Cloud. Momenteel, steunt de dienst van identiteitskaart [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html), en [Doel](http://www.adobe.com/marketing-cloud/testing-targeting.html). En dit is vereist als u wilt deelnemen aan de Adobe Experience Cloud Device Co-op. Als u de id-service niet hebt geïmplementeerd, is het nu tijd om een migratiestrategie te overwegen. Voor meer informatie over het belang en de rol van de dienst van identiteitskaart, zie [Waarom de Dienst van de Identiteit van de Experience Cloud op Uw Radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/) zou moeten zijn.

## Overzicht van functies

Samenvattend, de dienst van identiteitskaart:

* Hiermee maakt u een algemene sleutel of id die kan worden gebruikt om profielen en identiteiten te koppelen.
* Identificeert uniek een apparaat over veelvoudige oplossingen.
* Plaatst een eerstepartijkoekje in het domein van de klant om het volgen op het zelfde domein te verzekeren. Zie het document op [cookies en Experience Cloud Identity Service](./cookies.md) voor meer informatie.
* Ontvangt aliassen en identiteitskaart- afbeeldingen van de klanten en de partners van Experience Cloud.
* Beheert synchronisatie van id binnen de Experience Cloud.
* Ondersteunt synchronisatie van id&#39;s met verschillende derden in het ecosysteem van de advertentietechnologie.

## ID-servicevereisten

Uw oplossing en andere Adobe code bibliotheken moeten [bepaalde vereisten ](/help/reference/requirements.md) voldoen alvorens u de dienst van identiteitskaart kunt gebruiken.

* [Cookies en de Experience Cloud Identity Service](cookies.md): De id-service gebruikt uw organisatie-id, de Experience Cloud AMCV-cookie en een demdex-cookie om unieke, permanente id&#39;s voor uw sitebezoekers te maken en op te slaan. Deze koekjes laten de dienst van identiteitskaart bezoekers over uw verschillende domeinen volgen en gegevens toelaten delend onder verschillende oplossingen van Experience Cloud.
* [Hoe de Experience Cloud Identiteitsdienst verzoekt en identiteitskaart](id-request.md) plaatst: Een overzicht van het proces voor het aanvragen en beantwoorden van id&#39;s. Deze voorbeelden behandelen identiteitskaart taak op individuele plaatsen, over verschillende plaatsen, en voor plaatsen die door verschillende klanten van Experience Cloud met hun eigen organisatie IDs worden beheerd.
* [Identiteitssynchronisatie en gelijke tarieven](match-rates.md) begrijpen: Een overzicht van de processen van de synchronisatie van identiteitskaart en gelijke tarieven in de Dienst van de Identiteit van de Experience Cloud, met inbegrip van Adobe Media Optimizer en de dienst van identiteitskaart
