---
title: Wijzigingen in Google Chrome SameSite-labels
description: Documentatie voor Adobe ECID (ID Service) bibliotheek.
exl-id: f20b25a4-c9bc-41b9-8e49-79b8424e62a0
source-git-commit: ee4b7f8df5766372034da2a76e7acb81ba2a65f0
workflow-type: tm+mt
source-wordcount: '1048'
ht-degree: 1%

---

# Wijzigingen in Google Chrome SameSite-labels {#google-chrome-samesite-labelling-changes}

Het attribuut SameSite vertelt browsers wanneer en hoe te om koekjes in eerste en derdescenario&#39;s in brand te steken. Het attribuut SameSite kan een van de volgende drie waarden hebben: `strict`, `lax` of `none` . Chrome, Firefox, Edge, Safari en Opera ondersteunen `strict` en `lax` sinds november 2017, terwijl `none` werd geïntroduceerd in 2018. Deze instelling wordt echter niet door alle oudere browsers ondersteund.

In februari 2020 heeft Google Chrome 80 uitgebracht en de standaardinstelling gewijzigd van `none` in `lax` wanneer een cookie geen opgegeven waarde voor het SameSite-kenmerk heeft. Met deze instelling wordt voorkomen dat een cookie wordt gebruikt in een context van een derde, ook wel bekend als &#39;cross-site&#39;. Eventuele cookies van derden die worden uitgevoerd, moeten op `SameSite=none` worden ingesteld en als veilig worden gelabeld.

Cookies zonder een opgegeven waarde voor het kenmerk SameSite worden standaard ingesteld op `lax` .

Bezoek het [ koekjesstandaarddocument ](https://tools.ietf.org/html/draft-ietf-httpbis-rfc6265bis-03#section-4.1) voor meer informatie over attributen SameSite.

## Kenmerkwaarden van SameSite

| Waarde kenmerk SameSite | Beschrijvingen |
| ------ | ------------ |
| `strict` | Cookies met deze instelling worden alleen verzonden wanneer zowel de verwijzende pagina als de landingspagina deel uitmaken van hetzelfde domein als het cookie. |
| `lax` | Cookies met deze instelling worden alleen verzonden wanneer het domein dat wordt weergegeven in de URL van de browser overeenkomt met het domein van de cookie. Dit is de nieuwe standaard voor cookies in Chrome. |
| `none` | Cookies met deze instelling zijn beschikbaar voor externe toegang of toegang van derden, zoals &quot;naar andere sites&quot;. Vóór deze wijziging was `none` de standaardinstelling van SameSite voor cookies, zodat een cookie met deze instelling het meest op dezelfde manier werkt als de cookie traditioneel werkt. Google vereist echter dat cookies met deze instelling nu de beveiligde vlag opgeven. Dit betekent dat de cookie alleen wordt gemaakt en verzonden met aanvragen via HTTPS. Alle cross-site cookies zonder de beveiligde vlag worden door Google geweigerd. |

## Wat u als Adobe Experience Cloud-klant moet weten

**Geen vereiste updates van JavaScript**

Producten van de Adobe hebben al updates aan de serverzijde uitgebracht om cookies van derden met de juiste kenmerken in te stellen. Onze klanten hebben geen JavaScript-bibliotheekupdates nodig.

**verzeker derde eindpunten HTTPS** gebruiken

Alle klanten moeten bevestigen dat hun configuratie van JavaScript HTTPS voor hun vraag aan de diensten van Adobe gebruikt. Het doel, de Audience Manager, en de Dienst van de Identiteit van het Experience Cloud (ECID) richten derdeHTTP- vraag aan hun respectieve eindpunten HTTPS om, die latentie kunnen verhogen. Dit betekent dat u uw configuratie niet hoeft te wijzigen. Klanten van analyseprogramma&#39;s moeten hun implementaties bijwerken zodat uitsluitend HTTPS wordt gebruikt, omdat omleidingen die specifiek zijn voor Analytics gegevensverlies kunnen veroorzaken.

**correct geëtiketteerde koekjes zouden gegevens moeten verzamelen zoals bedoeld**

Zolang cookies correct zijn gelabeld, zullen browsers geen actie ondernemen om ze te blokkeren. Consumenten hebben de mogelijkheid om bepaalde soorten cookies te blokkeren, maar dit lijkt momenteel alleen een opt-in-instelling.

**Bestaande derdekoekjes zonder de bijgewerkte etiketten zullen worden genegeerd**

De koekjes van de derde die vóór Chrome 80 begonnen werden te handhaven SameSite= `none` en veilige vlaggen zullen door Chrome 80 worden genegeerd als deze vlaggen niet aanwezig zijn.

Veel van de bestaande Adobe cookies van derden hebben deze vlaggen niet en moeten door Edge-servers worden bijgewerkt voordat gebruikers een upgrade naar Chrome 80 uitvoeren, anders gaan deze cookies verloren. De Edge-servers worden automatisch bijgewerkt wanneer gebruikers naar een website gaan waar de cookie wordt gebruikt.

De meeste Adobe producten hebben reeds de aangewezen vlaggen die aan koekjes worden toegewezen. De uitzondering is de implementaties van Analytics die derdegegevensinzameling gebruiken en geen ECID gebruiken. Klanten kunnen te maken krijgen met een kleine, tijdelijke toename van nieuwe bezoekers die anders bezoekers zouden hebben geretourneerd.

**Mogelijke daling van de koekjesgelijke voor bestemming en marktplace partners (slechts Audience Manager)**

Terwijl de Adobe controle over het bijwerken van zijn koekjes heeft, kan de Adobe partners niet dwingen om noodzakelijke veranderingen aan te brengen. De gelijke van het cookie kan voor Audience Manager klanten verminderen gebruikend bestemmingspartners of marktplaatspartners die deze updates niet hebben gemaakt.

**Analytics Friendly derdekoekjes (de koekjes van Analytics `s_vi` slechts)**

Sommige analytische implementaties gebruiken een alias van de NAAM van Analytics om het creëren van het `s_vi` koekje in het domein van die CNAME toe te laten. Als de CNAME zich in hetzelfde domein bevindt als uw website, wordt dit toegewezen als een cookie van de eerste partij. Nochtans, als u veelvoudige domeinen bezit en zelfde CNAME voor gegevensinzameling over al uw domeinen gebruikt, dan zal het als derdekoekje op die andere domeinen worden aangewezen.

Als `lax` de nieuwe standaard SameSite-instelling wordt in Chrome, is de CNAME niet meer zichtbaar op andere domeinen.

Voor deze wijziging stelt Analytics nu expliciet de SameSite-waarde van `s_vi` cookie in op `lax` . Als u deze cookie in een vriendelijke context van derden wilt gebruiken, stelt u de waarde SameSite in op `none` . Dit betekent ook dat u altijd HTTPS moet gebruiken. Neem contact op met de klantenservice om de SameSite-waarde voor uw veilige CNAME&#39;s te wijzigen.

>[!IMPORTANT]
>
>Deze actie wordt niet vereist voor klanten Analytics die ECID gebruiken, klanten die een afzonderlijke CNAME voor elk van hun domeinen gebruiken, of klanten die slechts de gegevensinzameling van de Analytics van de derde gebruiken.

## Cookies met standaardbezoeker Adoben

Alleen de algemene cookies van de bezoekersstandaard worden in de onderstaande tabel weergegeven. Raadpleeg de productspecifieke documentatie of neem contact op met uw Adobe voor meer cookieconfiguraties.

### ECID

| Cookie | Type | Het attribuut SameSite | Secure, kenmerk |
| ------ | ---- | ------------------ | ---------------- |
| AMCV_##@AdobeOrg | Client-side first-party | Geen toegevoegde waarde *Chrome standaard ingesteld op `lax` | Configureerbaar |
| AMCVS_##@AdobeOrg | Client-side first-party | Geen toegevoegde waarde *Chrome standaard ingesteld op `lax` | Configureerbaar |
| s_ecid | Eerste partij op de server | SameSite==`lax` | Niet ingesteld |

### Audience Manager

| Cookie | Type | Het attribuut SameSite | Secure, kenmerk |
| ------ | ---- | ------------------ | ---------------- |
| Demdex | Derden | `none` | Instellen op veilig |
| Dextp | Derden | `none` | Instellen op veilig |

### Analytics

| Cookie | Type | Het attribuut SameSite | Secure, kenmerk |
| ------ | ---- | ------------------ | ---------------- |
| s_vi | <ul><li> Eerste partij aan de serverzijde bij gebruik van `CNAME` </li> <li>Derden bij gebruik van 2o7.net of omtrdc.net</li></ul> | <ul><li>`lax` if first-party</li> <li>`none` als derde</li></ul> *Klanten kunnen het plaatsen via het kaartje van de Zorg van de Klant voor eerste-partijdomeinen uitgeven* | Instellen als `none` en HTTPS-aanvraag worden gebruikt |
| s_fid | Client-side first-party | Geen toegevoegde waarde *Chrome heeft standaard de instelling `lax` | Niet ingesteld |

### Target

| Cookie | Type | Het attribuut SameSite | Secure, kenmerk |
| ------ | ---- | ------------------ | ---------------- |
| mbox | Eerste partij | Geen toegevoegde waarde *Chrome standaard ingesteld op `lax` | Niet ingesteld |

### Ad Cloud

| Cookie | Type | Het attribuut SameSite | Secure, kenmerk |
| ------ | ---- | ------------------ | ---------------- |
| everest_g_v2 | Derden | `none` *slechts op Google Chrome en op chroom-Gebaseerde browsers* | Instellen als `none` en HTTPS-aanvraag worden gebruikt |
| data_adcloud | Eerste partij | Geen toegevoegde waarde *Chrome standaard ingesteld op `lax` | Niet ingesteld |
| ev_tm | Derden | `none` *slechts op Google Chrome en op chroom-Gebaseerde browsers* | Instellen als `none` en HTTPS-aanvraag worden gebruikt |

### Bizible

| Cookie | Type | Het attribuut SameSite | Secure, kenmerk |
| ------ | ---- | ------------------ | ---------------- |
| _buid | Derden | `none` | Beveiligen |

### Marketo Munchkin

| Cookie | Type | Het attribuut SameSite | Secure, kenmerk |
| ------ | ---- | ------------------ | ---------------- |
| _mkto_trk | Client-side first-party | Geen toegevoegde waarde *Chrome standaard ingesteld op `lax` | Configureerbaar voor externe pagina&#39;s |

>  Cookies van derden Adoben worden ingesteld op de server.

Voor meer informatie, zie het document op [ het beleid van Google van Chrome SameSite van het Doel {](https://experienceleague.adobe.com/docs/target-dev/developer/implementation/privacy/google-chrome-samesite-cookie-policies.html).
