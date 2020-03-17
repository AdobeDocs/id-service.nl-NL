---
description: Veelgestelde vragen over functies, functionaliteit en problemen met betrekking tot het gebruik van andere Experience Cloud-oplossingen met de id-service.
keywords: ID Service
seo-description: Veelgestelde vragen over functies, functionaliteit en problemen met betrekking tot het gebruik van andere Experience Cloud-oplossingen met de id-service.
seo-title: Veelgestelde vragen voor andere Experience Cloud-oplossingen
title: Veelgestelde vragen voor andere Experience Cloud-oplossingen
uuid: 7d848663-6cbb-4d80-ab06-7b6d2dc20e2b
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Veelgestelde vragen voor andere Experience Cloud-oplossingen{#faqs-for-other-experience-cloud-solutions}

Veelgestelde vragen over functies, functionaliteit en problemen met betrekking tot het gebruik van andere Experience Cloud-oplossingen met de id-service.

## Dynamisch tagbeheer (DTM) {#section-7ac4b9c1f1fd45a5a03eac3fb5968af7}

**Kan ik Dynamisch tagbeheer gebruiken om de service bezoekersidentiteitskaart te implementeren?**

Ja, dit is de voorkeursoptie en aanbevolen implementatieoptie.

Zie [Standaardimplementatie met DTM](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445).

## Analysebeheer en Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**Zal de bezoekgeschiedenis van een gebruiker worden uitgevoerd van[!DNL Adobe Analytics]naar[!DNL Audience Manager]nadat ik de Experience Cloud Identity Service heb geïmplementeerd?**

Hier zijn twee opties:

* Als een gebruiker een bezoekende activiteit heeft nadat de Dienst van identiteitskaart wordt uitgevoerd, zijn de bezoeker en hun geschiedenis inbegrepen in de gegevensuitvoer naar [!DNL Audience Manager].
* Als een gebruiker geen bezoekende activiteit heeft nadat de Dienst van identiteitskaart wordt uitgevoerd, zullen de bezoeker en hun geschiedenis niet in de gegevensuitvoer naar de Manager van de Publiek worden omvat. Omdat er geen nieuwe activiteit aanwezig is, kunnen we de Analytics-id niet koppelen aan de Experience Cloud-id.

