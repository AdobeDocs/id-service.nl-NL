---
description: Opmerkingen bij de release en updates voor 2015.
keywords: ID-service
title: Opmerkingen bij de release 2015
exl-id: 57c45726-f856-4af5-a30a-9a1bdcaa6411
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 3%

---

# Opmerkingen bij de release 2015 {#release-notes}

Opmerkingen bij de release en updates voor 2015.

## Versie 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

november 2015

De wet ter bescherming van de online privacy van kinderen (COPPA) verbiedt online het verzamelen van persoonsgegevens van kinderen onder de 13 jaar zonder controleerbare toestemming van de ouders. Klanten die zich zorgen maken over COPPA, kunnen een optionele variabele toevoegen aan hun [!DNL Experience Cloud] ID-servicecode, die voorkomt dat cookies in het domein van derden van een browser worden ingesteld. Zie [ Steun COPPA in de Dienst van de Identiteit van het Experience Cloud ](../reference/coppa.md#concept-d7ddf81bebd74f129661fcec1ca19413). Voor versie 1.5.3 of hoger.

## Versie 1.5.2 {#section-e3c73e47539942a89b02d33061128148}

september 2015

* Probleem verholpen in de Safari-browser die ervoor zorgde dat synchronisatieservices niet werkten wanneer gebruikers cookies van derden blokkeerden. (AAM-20764)
* Oproepen aan de dienst van identiteitskaart omvatten nu versie ID in de `d_visid_ver=` parameter. De teruggekeerde identiteitskaart helpt interne teams met het oplossen van problemen en steunkwesties. (AAM-20824)

## Versie 1.5.1 {#section-f4309d7917964a748fee4bdb45bffa44}

augustus 2015

* Het probleem waarbij er geen gegevens werden gesynchroniseerd of geactiveerd, is opgelost door een ID-service. (AAM-20164)
* Het probleem waarbij de id-service een meerdelig domeincookie op hoofdniveau niet correct kon instellen, is opgelost. Als u bijvoorbeeld een domein als `my_company.co.uk` hebt, stelt de id-service onder bepaalde omstandigheden alleen een cookie in `co.uk` . (AN-104683)

  Dit beïnvloedde slechts een paar cliënten die *alle* van de volgende criteria voldeden:

   * De id-service gebruiken.
   * Toegelaten periode van de a [ respijtperiode ](../reference/analytics-reference/grace-period.md)*of* gebruiken eerderangs en de gebruikers blokkeren derdekoekjes.

   * Pagina&#39;s hebben met uit meerdere delen bestaande domeinen op hoofdniveau.

Documentatieherzieningen in deze release zijn onder meer:

* [ API Methoden en de Bibliotheek van de Code ](../library/library.md#concept-ff27497375644a898d47984aefb21c97): Herorganiseerde inhoud en tekst. In de meeste gevallen krijgt elke methode een eigen pagina.
* [ Vereisten voor de Dienst van de Identiteit van het Experience Cloud ](../reference/requirements.md): Herziene inhoud en herorganiseerde tekst.

## Versie 1.5 {#section-db5edfa11ae143ada07a96e0ab06dc57}

juli 2015

De [!DNL Experience Cloud] ID-service ondersteunt meerdere id&#39;s en verificatiestatussen. Deze wijziging verwijdert ook vervangen ondersteuning voor [!DNL Audience Manager] DPID-toewijzingen aan gebruikers-id&#39;s die door de functie `setCustomerIDs` worden gebruikt. Zie [ identiteitskaart van de Klant en de Staten van de Authentificatie ](../reference/authenticated-state.md)

## Versie 1.4 {#section-f5c596f355b14da28f45c798df513572}

Mei 2015

Vanaf versie 1.4 geeft de voorkeursmethode voor het instellen van de configuratie een config-object door als de tweede parameter aan de functie `Visitor.getInstance` .

```js
var visitor = Visitor.getInstance("016D5C175213CCA80A490D05@AdobeOrg",{ 
    "loadTimeout":1000, 
    "trackingServer":"myco.sc.omtrdc.net", 
    "idSyncContainerID":80 
});
```

Zie [ Experience Cloud ](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd).

## Versie 1.3.5 {#section-eed4567f058f446d9a819e4682621aed}

februari 2015

Oplossing voor de afhandeling van time-out bij aanvragen voor AAM blob en Locatiehint. Nu, op een onderbreking, zal het systeem correct die gebieden leeg voor de huidige pagina verlaten en alle callbacks maken. De time-out wordt beschouwd als een foutvoorwaarde, dus probeert deze opnieuw op de volgende pagina. (AN-94473, AN-94474)

## Versie 1.3.4 {#section-bca4a3e7c05546b7af1c9ec47fdb3331}

januari 2015

De tag `<head>/<body>` is opnieuw gevonden voor JSONP request `<script>` -tagcontainer en de tag `<script>` is gemaakt voor verschillende DOM-implementaties (HTML versus XHTML) met mogelijk andere instellingen voor hoofdlettergevoeligheid. (AN-9355)
