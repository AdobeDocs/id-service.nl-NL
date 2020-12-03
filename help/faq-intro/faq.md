---
description: Veelgestelde vragen over functies, functionaliteit en problemen met betrekking tot het gebruik van de id-service.
keywords: ID Service
seo-description: Veelgestelde vragen over functies, functionaliteit en problemen met betrekking tot het gebruik van de id-service.
seo-title: Veelgestelde vragen over ID-service
title: Veelgestelde vragen over ID-service
uuid: e8d8f819-3d73-4fa2-864c-4867071c14ee
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 0%

---


# Veelgestelde vragen over ID-service{#id-service-faqs}

Veelgestelde vragen over functies, functionaliteit en problemen met betrekking tot het gebruik van de id-service.

## Functionaliteit {#section-659e89f8b9a74cb8afff35587dc96836}

**Welk soort functionaliteit of mogelijkheden verstrekt de dienst van identiteitskaart?**

Zie het [overzicht](../introduction/overview.md).

**Waarom doet de dienst van identiteitskaart geen vraag om identiteitskaart van de Experience Cloud terug te winnen?**

Dit kan moeilijk te diagnosticeren zijn. Eén ding dat u kunt controleren, zijn de kopteksten voor inhoudsbeveiligingsbeleid op uw site. Als u een strikt veiligheidsbeleid hebt, kunnen die montages de derdevraag blokkeren die door de dienst van identiteitskaart wordt gemaakt. Zie Beleid voor [inhoudsbeveiliging en de Experience Cloud Identity Service](../reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3).

**BezoekerAPI.js, bestandsopslag**

Er kunnen problemen optreden als u de BezoekerAPI.js host als een lokaal bestand in mobiele apps. We raden u aan het bestand op een webserver te hosten.

## Duur en vertraging bij laden van pagina {#section-c78e148d8dbe4c77a436ef0f2af5434b}

**Hoe beïnvloedt de plaatsing van de bibliotheek van BezoekerAPI.js van de dienst van identiteitskaart paginaladingstijden?**

Plaats de bibliotheek VisitorAPI.js boven aan de pagina in de `<head>` sectie van uw code. Zo weet u zeker dat de aanroep naar een id wordt uitgevoerd voordat de hoofdtekst van de pagina begint te laden en is de kans groot dat een id met succes wordt geretourneerd.

De de dienstvraag van identiteitskaart is asynchroon en is de enige vraag aan het [demdex.net domein](https://docs.adobe.com/content/help/en/audience-manager/user-guide/reference/demdex-calls.html). De de dienstvraag van identiteitskaart blokkeert geen andere elementen van het laden op de pagina.

Voor [!DNL Target] klanten, kan het plaatsen van de de dienstcode van identiteitskaart in de `<body>` pagina de kansen verhogen dat het een [!DNL Target] vraag kon blokkeren. Als u id-servicecode in de hoofdtekst van de pagina moet plaatsen, moet u deze na de open `<body>` tag plaatsen.

**Maakt de dienst van identiteitskaart een servervraag met elke paginading?**

Nee, deze aanroep zal alleen plaatsvinden wanneer de pagina voor het eerst wordt weergegeven en vervolgens om de 7 dagen. In de tussentijd zijn serveraanroepen niet vereist. De dienst van identiteitskaart werkt op cliënt-zijwijze en te hoeven niet om een servervraag te maken om een identiteitskaart terug te keren.

Zie [Overzicht](../introduction/overview.md).

**Wat kan bij het gebruik van de id-service leiden tot een trage laadtijd van de pagina of tot een nadelige invloed op de gebruikerservaring?**

Het is moeilijk om alle mogelijke voorwaarden te catalogiseren. Miljarden klanten van de consument verbinden met onze diensten en de enorme verscheidenheid in waar en hoe zij verbinden beïnvloedt prestaties. Bijvoorbeeld:

* De snelheden variëren sterk op mobiele netwerken. Deze netwerken lijden ook aan signaal en gegevens of stempakketverlies.
* Connectiviteit heeft onder verschillende omstandigheden te lijden bij apparaten die verbinding maken via WiFi. Pakketverlies en snelheidsproblemen komen bijvoorbeeld vaak voor in openbare ruimten zoals koffiewinkels of in andere omgevingen, zoals vliegtuigen, waar pakketten door een satelliet moeten stuiteren voordat ze terrestrische netwerken bereiken.
* Slecht gevormde lokale netwerken kunnen connectiviteit en snelheid negatief beïnvloeden.
* Clientapparaten kunnen hun eigen problemen hebben, zoals een te laag geheugen, een te groot aantal schijven of een beperkt CPU-vermogen ten opzichte van de huidige werklasten.
* Browsers voeren een wachtrij voor externe serveraanroepen uit en verwerken de reacties zelfs met verschillende regels, afhankelijk van de fabrikant van de browser en de versie. Dit gedrag heeft invloed op snelheid en prestaties.

**Kunt u enkele verbeteringen noemen die u hebt aangebracht om de laadtijden van de pagina te verkorten?**

Bijvoorbeeld, draad die oplevert. We introduceerden thread die resulteerde in het geval van meerdere id-synchronisatieverzoeken. Wij merkten uit laboratoriumrapporten op dat voor klanten die veelvoudige syncs uitvoeren van identiteitskaart, UI wegens veel ononderbroken berekeningen van cpu zou worden geblokkeerd. Dientengevolge, introduceerden wij draad die oplevert om de verzoeken van de synchronisatie van identiteitskaart door 100 msec elk te scheiden.

Deze wijziging verbetert de prestaties voor klanten die Visitor 2.3.0+ en DIL 6.10+ gebruiken. De verbeteringen in de laadtijden van de pagina worden weergegeven in de onderstaande afbeelding:

![](assets/id_sync_improvements_copy.png)

**Heeft het gebruik van CORS en JSON-P invloed op de prestaties van de pagina?**

De verzoeken van het middel met CORS zijn over het algemeen geschikter dan met JSONP. Met JSONP, plaatsen sommige browsers en de-rangschikt verzoeken met betrekking tot andere synchrone en asynchrone vraag op de pagina in rij. De hulp van CORS zorgt ervoor dat deze verzoeken met een hogere prioriteit in de browser vraagstapel worden behandeld.

See [CORS Support in the Experience Cloud Identity Service](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

## Beveiliging {#section-b176b8492fbe4acfb79ebb30ec902f98}

**Steunt de dienst van identiteitskaart CORS?**

Ja. See [CORS Support in the Experience Cloud Identity Service](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**Wat is CORS?**

*`Cross-Origin Resource Sharing`* Voor CORS is dit een methode die browsers gebruiken om bronnen aan te vragen. De dienst van identiteitskaart vraagt altijd middelen gebruikend CORS in browsers die het steunen. De dienst van identiteitskaart vraagt middelen met JSON-P in oudere browsers die geen CORS steunen. Zie [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**Wat als mijn veiligheidsvereisten zo strikt zijn dat ik nooit JSONP wil gebruiken?**

Als u strenge veiligheidsvereisten hebt, plaats de dienst API config van identiteitskaart `useCORSOnly: true`. Schakel deze modus alleen in als u zeker weet dat bezoekers van de site browsers gebruiken die ondersteuning bieden voor CORS.

Zie [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758) en [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa).

>[!MORELIKETHIS]
>
>* [Klantenservice](https://helpx.adobe.com/marketing-cloud/contact-support.html)

