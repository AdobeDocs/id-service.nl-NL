---
description: De rol van de identiteitsdienst van het Experience Cloud in Adobe Experience Cloud.
title: Overzicht van Experience Cloud Identity Service
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
source-git-commit: f7c25f5ebd0690c56c081422949eb34f1f277ae1
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# Overzicht van Experience Cloud Identity Service

De dienst van de Identiteit van het Experience Cloud laat het gemeenschappelijke identificatiekader voor de Diensten van de Toepassing van het Experience Cloud toe. U kunt de Dienst van de Identiteit van het Experience Cloud gebruiken om [ identiteitskaart van het Experience Cloud (ECID) ](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html) te plaatsen.

ECID is een naamruimte voor gedeelde identiteit die in Adobe Experience Platform- en Experience Cloud-toepassingen wordt gebruikt om het gedrag van bezoekers bij te houden en ervoor te zorgen dat elk apparaat een unieke id heeft die tijdens meerdere sessies kan blijven bestaan.

>[!TIP]
>
>De Dienst van de Identiteit van het Experience Cloud, de Dienst van de Identiteit van het Experience Platform, en ECID zijn drie **verschillende** entiteiten.

De Dienst van de Identiteit van het Experience Cloud kan verschillende toepassing-specifieke IDs vervangen en de [ functionaliteit van identiteitskaartS van de Klant en van de Authentificatie van Staten ](/help/reference/authenticated-state.md) gebruiken om u binnen uw eigen klant IDs tot het Experience Cloud te laten overgaan.

>[!NOTE]
>
>De Dienst van de Identiteit van het Experience Cloud werkt slechts met de Diensten van de Toepassing van het Experience Cloud u aan wordt ingetekend en zal geen toegang tot andere toepassingsdiensten verlenen als u niet aan hen wordt ingetekend.

De Dienst van de Identiteit van het Experience Cloud steunt de volgende toepassingen:

* [ Adobe Analytics ](https://business.adobe.com/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/products/audience-manager/adobe-audience-manager.html)
* [ Adobe Target ](https://business.adobe.com/products/target/adobe-target.html)

De id-service is een integraal onderdeel van vele functies, verbeteringen en services voor huidige en toekomstige Experiencen Cloud. Momenteel, steunt de dienst van identiteitskaart [ Analytics ](http://www.adobe.com/marketing-cloud/web-analytics.html), [ Audience Manager ](http://www.adobe.com/marketing-cloud/data-management-platform.html), en [ Doel ](http://www.adobe.com/marketing-cloud/testing-targeting.html). Als u de id-service niet hebt geïmplementeerd, is het nu tijd om een migratiestrategie te overwegen.

## Overzicht van functies

Samengevat helpt de identiteitsdienst van het Experience Cloud:

* Hiermee wordt een bezoeker op een apparaat in meerdere toepassingen op unieke wijze geïdentificeerd.
* Plaatst een eerstepartijkoekje in het domein van de klant om het volgen op het zelfde domein te verzekeren. Zie het document op [ koekjes en de Dienst van de Identiteit van het Experience Cloud ](./cookies.md) voor meer informatie.
* Ontvangt aliassen en identiteitskaart- afbeeldingen van de klanten en de partners van het Experience Cloud.
* Beheert synchronisatie van id binnen het Experience Cloud.
* Ondersteunt synchronisatie van id&#39;s met verschillende derden in het ecosysteem van de advertentietechnologie.

## Vereisten voor identiteitsdienst van Experience Cloud

Uw oplossing en andere bibliotheken van de code van de Adobe moeten [ bepaalde vereisten ](/help/reference/requirements.md) ontmoeten alvorens u de Dienst van de Identiteit kunt gebruiken.

* [ Cookies en de Dienst van de Identiteit van het Experience Cloud ](cookies.md): De Dienst van de Identiteit van de Identiteit van het Experience Cloud gebruikt uw organisatie identiteitskaart, het Experience Cloud AMCV koekje, en een indexkoekje om unieke, blijvende herkenningstekens voor uw plaatsbezoekers tot stand te brengen en op te slaan. Met deze cookies kan Identity Service bezoekers in uw verschillende domeinen volgen en het delen van gegevens tussen verschillende oplossingen voor Experiencen Cloud mogelijk maken.
* [ hoe de Dienst van de Identiteit van het Experience Cloud verzoekt en plaatst IDs ](id-request.md): Een overzicht van het de verzoek en reactieproces van identiteitskaart Deze voorbeelden behandelen identiteitskaart taak op individuele plaatsen, over verschillende plaatsen, en voor plaatsen die door verschillende klanten van het Experience Cloud met hun eigen organisatie IDs worden beheerd.
* [ Begrijpend de synchronisatie van identiteitskaart en passen tarieven ](match-rates.md) aan: Een overzicht van de processen van de synchronisatie van identiteitskaart en gelijke tarieven in de Dienst van de Identiteit van het Experience Cloud, met inbegrip van Adobe Media Optimizer en de Dienst van de Identiteit.
