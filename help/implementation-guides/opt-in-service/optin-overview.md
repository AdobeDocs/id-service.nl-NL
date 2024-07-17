---
description: Met de Inschakelen-service kunt u protocollen voor de bezoeker instellen om te bepalen of u een cookie kunt instellen op het apparaat of de browser van de gebruiker wanneer deze uw site bezoekt.
title: Opt-in-service
exl-id: 351da861-4faa-409b-b0ff-f4d2ce66700b
source-git-commit: 070390ec0534c9066d717fe52ff572f34c110137
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# Opt-in-service{#opt-in-service}

Met de Inschakelen-service kunt u protocollen voor de bezoeker instellen om te bepalen of u een cookie kunt instellen op het apparaat of de browser van de gebruiker wanneer deze uw site bezoekt.

De Inschakelen-service is een uitbreiding van de Experience Cloud-id (ECID) waarmee u kunt bepalen of en welke Experience Cloud-oplossingen cookies op webpagina&#39;s kunnen maken voordat de gebruiker hiermee akkoord gaat. Met de Inschakelen-service kunt u ook protocollen instellen om als onderdeel van uw grotere ontwerp te integreren met uw CMP (Accsent Management Platform) en bestaande systemen.

Met de Inschakelen-service kunt u opgeven of een bezoeker zich kan aanmelden bij Adobe-oplossingen tegelijk, of oplossingen in de juiste volgorde kan presenteren voor machtigingen. Zodra het goedkeuringsproces volledig is en door de klant wordt geregistreerd, kunt u de CMP bezoekersgoedkeuringen van alle oplossingen van de Adobe terugwinnen.

De open-binnen dienst wordt uitgevoerd en gevormd gemakkelijk gebruikend [ Markeringen in Adobe Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl) met de [ Opt-binnen uitbreiding ](../../implementation-guides/opt-in-service/launch.md). Het kan ook worden uitgevoerd en worden gevormd gebruikend [ DTM ](../../implementation-guides/opt-in-service/optin-dtm.md).

Zie de [ Vestiging Opt-binnen Dienst ](../../implementation-guides/opt-in-service/getting-started.md) om begonnen te worden.

>[!NOTE]
>
>Met de Inschakelen-service kunt u een systeem instellen om alleen het downloaden van Adobe cookies goed te keuren of te weigeren. Het biedt geen ondersteuning voor het verzamelen van voorkeuren voor toestemming van gebruikers en is ook geen opslagplaats voor voorkeuren.

>[!IMPORTANT]
>
>De inhoud van dit document is geen juridisch advies en is niet bedoeld ter vervanging van juridisch advies. Raadpleeg de juridische afdeling van uw bedrijf voor advies over toestemming en praktijken bij het instellen van uw aanmeldingsprocedure.

## Opt-in voor alle oplossingen voor Experiencen Cloud {#section-053e6224505542cf961896f0ca869e52}

De open-binnen dienst is een hulpmiddel om een toestemmings het kiezen binnen werkschema volgens uw eigen behoeften te bouwen, die u toestaan om een werkschema te ontwerpen om (brandmarkeringen) te reageren alvorens en nadat de toestemming van de gebruiker of uw toestemmingscontrolemechanisme wordt gegeven.

Met de functie Inschakelen kunt u toestemmingsbeheerpraktijken instellen voor Adobe-oplossingen voor:

* Vermeld of vereisten voor het verzamelen van toestemmingen in het algemeen van toepassing zijn op een gebruiker.
* Geef op welke oplossingen mogen worden gebruikt om cookies te genereren.
* Pas standaardvoorkeuren toe voor elke oplossing waarvan de categorie niet expliciet wordt geaccepteerd of geweigerd door de gebruiker.
* Trigger douanerespons die op veranderingen in de toestemmingsmontages van een gebruiker wordt gebaseerd, die u toestaan om de montages van de gebruiker te handhaven of bij te werken.

Met behulp van de Opt-in-services kunt u uw site zo configureren dat bepaalde cookies voorafgaand aan de keuze van de gebruiker met toestemming kunnen worden geladen. U kunt de Opt-in diensten voor nieuwe klanten plaatsen om koekjes toe te staan om worden geladen nadat de gebruiker toestemming geeft of nadat een keus wordt gemaakt ter beschikking wordt gesteld. U kunt de toestemming voor aanmelden ook opslaan en ophalen van het bestaande beheerplatform voor toestemming of de aanmeldingsmachtigingen opslaan in een cookie.

![](assets/Opt-in-approval.png)

De oplossingen van de Adobe kunnen dan controleren als de markering wordt goedgekeurd, aan veranderingen intekenen, en dan alle Opt-in klanten terugwinnen. De open-in dienst staat u toe om toestemmingen direct door de bibliotheken van JavaScript van de oplossing of door ECID te krijgen als uitgevoerd.
