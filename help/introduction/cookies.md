---
description: De id-service gebruikt uw organisatie-id, de Experience Cloud AMCV-cookie en een demdex-cookie om unieke, permanente id's voor uw sitebezoekers te maken en op te slaan. Met deze cookies kan de id-service bezoekers in uw verschillende domeinen volgen en gegevensdeling tussen verschillende Experience Cloud-oplossingen inschakelen.
keywords: playstation;ID Service
seo-description: De id-service gebruikt uw organisatie-id, de Experience Cloud AMCV-cookie en een demdex-cookie om unieke, permanente id's voor uw sitebezoekers te maken en op te slaan. Met deze cookies kan de id-service bezoekers in uw verschillende domeinen volgen en gegevensdeling tussen verschillende Experience Cloud-oplossingen inschakelen.
seo-title: Cookies en de Experience Cloud Identity Service
title: Cookies en de Experience Cloud Identity Service
uuid: c5cbd235-37ee-4605-8792-b1a991e190ad
translation-type: tm+mt
source-git-commit: 7d7ecdf65cca67539b1b63c8811a0bad04c694c3

---


# Cookies and the Experience Cloud Identity Service{#cookies-and-the-experience-cloud-id-service}

De id-service gebruikt uw organisatie-id, de Experience Cloud AMCV-cookie en een demdex-cookie om unieke, permanente id&#39;s voor uw sitebezoekers te maken en op te slaan. Met deze cookies kan de id-service bezoekers in uw verschillende domeinen volgen en gegevensdeling tussen verschillende Experience Cloud-oplossingen inschakelen.

## Cookies van ID-service {#section-f438168beaec409ab8b2cc58bd021e26}

De id-service is afhankelijk van de cookies AMCV, AMCVS en demdex voor een correcte werking. Deze cookies zijn alleen bestanden waarin gegevens worden opgeslagen die door de id-service worden gebruikt. Deze ID-servicecookies zijn niet gevaarlijk, kwaadaardig of verschillen van andere cookies van een website of service in een browser die van andere leveranciers afkomstig zijn, volgens dezelfde regels die van toepassing zijn op andere cookies van andere leveranciers. Raadpleeg de volgende secties voor meer informatie over cookies die door de ID-service worden gebruikt.

### Wat de koekjes van de Dienst van identiteitskaart kunnen doen

* Stel een unieke id voor bezoekers van uw site in en sla deze op.
* Blijf deze unieke id gebruiken, zodat de id-service gegevens kan verzamelen en delen met andere Experience Cloud-oplossingen.
* Houd gebruikers in uw domeinen bij. Nochtans, vereist dit dat u die andere domeinen bezit en de dienstcode van identiteitskaart op hen heeft wordt opgesteld.

### Wat de koekjes van de Dienst van identiteitskaart niet kunnen doen

* U kunt computervirussen opslaan, verzenden of uitvoeren.
* Heb toegang tot of bewaar persoonlijk identificeerbare informatie (PII) zoals uw e-mailadres.
* Computerhardware of -software beheren.
* Maak computers instabiel of veroorzaken prestatieproblemen.
* Houd gebruikers bij op sites die de id-service niet gebruiken.

## AMCV-cookie {#section-c55af54828dc4cce89f6118655d694c8}

De volgende kenmerken van het cookie die door de ID-service is ingesteld.

**Naam**

De naam van het AMCV-cookie volgt de syntaxis `AMCV_<variable name>@AdobeOrg`. In de naam zijn de `<variable name>` elementen plaatsaanduidingen voor een deel van uw Experience Cloud-organisatie-id. Deze id wordt doorgegeven aan de DCS door de `Visitor.getInstance` functie in de ID-servicecode.

Een volledig gevormde cookienaam zou gelijkaardig aan dit kijken:

```
AMCV_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Inhoud**

Het AMCV-cookie bevat de Experience Cloud bezoeker-id of MID. MID wordt opgeslagen in een zeer belangrijk-waardepaar dat deze syntaxis volgt, `mid|<Experience Cloud ID>`.

Een volledig gevormd zeer belangrijk-waardepaar zou gelijkaardig aan dit kijken:

```
mid|20265673158980419722735089753036633573
```

Deze permanente id maakt het delen van gegevens tussen oplossingen mogelijk.

**Domein**

Het AMCV-cookie wordt ingesteld in het domein van de eerste fabrikant van een browser. Dit betekent dat deze is ingesteld in het domein van de site die momenteel wordt bezocht door een gebruiker. Dientengevolge, kunnen de de dienstcode van identiteitskaart en andere de codebibliotheken van de Wolk van de Ervaring MID lezen die in het koekje AMCV wordt opgeslagen.

Omdat het AMCV-cookie echter is ingesteld in het domein van de eerste partij, kan het niet worden gebruikt om gebruikers in verschillende domeinen bij te houden en te identificeren. In plaats daarvan, baseert de dienst van identiteitskaart zich op organisatie ID en demdex ID om correcte MID terug te keren wanneer een plaatsbezoeker aan een verschillend domein navigeert.

## AMCVS-cookie {#section-92a9454f1ac645948f9059b9fad928bf}

**Naam**

De naam van het AMCVS-cookie volgt de syntaxis `AMCVS_####@AdobeOrg`. In de naam zijn de ###-elementen tijdelijke aanduidingen voor een deel van uw Experience Cloud-organisatie-id. Deze id wordt doorgegeven aan de DCS door `theVisitor.getInstance` functie in de ID-servicecode.

Een volledig gevormde cookienaam zou gelijkaardig aan dit kijken:

```
AMCVS_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Inhoud**

Het cookie van AMCVS fungeert als een vlag die aangeeft dat de sessie is geïnitialiseerd. De waarde is altijd `1` en wordt beëindigd wanneer de sessie is beëindigd.

**Domein**

Het cookie van AMCVS wordt ingesteld in het domein van de eerste fabrikant van een browser. Dit betekent dat deze is ingesteld in het domein van de site die momenteel wordt bezocht door een gebruiker.

![](assets/AMCVS-cookie.png)

## Demdex cookie {#section-7ff7d96d6e4141b08a84a75a63d7814c}

In de volgende tabel worden enkele belangrijke kenmerken van het demdex-cookie weergegeven en gedefinieerd.

<table id="table_18E3CAF3550E4BB6A199736AACE39202"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Kenmerk </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Naam</b> </p> </td> 
   <td colname="col2"> <p>De naam van het cookie is "demdex". </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Inhoud</b> </p> </td> 
   <td colname="col2"> <p>Het demdex-cookie bevat de demdex-id, die wordt gegenereerd door de DCS. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Domein</b> </p> </td> 
   <td colname="col2"> <p>Het demdex-cookie wordt ingesteld in het domein demdex.net van een derde in de browser. Dit domein staat los van de site die momenteel door een gebruiker wordt bezocht. </p> <p>In tegenstelling tot de eerste partij, AMCV cookie, blijven het demdex cookie en de id in verschillende domeinen bestaan. De demdex-id en uw organisatie-id zijn de algemene waarden waarmee de id-service een sitebezoeker kan retourneren en identificeren met de juiste bezoeker-id. </p> </td> 
  </tr> 
 </tbody> 
</table>

Voor verwante informatie, zie het [Begrip van Vraag aan het Domein](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)van de Index.

## De Experience Cloud-id genereren {#section-15f69c0bac394b4b9966a23fbc586d17}

De Experience Cloud ID (MID) wordt wiskundig afgeleid van uw organisatie-id en de demdex-id. Zolang deze IDs constant blijft, is het produceren van juiste MID voor een specifieke gebruiker eenvoudig een wiskundeprobleem. Met dezelfde organisatie-id en dezelfde demdex-id krijgt u telkens dezelfde MID-waarde. Dit staat de dienst van identiteitskaart toe om bezoekers over domeinen te volgen die u controleert en met de dienstcode van identiteitskaart hebt gevormd.

De id-service maakt een id terwijl de pagina wordt geladen. Tijdens dit proces, verzendt de code door de `visitorAPI.js` codebibliotheek wordt verstrekt uw organisatieidentiteitskaart in een gebeurtenisvraag naar de dienst van identiteitskaart die. De id-service maakt en retourneert de MID en een demdex-id in respectievelijk de cookies AMCV en demdex.

## Markeringen

In de volgende tabel worden vlaggen voor Experience Cloud Cookies beschreven:

| Koekje (ingesteld door) | httpOnly | Beveiligen | SameSite |
|--- |--- |--- |--- |
| demdex (http response) | Nee | Ja | &quot;Geen&quot; |
| AMCV (JavaScript) | Nee | Configureerbaar | Unset (standaard ingesteld op Lax) |
| AMCVS (JavaScript) | Nee | Configureerbaar | Unset (standaard ingesteld op Lax) |

*Opmerking: Voor informatie bij het vormen van het koekje AMCV en AMCVS met veilige attributen, zie het onderwerp voor[secureCookie](https://docs.adobe.com/content/help/en/id-service/using/id-service-api/configurations/securecookie.html).*

## Volgende stappen {#section-8db1727a63bc4ff68b495f270315d453}

Zie [Hoe de Experience Cloud Identity Service id&#39;s aanvraagt en instelt...](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a).
