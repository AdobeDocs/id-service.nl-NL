---
description: Functies worden vrijgegeven, bijgewerkt of gewijzigd in de Experience Cloud Identity Service.
keywords: ID Service
seo-description: Functies worden vrijgegeven, bijgewerkt of gewijzigd in de Experience Cloud Identity Service.
seo-title: Opmerkingen bij de release 2020
title: Opmerkingen bij de release 2020
translation-type: tm+mt
source-git-commit: c4da0f3da99a96d2be7421f49e0e88286d0505e0

---


# Opmerkingen bij de release Experience Cloud - 2020 {#release-notes}

Functies worden vrijgegeven, bijgewerkt of gewijzigd in de Experience Cloud Identity Service (ECID).

## Versie 4.6

* Markering is standaard `loadSSL` ingeschakeld. Alle vraag aan de Dienst van de Identiteit zal `https` door gebrek zijn.  De klanten kunnen het aan vals plaatsen als zij de Diensten van de Identiteit op http van hun `non-ssl` pagina&#39;s willen roepen.
* Bijgewerkt aan de functie die wordt gebruikt om een versie te detecteren, om een probleem op te lossen dat door `Internet-Explorer (IE)` `ESLint`.
Oplossing voor prestatieproblemen op het `Internet-Explorer (IE) 11` moment dat ECID de optie Aanmelden krijgt `pre-approval` en later wordt bijgewerkt.

## Versie 4.5

* Vanaf versie 4.5 worden lege id&#39;s die naar de `setCustomerIDs` methode zijn verzonden, geweigerd.
* Probleem verholpen die zich voordeed wanneer de optie-in is geconfigureerd als `doesOptInApply=false` en `isIabContext=true`.
