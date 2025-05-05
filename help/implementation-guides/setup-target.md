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

Deze instructies zijn voor de klanten van het Doel die de Dienst van de Identiteit van het Experience Cloud willen gebruiken en [ geen markeringen van de Inzameling van Gegevens ](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en) gebruiken. Nochtans, adviseren wij sterk dat u markeringen gebruikt om de dienst van identiteitskaart uit te voeren. Met labels wordt de implementatieworkflow gestroomlijnd en wordt automatisch de juiste plaatsing van code en de juiste volgorde gegarandeerd.

>[!IMPORTANT]
>
>* [ leest de vereisten ](../reference/requirements.md) alvorens u begint.
>* Vorm en test deze code in een ontwikkelomgeving alvorens het in productie uit te voeren.

## Stap 1: Krijg de code van de Dienst van identiteitskaart {#section-b32ba0548aa546a79dd38be59832a53e}

Voor [!UICONTROL ID Service] is de codebibliotheek van `VisitorAPI.js` vereist. De Zorg van de Klant van het contact [&#128279;](https://helpx.adobe.com/marketing-cloud/contact-support.html) &lbrace;om deze code te krijgen.

## Stap 2: Voeg de functie Visitor.getInstance aan de code van de Dienst van identiteitskaart toe {#section-287ef2958e9f43858fe9d630ae519e22}

**Deel 1: Kopieer hieronder de functie Visitor.getInstance**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE"); 
```

**Deel 2: Voeg functiecode aan het VisitorAPI.js- dossier** toe

Plaats de functie `Visitor.getInstance` aan het einde van het bestand na het codeblok. Het bewerkte bestand moet er als volgt uitzien:

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

Vervang `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` in de functie [!DNL Experience Cloud] door uw organisatie-id. `Visitor.getInstance` Als u uw organisatie-id niet kent, vindt u deze op de beheerpagina van [!DNL Experience Cloud] . Zie ook, [ Beleid - de Diensten van de Kern ](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html). De bewerkte functie kan er ongeveer zo uitzien als het onderstaande voorbeeld.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*verander niet* het geval van de karakters in uw organisatieidentiteitskaart De id is hoofdlettergevoelig en moet precies worden gebruikt zoals opgegeven.

## Stap 4: Bezoeker-API-code toevoegen aan de pagina {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

Implementeer het bestand `VisitorAPI.js` in de tags `<head>` vóór de verwijzing naar het bestand `mbox.js` naar uw site. De [!DNL Experience Cloud] ID-service moet worden uitgevoerd voordat de eerste [!DNL Target] -netwerkaanroep wordt gegenereerd. Verplaats deze code naar productie na het testen en controleren.

## Stap 5: Test en stel de Code van de Dienst van identiteitskaart op {#section-e81ee439bb8a4c2abea43d76f3112e9c}

U kunt als volgt testen en opstellen.

**Test en verifieer**

U kunt als volgt de implementatie van uw id-service testen:

* Controleer of de AMCV-cookie zich in het domein bevindt waar de pagina wordt gehost.
* Controleer of `mboxMCGVID` wordt weergegeven in uw [!DNL Target] -aanvraag en of deze de [!DNL Experience Cloud] ID (MID) bevat.

Zie [ Cookies en de Dienst van de Identiteit van het Experience Cloud ](../introduction/cookies.md) voor informatie over het koekje AMCV en MID.

**opstellen**

Implementeer de code nadat deze voor het testen is geslaagd.
