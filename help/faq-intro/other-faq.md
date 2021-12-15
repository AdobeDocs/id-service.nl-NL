---
description: Veelgestelde vragen over eigenschappen, functionaliteit, en kwesties met betrekking tot het gebruiken van andere oplossingen van Experience Cloud met de dienst van identiteitskaart
keywords: ID-service
title: Veelgestelde vragen voor andere Experience Cloud-oplossingen
exl-id: d1164951-01c9-4375-981a-f87d8a280e4b
source-git-commit: e171c94ccfa1f4fe9b8d909d0204adb94f20cbb6
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# Veelgestelde vragen voor andere Experience Cloud-oplossingen{#faqs-for-other-experience-cloud-solutions}

Veelgestelde vragen over eigenschappen, functionaliteit, en kwesties met betrekking tot het gebruiken van andere oplossingen van Experience Cloud met de dienst van identiteitskaart

## Analyse en Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**Zal de bezoekgeschiedenis van een gebruiker worden uitgevoerd van [!DNL Adobe Analytics] tot [!DNL Audience Manager] nadat ik de Experience Cloud Identity Service heb geïmplementeerd?**

Hier zijn twee opties:

* Als een gebruiker een bezoekende activiteit heeft nadat de Dienst van identiteitskaart wordt uitgevoerd, zijn de bezoeker en hun geschiedenis inbegrepen in de gegevensuitvoer naar [!DNL Audience Manager].
* Als een gebruiker geen bezoekende activiteit heeft nadat de Dienst van identiteitskaart wordt uitgevoerd, zullen de bezoeker en hun geschiedenis niet in de gegevensuitvoer naar Audience Manager worden omvat. Omdat er geen nieuwe activiteit aanwezig is, kunnen we de analyse-id niet koppelen aan de Experience Cloud-id.
