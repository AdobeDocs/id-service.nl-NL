---
description: De rol van de Experience Cloud Identity Service in de Adobe Experience Cloud.
title: Overzicht van Experience Cloud-identiteitsservice
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
source-git-commit: f7c25f5ebd0690c56c081422949eb34f1f277ae1
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 1%

---

# Overzicht van Experience Cloud-identiteitsservice

De Experience Cloud Identity Service maakt het gemeenschappelijke identificatiekader voor Experience Cloud Application Services mogelijk. U kunt de Dienst van de Identiteit van de Experience Cloud gebruiken om te plaatsen [Experience Cloud-ID (ECID)](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html).

ECID is een naamruimte voor gedeelde identiteit die in Adobe Experience Platform- en Experience Cloud-toepassingen wordt gebruikt om het gedrag van bezoekers bij te houden en ervoor te zorgen dat elk apparaat een unieke id heeft die tijdens meerdere sessies kan blijven bestaan.

>[!TIP]
>
>De Experience Cloud Identiteitsdienst, de Dienst van de Identiteit van het Experience Platform, en ECID zijn drie **verschillend** entiteiten.

De Experience Cloud Identity Service kan verschillende toepassings-specifieke id&#39;s vervangen en de [Klant-id&#39;s en verificatiestatus](/help/reference/authenticated-state.md) functionaliteit zodat u uw eigen klant-id&#39;s kunt doorgeven aan de Experience Cloud.

>[!NOTE]
>
>De dienst van de Identiteit van Experience Cloud werkt slechts met de Diensten van de Toepassing van Experience Cloud die u aan wordt ingetekend en zal geen toegang tot andere toepassingsdiensten verlenen als u niet aan hen wordt ingetekend.

Experience Cloud Identity Service ondersteunt de volgende toepassingen:

* [Adobe Analytics](https://business.adobe.com/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/products/target/adobe-target.html)

De id-service is een integraal onderdeel van vele huidige en toekomstige functies, verbeteringen en services voor Experience Cloud. De id-service biedt momenteel ondersteuning voor [Analyse](http://www.adobe.com/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html), en [Doel](http://www.adobe.com/marketing-cloud/testing-targeting.html). Als u de id-service niet hebt geïmplementeerd, is het nu tijd om een migratiestrategie te overwegen.

## Overzicht van functies

Samengevat helpt de Experience Cloud Identity Service:

* Hiermee wordt een bezoeker op een apparaat in meerdere toepassingen op unieke wijze geïdentificeerd.
* Plaatst een eerstepartijkoekje in het domein van de klant om het volgen op het zelfde domein te verzekeren. Document weergeven op [cookies en Experience Cloud Identity Service](./cookies.md) voor meer informatie .
* Ontvangt aliassen en identiteitskaart- afbeeldingen van de klanten en de partners van Experience Cloud.
* Beheert synchronisatie van id binnen de Experience Cloud.
* Ondersteunt synchronisatie van id&#39;s met verschillende derden in het ecosysteem van de advertentietechnologie.

## Vereisten voor Experience Cloud-identiteitsdienst

Uw oplossing en andere Adobe code bibliotheken moeten [bepaalde eisen](/help/reference/requirements.md) voordat u identiteitsservice kunt gebruiken.

* [Cookies en de Experience Cloud Identity Service](cookies.md): De Identiteitsservice van Experience Cloud Identity Service gebruikt uw organisatie-id, de Experience Cloud AMCV-cookie en een demdex-cookie om unieke, permanente id&#39;s voor uw sitebezoekers te maken en op te slaan. Met deze cookies kan Identity Service bezoekers in uw verschillende domeinen volgen en gegevensdeling tussen verschillende Experience Cloud-oplossingen mogelijk maken.
* [Hoe de Dienst van de Identiteit van de Experience Cloud verzoekt en identiteitskaart plaatst](id-request.md): Een overzicht van het proces voor het aanvragen en beantwoorden van id&#39;s. Deze voorbeelden behandelen identiteitskaart taak op individuele plaatsen, over verschillende plaatsen, en voor plaatsen die door verschillende klanten van Experience Cloud met hun eigen organisatie IDs worden beheerd.
* [ID-synchronisatie en overeenkomsten](match-rates.md): Een overzicht van de processen van de synchronisatie van identiteitskaart en gelijke tarieven in de Dienst van de Identiteit van de Experience Cloud, met inbegrip van Adobe Media Optimizer en de Dienst van de Identiteit.
