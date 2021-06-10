---
title: Wijzigingen in de Google Chrome SameSite-labels
description: Documentatie voor Adobe ECID-bibliotheek (ID Service).
exl-id: f20b25a4-c9bc-41b9-8e49-79b8424e62a0
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '1067'
ht-degree: 1%

---

# Wijzigingen in het label van Google Chrome SameSite {#google-chrome-samesite-labelling-changes}

Het attribuut SameSite vertelt browsers wanneer en hoe te om koekjes in eerste en derdescenario&#39;s in brand te steken. Het attribuut SameSite kan een van de volgende drie waarden hebben: `strict`, `lax` of `none`. Chrome, Firefox, Edge, Safari en Opera ondersteunen `strict` en `lax` sinds november 2017, terwijl `none` in 2018 werd geïntroduceerd. Deze instelling wordt echter niet door alle oudere browsers ondersteund.

In februari 2020 heeft Google Chrome 80 uitgebracht en de standaardinstelling gewijzigd van `none` in `lax` wanneer een cookie geen opgegeven waarde voor het SameSite-kenmerk heeft. Met deze instelling wordt voorkomen dat een cookie wordt gebruikt in een context van een derde, ook wel bekend als &#39;cross-site&#39;. Eventuele cookies die daaruit voortvloeien, moeten op `SameSite=none` worden ingesteld en als veilig worden gelabeld.

Cookies zonder een opgegeven waarde voor het kenmerk SameSite worden standaard ingesteld op `lax`.

Ga naar [cookie standard document](https://tools.ietf.org/html/draft-ietf-httpbis-rfc6265bis-03#section-4.1) voor meer informatie over SameSite-kenmerken.

## Kenmerkwaarden van SameSite

| Waarde kenmerk SameSite | Beschrijvingen |
| ------ | ------------ |
| `strict` | Cookies met deze instelling worden alleen verzonden wanneer zowel de verwijzende pagina als de landingspagina deel uitmaken van hetzelfde domein als het cookie. |
| `lax` | Cookies met deze instelling worden alleen verzonden wanneer het domein dat wordt weergegeven in de URL van de browser overeenkomt met het domein van de cookie. Dit is de nieuwe standaardinstelling voor cookies in Chrome. |
| `none` | Cookies met deze instelling zijn beschikbaar voor externe toegang of toegang van derden, zoals &quot;naar andere sites&quot;. Vóór deze wijziging was `none` de standaardinstelling SameSite voor cookies. Als u deze instelling gebruikt, gedraagt een cookie zich het meest op dezelfde manier als voorheen. Google vereist echter dat in alle cookies met deze instelling nu de markering secure wordt opgegeven. Dit betekent dat de cookie alleen wordt gemaakt en verzonden met aanvragen via HTTPS. Alle cookies die naar andere sites verwijzen zonder de beveiligde vlag worden door Google afgewezen. |

## Wat u als Adobe Experience Cloud-klant moet weten

**Geen JavaScript-updates vereist**

Adobe-producten hebben al updates aan de serverzijde uitgebracht om cookies van derden met de juiste kenmerken in te stellen. Onze klanten hebben geen JavaScript-bibliotheekupdates nodig.

**Zorg ervoor dat eindpunten van derden HTTPS gebruiken**

Alle klanten moeten bevestigen dat hun configuratie JavaScript HTTPS voor hun vraag aan de diensten van de Adobe gebruikt. Het doel, de Audience Manager, en de Dienst van de Identiteit van de Experience Cloud (ECID) richten derdeHTTP- vraag aan hun respectieve eindpunten HTTPS om, die latentie kunnen verhogen. Dit betekent dat u uw configuratie niet hoeft te wijzigen. Klanten van analyseprogramma&#39;s moeten hun implementaties bijwerken zodat uitsluitend HTTPS wordt gebruikt, omdat omleidingen die specifiek zijn voor Analytics gegevensverlies kunnen veroorzaken.

**Juist gelabelde cookies moeten gegevens verzamelen zoals bedoeld**

Zolang cookies correct zijn gelabeld, zullen browsers geen actie ondernemen om ze te blokkeren. Consumenten hebben de mogelijkheid om bepaalde soorten cookies te blokkeren, maar dit lijkt momenteel alleen een opt-in-instelling.

**Bestaande cookies van derden zonder de bijgewerkte labels worden genegeerd**

Cookies van andere bedrijven die zijn gemaakt voordat Chrome 80 de SameSite=`none` ging toepassen en instellingen voor veilige vlaggen worden genegeerd door Chrome 80 als deze markeringen niet aanwezig zijn.

Veel van de bestaande Adobe cookies van derden hebben deze vlaggen niet en moeten door Edge-servers worden bijgewerkt voordat gebruikers een upgrade naar Chrome 80 uitvoeren, anders gaan deze cookies verloren. De Edge-servers worden automatisch bijgewerkt wanneer gebruikers de website bezoeken waar de cookie wordt gebruikt.

De meeste Adobe-producten beschikken al over de juiste vlaggen die aan cookies zijn toegewezen. De uitzondering is de implementaties van Analytics die derdegegevensinzameling gebruiken en geen ECID gebruiken. Klanten kunnen te maken krijgen met een kleine, tijdelijke toename van nieuwe bezoekers die anders bezoekers zouden hebben geretourneerd.

**Mogelijke daling van de koekjesgelijke voor bestemming en marketingplace partners (slechts Audience Manager)**

Hoewel Adobe controle heeft over het bijwerken van de cookies, kan Adobe partners niet dwingen de benodigde wijzigingen aan te brengen. De gelijke van het cookie kan voor Audience Manager klanten verminderen gebruikend bestemmingspartners of marktplaatspartners die deze updates niet hebben gemaakt.

**Analytics Friendly third-party Cookies (alleen analytische  `s_vi` cookies)**

Sommige implementaties van Analytics gebruiken een alias van CNAME van Analytics om het creëren van het `s_vi` koekje in het domein van die CNAME toe te laten. Als de CNAME zich in hetzelfde domein bevindt als uw website, wordt dit toegewezen als een cookie van de eerste partij. Nochtans, als u veelvoudige domeinen bezit en zelfde CNAME voor gegevensinzameling over al uw domeinen gebruikt, dan zal het als derdekoekje op die andere domeinen worden aangewezen.

Als `lax` de nieuwe standaard instelling SameSite in Chrome wordt, is de CNAME niet meer zichtbaar op andere domeinen.

Om de verandering aan te passen, stelt de Analytics nu uitdrukkelijk de waarde SameSite van `s_vi` koekje aan `lax`. Als u dit cookie wilt gebruiken in een vriendelijke context van derden, stelt u de waarde SameSite in op `none`. Dit betekent ook dat u altijd HTTPS moet gebruiken. Neem contact op met de klantenservice om de SameSite-waarde voor uw veilige CNAME&#39;s te wijzigen.

>[!IMPORTANT]
>
>Deze actie wordt niet vereist voor klanten Analytics die ECID gebruiken, klanten die een afzonderlijke CNAME voor elk van hun domeinen gebruiken, of klanten die slechts de gegevensinzameling van de Analytics van de derde gebruiken.

## Cookies met standaardbezoeker Adobe

Alleen de algemene cookies van de bezoekersstandaard worden in de onderstaande tabel weergegeven. Raadpleeg de productspecifieke documentatie of neem contact op met uw Adobe-vertegenwoordiger voor meer cookieconfiguraties.

### ECID

| Cookie | Type | Het kenmerk SameSite | Secure, kenmerk |
| ------ | ---- | ------------------ | ---------------- |
| AMCV_##@AdobeOrg | Client-side first-party | Geen toegevoegde waarde *Chrome heeft standaardinstelling `lax` | Configureerbaar |
| AMCVS_##@AdobeOrg | Client-side first-party | Geen toegevoegde waarde *Chrome heeft standaardinstelling `lax` | Configureerbaar |
| s_ecid | Eerste partij op de server | SameSite==`lax` | Niet ingesteld |

### Audience Manager

| Cookie | Type | Het kenmerk SameSite | Secure, kenmerk |
| ------ | ---- | ------------------ | ---------------- |
| Demdex | Derde partij | `none` | Instellen op veilig |
| Dextp | Derde partij | `none` | Instellen op veilig |

### Analytics

| Cookie | Type | Het kenmerk SameSite | Secure, kenmerk |
| ------ | ---- | ------------------ | ---------------- |
| s_vi | <ul><li> Server-side first-party bij gebruik van `CNAME` </li> <li>Derden bij gebruik van 2o7.net of omtr dc.net</li></ul> | <ul><li>`lax` indien eerste partij</li> <li>`none` indien derde partij</li></ul> *Klanten kunnen de instelling via het Customer Care-ticket voor domeinen van de eerste partij bewerken* | Instellen bij gebruik van `none`- en HTTPS-verzoek |
| s_fid | Client-side first-party | Geen toegevoegde waarde *Chrome standaardinstellingen `lax` | Niet ingesteld |

### Target

| Cookie | Type | Het kenmerk SameSite | Secure, kenmerk |
| ------ | ---- | ------------------ | ---------------- |
| mbox | Eerste partij | Geen toegevoegde waarde *Chrome heeft standaardinstelling `lax` | Niet ingesteld |

### Ad Cloud

| Cookie | Type | Het kenmerk SameSite | Secure, kenmerk |
| ------ | ---- | ------------------ | ---------------- |
| everest_g_v2 | Derde partij | `none` *Alleen op Google Chrome- en Chromium-browsers* | Instellen bij gebruik van `none`- en HTTPS-verzoek |
| data_adcloud | Eerste partij | Geen toegevoegde waarde *Chrome heeft standaardinstelling `lax` | Niet ingesteld |
| ev_tm | Derde partij | `none` *Alleen op Google Chrome- en Chromium-browsers* | Instellen bij gebruik van `none`- en HTTPS-verzoek |

### Bizible

| Cookie | Type | Het kenmerk SameSite | Secure, kenmerk |
| ------ | ---- | ------------------ | ---------------- |
| _buid | Derde partij | `none` | Beveiligen |

### Marketo Munchkin

| Cookie | Type | Het kenmerk SameSite | Secure, kenmerk |
| ------ | ---- | ------------------ | ---------------- |
| _mkto_trk | Client-side first-party | Geen toegevoegde waarde *Chrome heeft standaardinstelling `lax` | Configureerbaar voor externe pagina&#39;s |

> !![IMPORTANT] Cookies van derden Adobe worden ingesteld op de server

Zie het document over het Google Chrome SameSite-beleid van het doel](https://docs.adobe.com/content/help/en/target/using/implement-target/before-implement/privacy/google-chrome-samesite-cookie-policies.html) voor meer informatie.[
