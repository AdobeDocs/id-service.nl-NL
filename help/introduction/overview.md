---
description: De rol van de Experience Cloud Identity-service in de Adobe Experience Cloud.
seo-description: Met de Experience Cloud Identity Service (voorheen Bezoeker ID-service of Marketing Cloud ID-service) beschikt u over het gemeenschappelijke identificatiekader voor de Experience Cloud-services, zoals klantkenmerken en publiek.
seo-title: Overzicht van Experience Cloud ID Service
title: Overzicht van Experience Cloud ID Service
translation-type: tm+mt
source-git-commit: 98b72f87b188debd6a5f6b86822c3f714647de61

---


# Overzicht van Experience Cloud ID Service

Het [!UICONTROL Experience Cloud Identity Service] biedt het gemeenschappelijke identificatiekader voor Experience Cloud Core Services (zoals klantkenmerken en publiek)-oplossingen in de Experience Platform Identity Service.

>[!NOTE]
>
> Verwijzingen naar de id-service worden mogelijk als acroniemen of voormalige namen weergegeven, zoals ECID, Marketing Cloud ID Service (MID) en Bezoekersidentiteitsservice. Deze verwijzen naar de [!UICONTROL Experience Cloud Identity Service]. Je ziet misschien ook [!UICONTROL Experience Platform Identity Service]. Ter verduidelijking:

* [!UICONTROL Experience Platform Identity Service]: De service die identiteiten koppelt. Het is de apparaat-verbinden dienst voor op mensen-gebaseerd ervaringsbeheer.
* [!UICONTROL Experience Cloud ID Service] (ECID): De unieke, permanente id die aan een sitebezoeker is toegewezen. Het is een specifieke entiteit die door de Dienst van de Identiteit van het Platform kan worden gebruikt.

Wanneer uw organisatie de id-service implementeert, kunt u met deze id dezelfde sitebezoeker en hun gegevens identificeren in verschillende Experience Cloud-oplossingen.

![](assets/ecid-new.png)

Ook, kan de dienst van identiteitskaart de verschillende oplossing-specifieke IDs (b.v., Analytics HULP) vervangen. En via de [klant-id&#39;s en de verificatiestatus](/help/reference/authenticated-state.md) kunt u met de id-service uw eigen klant-id&#39;s doorgeven aan de Experience Cloud. Houd er echter rekening mee dat de id-service alleen werkt met de oplossingen waarop u al bent geabonneerd. Het zal geen toegang tot andere producten verlenen als u niet voor hen wordt geregistreerd.

De id-service is een integraal onderdeel van vele functies, verbeteringen en services van de Experience Cloud. Momenteel ondersteunt de id-service [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html)en [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html). En dit is vereist als u wilt deelnemen aan de Adobe Experience Cloud Device Co-op. Als u de id-service niet hebt geïmplementeerd, is het nu tijd om een migratiestrategie te overwegen. Voor meer informatie over het belang en de rol van de dienst van identiteitskaart, zie [waarom de Dienst van de Identiteit van de Ervaring Cloud op Uw Radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/)zou moeten zijn.

## Overzicht van functies

Samenvattend, de dienst van identiteitskaart:

* Hiermee maakt u een algemene sleutel of id die kan worden gebruikt om profielen en identiteiten te koppelen.
* Identificeert een apparaat uniek over veelvoudige oplossingen.
* Plaatst een eerstepartijkoekje in het domein van de klant om het volgen op het zelfde domein te verzekeren. Raadpleeg het document over [cookies en Experience Cloud Identity Service](https://docs.adobe.com/content/help/en/id-service/using/intro/cookies.html) voor meer informatie.
* Ontvangt aliassen en id-toewijzingen van Experience Cloud-klanten en -partners.
* Beheert synchronisatie van id&#39;s in de Experience Cloud.
* Ondersteunt synchronisatie van id&#39;s met verschillende derden in het ecosysteem van de advertentietechnologie.

## ID-servicevereisten

Uw oplossing en andere Adobe-codebibliotheken moeten aan [bepaalde vereisten](/help/reference/requirements.md) voldoen voordat u de id-service kunt gebruiken.

* [Cookies en de Experience Cloud Identity Service](cookies.md): De id-service gebruikt uw organisatie-id, de Experience Cloud AMCV-cookie en een demdex-cookie om unieke, permanente id&#39;s voor uw sitebezoekers te maken en op te slaan. Met deze cookies kan de id-service bezoekers in uw verschillende domeinen volgen en gegevensdeling tussen verschillende Experience Cloud-oplossingen inschakelen.
* [Hoe de Experience Cloud Identity Service id&#39;s aanvraagt en instelt](id-request.md): Een overzicht van het proces voor het aanvragen en beantwoorden van id&#39;s. Deze voorbeelden hebben betrekking op id-toewijzing op afzonderlijke sites, op verschillende sites en voor sites die worden beheerd door verschillende Experience Cloud-klanten met hun eigen organisatie-id&#39;s.
* [Identiteitssynchronisatie en gelijke tarieven](match-rates.md)begrijpen: Een overzicht van de processen en overeenkomsten voor id-synchronisatie in de Experience Cloud Identity Service, inclusief Adobe Media Optimizer en de ID-service.
