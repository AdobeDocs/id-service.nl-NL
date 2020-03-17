---
description: Sluit hun platform van het Beheer van de Toestemming (CMP) met de stop van de Manager van de Publiek van Opt-binnen voor de Transparantie en van de Toestemming van IAB Kader (TCF) aan.
seo-description: Sluit het beheerplatform voor toegang (CMP) aan op de insteekmodule Audience Manager voor IAB Transparency and Consent Framework (TCF).
seo-title: Het gebruiken van Opt-in de Diensten met IAB Kader
title: Het gebruiken van Opt-in de Diensten met IAB Kader
uuid: 8df39d9c-c016-490e-b4db-d02e4044b480
translation-type: tm+mt
source-git-commit: 5c20510d9b2174b14599eab04fb694389ff87589

---


# Het gebruiken van Opt-in de Diensten met IAB Kader{#using-opt-in-services-with-iab-framework}

Verbind het Platform van het Beheer van de Toestemming (CMP) met de Insteekmodule van de Manager van de Publiek van Opt-binnen voor IAB TCF.

De klanten van de Manager van het publiek die het Kader van de Transparantie en van de Toestemming [IAB (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) gebruiken kunnen hun Platform van het Beheer van de Toestemming (CMP) met de Insteekmodule van de Manager van het Publiek van Opt-binnen voor IAB TCF verbinden. Inschakelen is een functie die is ingesloten in de ECID JavaScript-bibliotheek en die afzonderlijke Adobe-oplossingsbibliotheken kan uitschakelen, afhankelijk van de voorkeuren van de bezoeker die in een CMP zijn ingesteld. Wanneer de insteekmodule Audience Manager voor IAB TCF is geïmplementeerd met de ECID-bibliotheek, worden de voorkeuren van bezoekers van uw IAB-compatibele CMP automatisch toegewezen aan Inschakelen. Met deze voorkeuren worden bibliotheken op basis van Audience Manager (DIL en ECID) en bijbehorende aanroepen ingeschakeld wanneer toestemming wordt ontvangen.

## Voer CMP uit die IAB steunt {#section-9fd2403b548947dbb1921ac6ff9d0c82}

Opt-In kan alleen worden geïntegreerd met de IAB-toestemming als u het volgende invult:

1. Voer CMP uit die IAB steunt en als IAB verkoper [wordt](https://vendorlist.consensu.org/vendorlist.json) geregistreerd of ontwikkelt intern CMP dat de IAB specificatie uitvoert, en als CMP met IAB Europe registreert.
1. Definieer/laad de URL `__cmp` voordat u de Adobe JS laadt.

Lees voor meer informatie de documenten van het [Interactive Advertising Bureau](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md).

## De insteekmodule Audience Manager voor IAB TCF inschakelen in uw ECID Javascript-bibliotheek {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>Inschakelen is alleen beschikbaar in ECID 4.0+

Met Adobe Experience Platform Launch kunt u zowel de plug-in Opt-in als Audience Manager voor IAB TCF voor uw site implementeren. Wanneer het toelaten van IAB voor Opt-binnen manueel, controleer om ervoor te zorgen de volgende montages aan waar binnen het voorwerp van de Bezoeker worden geplaatst:

```
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,   
  isIabContext: true   
});
```

Nadat de instellingen correct zijn geconfigureerd, worden ECID- en DIL-bibliotheken in- of uitgeschakeld, afhankelijk van de toestemmingscriteria van het CMP- en IAB-framework.

>[!IMPORTANT]
>
>Audience Manager heeft toestemming nodig voor de *doeleinden 1, 2 en 5, plus toestemming* van de leverancier om cookies te implementeren en ID-syncs te initiëren of te respecteren. Lees meer over de Plug-in van de Manager van de Audience voor IAB TCF in de documentatie van de Manager van de Audience [hier](https://docs.adobe.com/help/en/audience-manager/user-guide/overview/gdpr/aam-iab-plugin.html).

Voor meer informatie over hoe te om zowel Opt-binnen als de elektrisch toestel van de Manager van de Publiek voor IAB TCF te bevestigen, controleer gebruiksgeval nr. 4 in de bevestigingsgids [hier](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Verwante documentatie {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB Transparency and Consent Framework (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - Voor meer informatie over de IAB-standaard
* [Adobe Opt-In](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - Voor meer informatie over Opt-In, een vereiste component voor toestemmingsbeheer in Platform-oplossingen
* De Steun van het Kader van de Transparantie en van de Toestemming van IAB (TCF) [in de Manager van de Audience](https://docs.adobe.com/content/help/en/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html)
* [Uw privacyopties](https://www.adobe.com/privacy/opt-out.html#customeruse) - Een andere privacyoptie waarover uw gebruikers beschikken, is de mogelijkheid om af te zien van alle gegevensverzameling met andere wereldwijde opt-outprogramma&#39;s. Globale Opt-out heeft voorrang op de Opt-binnen en IAB controle

