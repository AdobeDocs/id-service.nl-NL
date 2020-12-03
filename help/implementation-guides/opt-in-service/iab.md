---
description: Sluit hun Platform van het Beheer van de Toestemming (CMP) met de stop van de Audience Manager van Opt-binnen voor de Transparantie en van de Toestemming van IAB Kader (TCF) aan.
seo-description: Sluit hun Platform van het Beheer van de Toestemming (CMP) met de stop van de Audience Manager voor het Kader van de Transparantie van IAB en van de Toestemming (TCF) aan.
seo-title: Het gebruiken van Opt-in de Diensten met IAB Kader
title: Het gebruiken van Opt-in de Diensten met IAB Kader
uuid: 8df39d9c-c016-490e-b4db-d02e4044b480
translation-type: tm+mt
source-git-commit: ddff95876722b981f22c7e3196ff2ce9b696010e
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 5%

---


# Het gebruiken van Opt-in de Diensten met IAB Kader{#using-opt-in-services-with-iab-framework}

>[!IMPORTANT]
>
>Het volgende document is alleen van toepassing op IAB 2.0. Gebruikers moeten versie 5.0 van Visitor.js gebruiken om met IAB 2.0 te werken.

Verbind het Platform van het Beheer van de Toestemming (CMP) met de stop van het Kader van de Transparantie en van de Toestemming van de Opt-binnen (TCF).

Adobe Audience Manager-klanten die [IAB TCF](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) gebruiken, kunnen hun CMP (Consent Management Platform) verbinden met de TCF-plug-in van Opt-in. Inschakelen is een functie die is ingesloten in de ECID JavaScript-bibliotheek en die individuele Adobe-oplossingsbibliotheken kan uitschakelen afhankelijk van de voorkeuren van de bezoeker die zijn ingesteld in een CMP. Wanneer de TCF-plug-in van Opt-in is geïmplementeerd met de ECID-bibliotheek, worden de voorkeuren van de bezoeker van uw CMP die IAB TCF ondersteunt automatisch toegewezen aan Opt-in. Deze voorkeur zal op Audience Manager gebaseerde bibliotheken (DIL en ECID) en bijbehorende vraag toelaten wanneer de toestemming wordt ontvangen.

## Voer CMP uit die IAB steunt {#section-9fd2403b548947dbb1921ac6ff9d0c82}

Opt-In kan alleen worden geïntegreerd met IAB TCF als u het volgende invult:

1. Voer CMP uit die IAB steunt en als IAB verkoper [wordt](https://vendorlist.consensu.org/vendorlist.json) geregistreerd of ontwikkelt binnen-huis CMP die IAB TCF specificatie uitvoert, en als CMP met IAB TCF registreert.
1. Definieer/laad de URL `__tcfapi` voordat u de JS Adobe laadt.

Lees voor meer informatie de documenten van het [Interactive Advertising Bureau](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/TCFv2/TCF-Implementation-Guidelines.md).

## De TCF-plug-in IAB TCF van Opt-in inschakelen in uw ECID Javascript-bibliotheek {#section-77bf1b9ed67241a59e56c21ab752e82f}

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
>Audience Manager needs consent for *Purpose 1 and Purpose 10, plus vendor consent* in order to deploy cookies and initiate or honor ID syncs. Meer informatie over de IAB TCF-plug-in van de Opt-in vindt u [hier](https://docs.adobe.com/help/en/audience-manager/user-guide/overview/gdpr/aam-iab-plugin.html)in de documentatie van de Audience Manager.

Voor meer informatie over het valideren van de TCF-plug-in van Opt-in raadpleegt u het gebruiksscenario #4 in de validatiehandleiding [hier](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Verwante documentatie {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB Transparency and Consent Framework (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - Voor meer informatie over de IAB-standaard
* [Adobe Opt-In](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - Voor meer informatie over Opt-In, een vereiste component voor toestemmingsbeheer in Platform oplossingen
* De Steun van het Kader van de Transparantie en van de Toestemming van IAB (TCF) [in Audience Manager](https://docs.adobe.com/content/help/nl-NL/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html)
* [Uw privacyopties](https://www.adobe.com/nl/privacy/opt-out.html#customeruse) - Een andere privacyoptie waarover uw gebruikers beschikken, is de mogelijkheid om zich af te melden bij het verzamelen van gegevens met andere wereldwijde opt-outprogramma&#39;s. Globale Opt-Out neemt belangrijkheid over de Opt-binnen en IAB TCF controle