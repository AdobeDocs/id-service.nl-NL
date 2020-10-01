---
title: Wijzigingen in de Google Chrome SameSite-labels
seo-title: Wijzigingen in de Google Chrome SameSite-labels
description: Documentatie voor Adobe ECID-bibliotheek (ID Service).
seo-description: Documentatie voor Adobe ECID-bibliotheek (ID Service).
translation-type: tm+mt
source-git-commit: f74a028532e95ab17f5d2e64697d69eb64e03391
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 1%

---


# Wijzigingen in de Google Chrome SameSite-labels {#google-chrome-samesite-labelling-changes}

Het attribuut SameSite vertelt browsers wanneer en hoe te om koekjes in eerste en derdescenario&#39;s in brand te steken. Het attribuut SameSite kan een van de volgende drie waarden hebben: `strict`, `lax`of `none`. Chrome, Firefox, Edge, Safari en Opera ondersteunen en `strict` sinds november 2017, terwijl deze `lax` `none` werd geïntroduceerd in 2018. Deze instelling wordt echter niet door alle oudere browsers ondersteund.

In februari 2020 heeft Google Chrome 80 uitgebracht en de standaardinstelling gewijzigd van `none` in `lax` wanneer een cookie geen specifieke waarde voor het SameSite-kenmerk heeft. Met deze instelling wordt voorkomen dat een cookie wordt gebruikt in een context van een derde, ook wel bekend als &#39;cross-site&#39;. Eventuele cookies die daaruit voortvloeien, moeten worden ingesteld op `SameSite=none` en worden gelabeld als veilig.

Cookies zonder een opgegeven waarde voor het kenmerk SameSite worden standaard ingesteld op `lax`.

Ga naar het standaarddocument [voor](https://tools.ietf.org/html/draft-ietf-httpbis-rfc6265bis-03#section-4.1) cookies voor meer informatie over de kenmerken van SameSite.

## Kenmerkwaarden van SameSite

| Waarde kenmerk SameSite | Beschrijvingen |
| ------ | ------------ |
| `strict` | Cookies met deze instelling worden alleen verzonden wanneer zowel de verwijzende pagina als de landingspagina deel uitmaken van hetzelfde domein als het cookie. |
| `lax` | Cookies met deze instelling worden alleen verzonden wanneer het domein dat wordt weergegeven in de URL van de browser overeenkomt met het domein van de cookie. Dit is de nieuwe standaardinstelling voor cookies in Chrome. |
| `none` | Cookies met deze instelling zijn beschikbaar voor externe toegang of toegang van derden, zoals &quot;naar andere sites&quot;. Vóór deze wijziging `none` was de standaardinstelling van SameSite voor cookies, zodat een cookie met deze instelling het meest op dezelfde manier werkt als de cookie traditioneel werkt. Google vereist echter dat in alle cookies met deze instelling nu de markering secure wordt opgegeven. Dit betekent dat de cookie alleen wordt gemaakt en verzonden met aanvragen via HTTPS. Alle cookies die naar andere sites verwijzen zonder de beveiligde vlag worden door Google afgewezen. |

## Wat u als Adobe Experience Cloud-klant moet weten

**Geen JavaScript-updates vereist**

Adobe-producten hebben al updates aan de serverzijde uitgebracht om cookies van derden met de juiste kenmerken in te stellen. Onze klanten hebben geen JavaScript-bibliotheekupdates nodig.

**Zorg ervoor dat eindpunten van derden HTTPS gebruiken**

Alle klanten moeten bevestigen dat hun configuratie JavaScript HTTPS voor hun vraag aan de diensten van de Adobe gebruikt. Het doel, de Audience Manager, en de Dienst van de Identiteit van de Experience Cloud (ECID) richten derdeHTTP- vraag aan hun respectieve eindpunten HTTPS om, die latentie kunnen verhogen. Dit betekent dat u uw configuratie niet hoeft te wijzigen. Klanten van analyseprogramma&#39;s moeten hun implementaties bijwerken zodat uitsluitend HTTPS wordt gebruikt, omdat omleidingen die specifiek zijn voor Analytics gegevensverlies kunnen veroorzaken.

**Juist gelabelde cookies moeten gegevens verzamelen zoals bedoeld**

Zolang cookies correct zijn gelabeld, zullen browsers geen actie ondernemen om ze te blokkeren. Consumenten hebben de mogelijkheid om bepaalde soorten cookies te blokkeren, maar dit lijkt momenteel alleen een opt-in-instelling.

**Bestaande cookies van derden zonder de bijgewerkte labels worden genegeerd**

Cookies van andere bedrijven die zijn gemaakt voordat Chrome 80 de instellingen SameSite=`none` en Secure flags ging toepassen, worden door Chrome 80 genegeerd als deze vlaggen niet aanwezig zijn.

Veel van de bestaande Adobe cookies van derden hebben deze vlaggen niet en moeten door Edge-servers worden bijgewerkt voordat gebruikers een upgrade naar Chrome 80 uitvoeren, anders gaan deze cookies verloren. De Edge-servers worden automatisch bijgewerkt wanneer gebruikers de website bezoeken waar de cookie wordt gebruikt.

De meeste Adobe-producten beschikken al over de juiste vlaggen voor cookies. De uitzondering is de implementaties van Analytics die derdegegevensinzameling gebruiken en geen ECID gebruiken. Klanten kunnen te maken krijgen met een kleine, tijdelijke toename van nieuwe bezoekers die anders bezoekers zouden hebben geretourneerd.

**Mogelijke daling van de koekjesgelijke voor bestemming en marketingplace partners (slechts Audience Manager)**

Hoewel Adobe controle heeft over het bijwerken van de cookies, kan Adobe partners niet dwingen de benodigde wijzigingen aan te brengen. De gelijke van het cookie kan voor Audience Manager klanten verminderen gebruikend bestemmingspartners of marktplaatspartners die deze updates niet hebben gemaakt.

**Analytics Friendly third-party Cookies (alleen`s_vi`cookies voor analysemogelijkheden)**

Sommige implementaties van Analytics gebruiken een alias van de NAAM van Analytics om het creëren van het `s_vi` koekje in het domein van dat CNAME toe te laten. Als de CNAME zich in hetzelfde domein bevindt als uw website, wordt dit toegewezen als een cookie van de eerste partij. Nochtans, als u veelvoudige domeinen bezit en zelfde CNAME voor gegevensinzameling over al uw domeinen gebruikt, dan zal het als derdekoekje op die andere domeinen worden aangewezen.

Als de nieuwe standaard SameSite-instelling in Chrome wordt, is de CNAME niet meer zichtbaar op andere domeinen. `lax`

Om de verandering aan te passen, stelt de Analytics nu uitdrukkelijk de waarde SameSite van `s_vi` koekje aan `lax`. Als u dit cookie wilt gebruiken in een vriendelijke context van derden, stelt u de waarde SameSite in op `none`, wat betekent dat u altijd HTTPS moet gebruiken. Neem contact op met de klantenservice om de SameSite-waarde voor uw veilige CNAME&#39;s te wijzigen.

> [!IMPORTANT] Deze actie wordt niet vereist voor klanten Analytics die ECID gebruiken, klanten die een afzonderlijke CNAME voor elk van hun domeinen gebruiken, of klanten die slechts de gegevensinzameling van de Analytics van de derde gebruiken.

## Cookies met standaardbezoeker Adobe

Alleen de algemene cookies van de bezoekersstandaard worden in de onderstaande tabel weergegeven. Raadpleeg de productspecifieke documentatie of neem contact op met uw Adobe-vertegenwoordiger voor meer cookieconfiguraties.

### ECID

| Cookie | Type | Het kenmerk SameSite | Secure, kenmerk |
| ------ | ---- | ------------------ | ---------------- |
| AMCV_##@AdobeOrg | Client-side first-party | No-value added *Chrome is default to `lax` setting | Configureerbaar |
| AMCVS_##@AdobeOrg | Client-side first-party | No-value added *Chrome is default to `lax` setting | Configureerbaar |
| s_ecid | Eerste partij op de server | SameSite==`lax` | Niet ingesteld |

### Audience Manager

| Cookie | Type | Het kenmerk SameSite | Secure, kenmerk |
| ------ | ---- | ------------------ | ---------------- |
| Demdex | Derde partij | `none` | Instellen op veilig |
| Dextp | Derde partij | `none` | Instellen op veilig |

### Analytics

| Cookie | Type | Het kenmerk SameSite | Secure, kenmerk |
| ------ | ---- | ------------------ | ---------------- |
| s_vi | <ul><li> Eerste partij aan de serverzijde bij gebruik `CNAME` </li> <li>Derden bij gebruik van 2o7.net of omtr dc.net</li></ul> | <ul><li>`lax` indien eerste partij</li> <li>`none` indien derde partij</li></ul> *Klanten kunnen de instelling via het Customer Care-ticket voor domeinen van de eerste partij bewerken* | Instellen, indien gebruiken `none` en HTTPS-aanvraag |
| s_fid | Client-side first-party | Geen toegevoegde waarde *Chrome-standaardinstellingen voor `lax` instelling | Niet ingesteld |

### Target

| Cookie | Type | Het kenmerk SameSite | Secure, kenmerk |
| ------ | ---- | ------------------ | ---------------- |
| mbox | Eerste partij | No-value added *Chrome is default to `lax` setting | Niet ingesteld |

### Ad Cloud

| Cookie | Type | Het kenmerk SameSite | Secure, kenmerk |
| ------ | ---- | ------------------ | ---------------- |
| everest_g_v2 | Derde partij | `none` *Alleen op Google Chrome- en Chromium-browsers* | Instellen, indien gebruiken `none` en HTTPS-aanvraag |
| data_adcloud | Eerste partij | No-value added *Chrome is default to `lax` setting | Niet ingesteld |
| ev_tm | Derde partij | `none` *Alleen op Google Chrome- en Chromium-browsers* | Instellen, indien gebruiken `none` en HTTPS-aanvraag |

### Bizible

| Cookie | Type | Het kenmerk SameSite | Secure, kenmerk |
| ------ | ---- | ------------------ | ---------------- |
| _buid | Derde partij | `none` | Beveiligen |

### Marketo Munchkin

| Cookie | Type | Het kenmerk SameSite | Secure, kenmerk |
| ------ | ---- | ------------------ | ---------------- |
| _mkto_trk | Client-side first-party | No-value added *Chrome is default to `lax` setting | Configureerbaar voor externe pagina&#39;s |

> !![IMPORTANT] Cookies van derden Adobe worden ingesteld op de server

Raadpleeg het document over het Google Chrome SameSite-beleid [van](https://docs.adobe.com/content/help/en/target/using/implement-target/before-implement/privacy/google-chrome-samesite-cookie-policies.html)Target voor meer informatie.