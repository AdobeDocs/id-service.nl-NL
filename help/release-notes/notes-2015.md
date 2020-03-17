---
description: Opmerkingen bij de release en updates voor 2015.
keywords: ID Service
seo-description: Opmerkingen bij de release en updates voor 2015.
seo-title: Opmerkingen bij de release 2015
title: Opmerkingen bij de release 2015
uuid: 49423699-1e0f-49e4-9135-2ae84b4f92df
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Opmerkingen bij de release 2015 {#release-notes}

Opmerkingen bij de release en updates voor 2015.

## Versie 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

november 2015

De wet ter bescherming van de online privacy van kinderen (COPPA) verbiedt online het verzamelen van persoonsgegevens van kinderen onder de 13 jaar zonder controleerbare toestemming van de ouders. Klanten die zich zorgen maken over COPPA kunnen een optionele variabele toevoegen aan hun [!DNL Experience Cloud] id-servicecode, die verhindert dat cookies worden ingesteld in het domein van derden van een browser. See [COPPA Support in the Experience Cloud Identity Service](../reference/coppa.md#concept-d7ddf81bebd74f129661fcec1ca19413). Voor versie 1.5.3 of hoger.

## Versie 1.5.2 {#section-e3c73e47539942a89b02d33061128148}

september 2015

* Probleem verholpen in de Safari-browser die ervoor zorgde dat synchronisatieservices niet werkten wanneer gebruikers cookies van derden blokkeerden. (AM-20764)
* De vraag aan de dienst van identiteitskaart omvat nu versie ID in de `d_visid_ver=` parameter. De teruggekeerde identiteitskaart helpt interne teams met het oplossen van problemen en steunkwesties. (AM-20824)

## Versie 1.5.1 {#section-f4309d7917964a748fee4bdb45bffa44}

augustus 2015

* Het probleem waarbij er geen gegevens werden gesynchroniseerd of geactiveerd, is opgelost door een ID-service. (AM-2016)
* Het probleem waarbij de id-service een meerdelig domeincookie op hoofdniveau niet correct kon instellen, is opgelost. Bijvoorbeeld, als u een domein zoals hebt, `my_company.co.uk`in sommige omstandigheden, zou de dienst van identiteitskaart een koekje in `co.uk` slechts plaatsen. (AN-104683)

   Dit betrof slechts een paar cliënten die aan *alle* volgende criteria voldeden:

   * De id-service gebruiken.
   * Een [respijtperiode ingeschakeld](../reference/analytics-reference/grace-period.md)*of *worden cookies van andere leveranciers gebruikt en gebruikers blokkeren cookies van andere leveranciers.

   * Pagina&#39;s hebben met uit meerdere delen bestaande domeinen op hoofdniveau.

Documentatieherzieningen in deze release zijn onder meer:

* [API-methoden en codebibliotheek](../library/library.md#concept-ff27497375644a898d47984aefb21c97): Inhoud en tekst zijn opnieuw ingedeeld. In de meeste gevallen krijgt elke methode een eigen pagina.
* [Vereisten voor de Experience Cloud Identity Service](../reference/requirements.md): Gereviseerde inhoud en opnieuw geordende tekst.

## Versie 1.5 {#section-db5edfa11ae143ada07a96e0ab06dc57}

juli 2015

De [!DNL Experience Cloud] id-service ondersteunt meerdere id&#39;s en verificatiestatussen. Deze wijziging verwijdert ook vervangen ondersteuning voor DPID-toewijzingen [!DNL Audience Manager] aan gebruikers-id&#39;s die door de `setCustomerIDs` functie worden gebruikt. See [Customer IDs and Authentication States](../reference/authenticated-state.md)

## Versie 1.4 {#section-f5c596f355b14da28f45c798df513572}

Mei 2015

Vanaf versie 1.4, wordt de aangewezen methode om configuratie te plaatsen overgegaan in een config voorwerp binnen als tweede parameter aan de `Visitor.getInstance` functie.

```js
var visitor = Visitor.getInstance("016D5C175213CCA80A490D05@AdobeOrg",{ 
    "loadTimeout":1000, 
    "trackingServer":"myco.sc.omtrdc.net", 
    "idSyncContainerID":80 
});
```

Zie [Experience Cloud](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd).

## Versie 1.3.5 {#section-eed4567f058f446d9a819e4682621aed}

februari 2015

Oplossing voor de afhandeling van time-out bij aanvragen voor AAM Blob en Location Hint. Nu, op een onderbreking, zal het systeem correct die gebieden leeg voor de huidige pagina verlaten en alle callbacks maken. De time-out wordt beschouwd als een foutvoorwaarde, dus probeert deze opnieuw op de volgende pagina. (AN-94473, AN-94474)

## Versie 1.3.4 {#section-bca4a3e7c05546b7af1c9ec47fdb3331}

januari 2015

Herwerkte `<head>/<body>` tag-zoekactie voor JSONP-aanvraagtagcontainer en het maken van de `<script>` `<script>` tag om rekening te houden met verschillende DOM-implementaties (HTML versus XHTML) met mogelijk andere instellingen voor hoofdlettergevoeligheid. (AN-9355)
