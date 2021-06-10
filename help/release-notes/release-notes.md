---
description: De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van de Experience Cloud.
keywords: ID-service
title: Opmerkingen bij de release 2020
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 5%

---

# Opmerkingen bij de release Experience Cloud - 2020 {#release-notes}

De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van de Experience Cloud (ECID).

## Versie 4.6

* Markering `loadSSL` is standaard ingeschakeld. Alle oproepen aan de Dienst van de Identiteit zullen `https` door gebrek zijn.  Klanten kunnen de waarde instellen op false als ze Identity Services via hun `non-ssl`-pagina&#39;s willen bellen.
* Bijgewerkt de functie die werd gebruikt om `Internet-Explorer (IE)` versie te ontdekken, om een kwestie te bevestigen die door `ESLint` wordt gemeld.
Oplossen voor prestatieprobleem op `Internet-Explorer (IE) 11` wanneer ECID `pre-approval` optIn wordt gegeven en later wordt bijgewerkt.

## Versie 4.5

* Vanaf versie 4.5 worden lege id&#39;s die naar de methode `setCustomerIDs` zijn verzonden, door ECID afgewezen.
* Probleem verholpen die zich voordeed wanneer de optie-in is geconfigureerd als `doesOptInApply=false` en `isIabContext=true`.

Zie [Opmerkingen bij de release van Experience Cloud](https://docs.adobe.com/content/help/nl-NL/release-notes/experience-cloud/current.html) voor maandelijkse opmerkingen bij de release voor alle producten.
