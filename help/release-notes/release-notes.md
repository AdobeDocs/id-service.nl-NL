---
description: De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van de Experience Cloud.
keywords: ID Service
seo-description: De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van de Experience Cloud.
seo-title: Opmerkingen bij de release 2020
title: Opmerkingen bij de release 2020
translation-type: tm+mt
source-git-commit: d0057a8242dafca63101b1a2f569766bde11bea7
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 5%

---


# Experience Cloud release notes - 2020 {#release-notes}

De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van de Experience Cloud (ECID).

## Versie 4.6

* Markering is standaard `loadSSL` ingeschakeld. Alle vraag aan de Dienst van de Identiteit zal `https` door gebrek zijn.  De klanten kunnen het aan vals plaatsen als zij de Diensten van de Identiteit op http van hun `non-ssl` pagina&#39;s willen roepen.
* De functie voor het detecteren van `Internet-Explorer (IE)` versies is bijgewerkt om een probleem te verhelpen dat door `ESLint`.
Oplossing voor prestatieproblemen op het `Internet-Explorer (IE) 11` moment dat ECID de optie Aanmelden krijgt `pre-approval` en later wordt bijgewerkt.

## Versie 4.5

* Vanaf versie 4.5 worden lege id&#39;s die naar de `setCustomerIDs` methode zijn verzonden, geweigerd.
* Probleem verholpen die zich voordeed wanneer de optie-in is geconfigureerd als `doesOptInApply=false` en `isIabContext=true`.

Zie Opmerkingen [bij de release van](https://docs.adobe.com/content/help/nl-NL/release-notes/experience-cloud/current.html) Experience Cloud voor maandelijkse releases voor alle producten.
