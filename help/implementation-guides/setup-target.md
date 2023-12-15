---
description: Deze instructies gelden voor klanten van het Doel die de identiteitsservice van het Experience Cloud willen gebruiken en geen labels voor gegevensverzameling gebruiken. Nochtans, adviseren wij sterk dat u markeringen gebruikt om de dienst van identiteitskaart uit te voeren. Met labels wordt de implementatieworkflow gestroomlijnd en wordt automatisch de juiste plaatsing van code en de juiste volgorde gegarandeerd.
keywords: ID-service
title: Voer de Dienst van de Identiteit van het Experience Cloud voor Doel uit
exl-id: 7a387e98-c8fc-4904-942a-be5e527eada2
source-git-commit: 792fb5d5192843f345577a99b6179fb6d95fedc0
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# Voer de Dienst van de Identiteit van het Experience Cloud voor Doel uit{#implement-the-experience-cloud-id-service-for-target}

Deze instructies gelden voor klanten van het Doel die de service Identiteit Experience Cloud willen gebruiken en niet [Labels voor gegevensverzameling](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en). Nochtans, adviseren wij sterk dat u markeringen gebruikt om de dienst van identiteitskaart uit te voeren. Met labels wordt de implementatieworkflow gestroomlijnd en wordt automatisch de juiste plaatsing van code en de juiste volgorde gegarandeerd.

>[!IMPORTANT]
>
>* [Lees de vereisten](../reference/requirements.md) voordat u begint.
>* Vorm en test deze code in een ontwikkelomgeving alvorens het in productie uit te voeren.

## Stap 1: Krijg de code van de Dienst van identiteitskaart {#section-b32ba0548aa546a79dd38be59832a53e}

De [!UICONTROL ID Service] vereist `VisitorAPI.js` codebibliotheek. Contact [Klantenservice](https://helpx.adobe.com/marketing-cloud/contact-support.html) om deze code op te halen.

## Stap 2: Voeg de functie Visitor.getInstance aan de code van de Dienst van identiteitskaart toe {#section-287ef2958e9f43858fe9d630ae519e22}

**Deel 1: Kopieer de functie Visitor.getInstance hieronder**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE"); 
```

**Deel 2: Functiecode toevoegen aan het bestand VisitorAPI.js**

Plaats de `Visitor.getInstance` aan het einde van het bestand na het codeblok. Het bewerkte bestand moet er als volgt uitzien:

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library 
 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");
```

## Stap 3: Voeg uw identiteitskaart van de Organisatie van het Experience Cloud aan Visitor.getInstance toe {#section-522b1877be9243c39b222859b821f0ce}

In de `Visitor.getInstance` functie, vervangen `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` met uw [!DNL Experience Cloud] organisatie-id. Als u uw organisatie-id niet kent, kunt u deze vinden op de [!DNL Experience Cloud] beheerpagina. Zie ook: [Beheer - Core Services](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html). De bewerkte functie kan er ongeveer zo uitzien als het onderstaande voorbeeld.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*Niet gebruiken* Wijzig het hoofdlettergebruik van de tekens in uw organisatie-id. De id is hoofdlettergevoelig en moet precies worden gebruikt zoals opgegeven.

## Stap 4: Bezoeker-API-code toevoegen aan de pagina {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

Implementeer de `VisitorAPI.js` bestand naar uw site in `<head>` -tags vóór de verwijzing naar de `mbox.js` bestand. De [!DNL Experience Cloud] De id-service moet worden uitgevoerd vóór de eerste [!DNL Target] netwerkaanroep wordt gegenereerd. Verplaats deze code naar productie na het testen en controleren.

## Stap 5: Test en stel de Code van de Dienst van identiteitskaart op {#section-e81ee439bb8a4c2abea43d76f3112e9c}

U kunt als volgt testen en opstellen.

**Testen en verifiëren**

U kunt als volgt de implementatie van uw id-service testen:

* Controleer of de AMCV-cookie zich in het domein bevindt waar de pagina wordt gehost.
* Verifiëren `mboxMCGVID` verschijnt in uw [!DNL Target] en dat het de [!DNL Experience Cloud] ID (MID).

Zie [Cookies en de identiteitsservice van Experiencen Cloud](../introduction/cookies.md) voor meer informatie over de AMCV-cookie en de MID.

**Implementeren**

Implementeer de code nadat deze voor het testen is geslaagd.
