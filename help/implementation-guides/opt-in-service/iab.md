---
description: Sluit het beheerplatform voor toegang (CMP) aan op de plug-in Audience Manager van de plug-in voor IAB Transparency and Consent Framework (TCF).
title: Het gebruiken van Opt-in de Diensten met IAB Kader
exl-id: 9ac9b232-0797-4e77-a611-9cf5d17a5cb7
source-git-commit: 159b37e360b586bbada13e34793009e3067de668
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# Het gebruiken van Opt-in de Diensten met IAB Kader{#using-opt-in-services-with-iab-framework}

>[!IMPORTANT]
>
>Het volgende document is alleen van toepassing op IAB 2.0. Gebruikers moeten versie 5.0 van Visitor.js gebruiken om met IAB 2.0 te werken.

Verbind het Platform van het Beheer van de Toestemming (CMP) met de stop van het Kader van de Transparantie en van de Toestemming van de Opt-in (IAB).

De klanten die van Adobe Audience Manager [ IAB TCF ](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) gebruiken kunnen hun Platform van het Beheer van de Toestemming (CMP) met de stop van IAB TCF van opt-binnen verbinden. Inschakelen is een functie die is ingesloten in de ECID JavaScript-bibliotheek en die individuele bibliotheken met oplossingen voor Adoben kan uitschakelen, afhankelijk van de voorkeuren van de bezoeker die zijn ingesteld in een CMP. Wanneer de TCF-plug-in van Opt-in is geïmplementeerd met de ECID-bibliotheek, worden de voorkeuren van de bezoeker van uw CMP die IAB TCF ondersteunt automatisch toegewezen aan Opt-in. Deze voorkeur zal op Audience Manager gebaseerde bibliotheken (DIL en ECID) en bijbehorende vraag toelaten wanneer de toestemming wordt ontvangen.

## Voer CMP uit die IAB steunt {#section-9fd2403b548947dbb1921ac6ff9d0c82}

Opt-In kan alleen worden geïntegreerd met IAB TCF als u het volgende invult:

1. Voer CMP uit die IAB steunt en als IAB verkoper geregistreerd is, of ontwikkelt intern CMP dat de specificaties IAB TCF uitvoert, en registreert als CMP met IAB TCF.
1. Definieer of laad de `__tcfapi` voordat u de Adobe JS laadt.

Voor meer details, gelieve te lezen de [ Interactieve documenten van het Bureau van Advertising ](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/TCFv2/TCF-Implementation-Guidelines.md).

## De TCF-plug-in IAB van Opt-in inschakelen in uw ECID Javascript-bibliotheek {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>Inschakelen is alleen beschikbaar in ECID 4.0+.

Gebruik Adobe Experience Platform Launch om de TCF-plug-in van Opt-in voor uw site te implementeren. Wanneer het toelaten van IAB voor Opt-binnen manueel, controleer om ervoor te zorgen de volgende montages aan waar binnen het voorwerp van de Bezoeker worden geplaatst:

```javascript
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,
  isIabContext: true
});
```

Nadat de instellingen correct zijn geconfigureerd, worden ECID- en DIL-bibliotheken ingeschakeld/uitgeschakeld, afhankelijk van de toestemmingscriteria van de CMP en IAB TCF.

>[!IMPORTANT]
>
>De Audience Manager heeft toestemming voor *Doel 1 en Doel 10 nodig, plus verkoperstoestemming* om koekjes op te stellen en of de syncs van identiteitskaart in werking te stellen in werking te stellen of te respecteren. Lees meer over de opt-binnen insteekmodule IAB TCF in de documentatie van de Audience Manager [ hier ](https://experienceleague.adobe.com/docs/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html).

Voor meer informatie over hoe te om de stop van IAB TCF van Opt-binnen te bevestigen, controleer gebruiksgeval #4 in de bevestigingsgids [ hier ](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Verwante documentatie {#section-55da1110051a4b39b1037803f4a7b264}

* [ IAB Transparantie en het Kader van de Toestemming (TCF) ](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - voor meer informatie over de norm IAB
* [ Adobe Opt-binnen ](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - voor meer informatie over Opt-binnen, een vereiste component voor toestemmingsbeheer in de oplossingen van het Platform
* De Steun van de Transparantie en van het Kader van de Toestemming van IAB (TCF) [ in Audience Manager ](https://experienceleague.adobe.com/docs/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html)
* [ Uw Keuzen van de Privacy ](https://www.adobe.com/privacy/opt-out.html#customeruse) - Een andere privacyoptie bij de verwijdering van uw gebruikers is de capaciteit om uit alle gegevensinzameling te kiezen gebruikend andere globale opt-out hulpmiddelen. Globale Opt-Out neemt belangrijkheid over de Opt-binnen en IAB TCF controle
