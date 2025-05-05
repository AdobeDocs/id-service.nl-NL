---
description: De id-service gebruikt uw organisatie-id, het Experience Cloud-AMCV-cookie en een demdex-cookie om unieke, permanente id's voor uw sitebezoekers te maken en op te slaan. Deze koekjes laten de dienst van identiteitskaart bezoekers over uw verschillende domeinen volgen en gegevens toelaten die onder verschillende Experience Cloud oplossingen delen.
keywords: afspeelstation;ID-service
title: Cookies en de identiteitsservice van Experiencen Cloud
exl-id: 727c6381-56b9-44b8-8e59-355d072769be
source-git-commit: 33e467ade389144423abf14539aad8a5a5f69d21
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 0%

---

# Cookies en de identiteitsservice van Experiencen Cloud{#cookies-and-the-experience-cloud-id-service}

De id-service gebruikt uw organisatie-id, het Experience Cloud-AMCV-cookie en een demdex-cookie om unieke, permanente id&#39;s voor uw sitebezoekers te maken en op te slaan. Deze koekjes laten de dienst van identiteitskaart bezoekers over uw verschillende domeinen volgen en gegevens toelaten die onder verschillende Experience Cloud oplossingen delen.

## Cookies van ID-service {#section-f438168beaec409ab8b2cc58bd021e26}

De id-service is afhankelijk van de cookies AMCV, AMCVS en demdex voor een correcte werking. Deze cookies zijn alleen bestanden waarin gegevens worden opgeslagen die door de id-service worden gebruikt. Deze ID-servicecookies zijn niet gevaarlijk, kwaadaardig of verschillen van andere cookies van een website of service in een browser die van andere leveranciers afkomstig zijn, volgens dezelfde regels die van toepassing zijn op andere cookies van andere leveranciers. Raadpleeg de volgende secties voor meer informatie over cookies die door de ID-service worden gebruikt.

### Wat de koekjes van de Dienst van identiteitskaart kunnen doen

* Stel een unieke id in voor bezoekers van uw site (de MID) en sla deze op.
* Blijf deze unieke id gebruiken zodat de id-service gegevens kan verzamelen en delen met andere oplossingen voor Experiencen Cloud.
* Houd gebruikers in uw domeinen bij. Nochtans, vereist dit dat u die andere domeinen bezit en de dienstcode van identiteitskaart op hen heeft wordt opgesteld.

### Wat de koekjes van de Dienst van identiteitskaart niet kunnen doen

* U kunt computervirussen opslaan, verzenden of uitvoeren.
* Heb toegang tot of bewaar persoonlijk identificeerbare informatie (PII) zoals uw e-mailadres.
* Computerhardware of -software beheren.
* Maak computers instabiel of veroorzaken prestatieproblemen.
* Houd gebruikers bij op sites die de id-service niet gebruiken.

## AMCV cookie {#section-c55af54828dc4cce89f6118655d694c8}

De volgende kenmerken van het cookie die door de ID-service is ingesteld.

**Naam**

De naam van het AMCV-cookie volgt de syntaxis `AMCV_<variable name>@AdobeOrg` . In de naam zijn de `<variable name>` -elementen tijdelijke aanduidingen voor een deel van de organisatie-id van het Experience Cloud. Deze id wordt door de functie `Visitor.getInstance` in de ID-servicecode doorgegeven aan de DCS.

Een volledig gevormde cookienaam zou gelijkaardig aan dit kijken:

```
AMCV_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Inhoud**

Het AMCV-cookie bevat de Experience Cloud bezoeker-id of MID. MID wordt opgeslagen in een sleutelwaardepaar dat deze syntaxis volgt, `MCMID|<Experience Cloud ID>`.

Een volledig gevormd zeer belangrijk-waardepaar zou gelijkaardig aan dit kijken:

```
MCMID|20265673158980419722735089753036633573
```

Deze permanente id maakt het delen van gegevens tussen oplossingen mogelijk.

**Domein**

Het AMCV-cookie wordt ingesteld in het domein van de eerste fabrikant van een browser. Dit betekent dat deze is ingesteld in het domein van de site die momenteel wordt bezocht door een gebruiker. Dientengevolge, kunnen de de dienstcode van identiteitskaart en andere bibliotheken van de code van het Experience Cloud MID lezen die in het koekje AMCV wordt opgeslagen.

Omdat het AMCV-cookie echter is ingesteld in het domein van de eerste partij, kan het niet worden gebruikt om gebruikers in verschillende domeinen bij te houden en te identificeren. In plaats daarvan, baseert de dienst van identiteitskaart zich op organisatie ID en demdex ID om correcte MID terug te keren wanneer een plaatsbezoeker aan een verschillend domein navigeert.

## AMCVS-cookie {#section-92a9454f1ac645948f9059b9fad928bf}

**Naam**

De naam van het AMCVS-cookie volgt de syntaxis `AMCVS_####@AdobeOrg` . In de naam, zijn de ### elementen placeholders voor een deel van uw identiteitskaart van de organisatie van het Experience Cloud. Deze id wordt door de functie `theVisitor.getInstance` aan de DCS doorgegeven in de ID-servicecode.

Een volledig gevormde cookienaam zou gelijkaardig aan dit kijken:

```
AMCVS_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Inhoud**

Het cookie van AMCVS fungeert als een vlag die aangeeft dat de sessie is geïnitialiseerd. De waarde ervan is altijd `1` en wordt beëindigd wanneer de sessie is beëindigd.

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
   <td colname="col1"> <p> <b> Inhoud </b> </p> </td> 
   <td colname="col2"> <p>Het demdex-cookie bevat de demdex-id, die wordt gegenereerd door de DCS. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> Domein </b> </p> </td> 
   <td colname="col2"> <p>Het demdex-cookie wordt ingesteld in het domein demdex.net in de browser van een derde. Dit domein staat los van de site die momenteel door een gebruiker wordt bezocht. </p> <p>In tegenstelling tot de eerste partij, AMCV cookie, blijven het demdex cookie en de id in verschillende domeinen bestaan. De demdex-id en uw organisatie-id zijn de algemene waarden waarmee de id-service een sitebezoeker kan retourneren en identificeren met de juiste bezoeker-id. </p> </td> 
  </tr> 
 </tbody> 
</table>

Voor informatie over informatie betreffende Demdex, bezoek de [ informatie van de het apparatenopslag van de Audience Manager ](https://aam-iab-tcf-vendor.s3.amazonaws.com/aam_device_storage_disclosures.json).

Voor verwante informatie, lees de documentatie over [ het begrip Vraag aan het Domein van de Index ](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=nl-NL).

## Experience Cloud-id genereren {#section-15f69c0bac394b4b9966a23fbc586d17}

De Experience Cloud-id (MID) wordt wiskundig afgeleid van uw organisatie-id en de demdex-id. Zolang deze IDs constant blijft, is het produceren van juiste MID voor een specifieke gebruiker eenvoudig een wiskundeprobleem. Met dezelfde organisatie-id en dezelfde demdex-id krijgt u telkens dezelfde MID-waarde. Dit staat de dienst van identiteitskaart toe om bezoekers over domeinen te volgen die u controleert en met de dienstcode van identiteitskaart hebt gevormd.

De id-service maakt een id terwijl de pagina wordt geladen. Tijdens dit proces verzendt de code die door de `visitorAPI.js` codebibliotheek wordt verstrekt uw organisatie-id in een gebeurtenisvraag naar de dienst van identiteitskaart. De id-service maakt en retourneert de MID en een demdex-id in respectievelijk de cookies AMCV en demdex.

## Markeringen

In de volgende tabel worden markeringen voor Experience Cloud Cookies beschreven:

| Koekje (ingesteld door) | httpOnly | Beveiligen | SameSite |
|--- |--- |--- |--- |
| demdex (http response) | Nee | Ja | &quot;Geen&quot; |
| AMCV (JavaScript) | Nee | Configureerbaar | Unset (standaard ingesteld op Lax) |
| AMCVS (JavaScript) | Nee | Configureerbaar | Unset (standaard ingesteld op Lax) |

*Nota: Voor informatie bij het vormen van het koekje AMCV en AMCVS met veilige attributen, zie het onderwerp voor [ secureCookie ](../library/function-vars/securecookie.md).*

## Volgende stappen {#section-8db1727a63bc4ff68b495f270315d453}

Zie [ hoe de Dienst van de Identiteit van het Experience Cloud verzoekt en IDs plaatst...](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a).
