---
description: Deze instructies gelden voor Target-klanten die de Experience Cloud Identity Service willen gebruiken en geen Dynamic Tag Management (DTM) gebruiken. Wij raden u echter sterk aan DTM te gebruiken om de id-service te implementeren. DTM stroomlijnt de implementatieworkflow en zorgt automatisch voor de juiste plaatsing van code en de juiste volgorde van code.
keywords: ID Service
seo-description: Deze instructies gelden voor Target-klanten die de Experience Cloud Identity Service willen gebruiken en geen Dynamic Tag Management (DTM) gebruiken. Wij raden u echter sterk aan DTM te gebruiken om de id-service te implementeren. DTM stroomlijnt de implementatieworkflow en zorgt automatisch voor de juiste plaatsing van code en de juiste volgorde van code.
seo-title: Implementeer de Experience Cloud Identity Service voor Target
title: Implementeer de Experience Cloud Identity Service voor Target
uuid: cb3581fa-4c4b-43aa-bb8e-8db85a6a1ef2
translation-type: tm+mt
source-git-commit: ddff95876722b981f22c7e3196ff2ce9b696010e
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 2%

---


# Implementeer de Experience Cloud Identity Service voor Target{#implement-the-experience-cloud-id-service-for-target}

Deze instructies gelden voor Target-klanten die de Experience Cloud Identity Service willen gebruiken en geen Dynamic Tag Management (DTM) gebruiken. Wij raden u echter sterk aan DTM te gebruiken om de id-service te implementeren. DTM stroomlijnt de implementatieworkflow en zorgt automatisch voor de juiste plaatsing van code en de juiste volgorde van code.

>[!IMPORTANT]
>
>* [Lees de vereisten](../reference/requirements.md) voordat u begint.
>* Vorm en test deze code in een ontwikkelomgeving alvorens het in productie uit te voeren.


## Stap 1: De ID-servicecode ophalen {#section-b32ba0548aa546a79dd38be59832a53e}

De [!UICONTROL ID Service] code vereist de `VisitorAPI.js` codebibliotheek. Neem contact op met de [klantenservice](https://helpx.adobe.com/marketing-cloud/contact-support.html) voor deze code.

## Stap 2: Voeg de functie Visitor.getInstance aan de code van de Dienst van identiteitskaart toe {#section-287ef2958e9f43858fe9d630ae519e22}

**Deel 1: Kopieer de functie Visitor.getInstance hieronder**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE"); 
```

**Deel 2: Functiecode toevoegen aan het bestand VisitorAPI.js**

Plaats de `Visitor.getInstance` functie aan het eind van het dossier na het codeblok. Het bewerkte bestand moet er als volgt uitzien:

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library 
 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");
```

## Stap 3: Voeg uw Experience Cloud-organisatie-id toe aan Visitor.getInstance {#section-522b1877be9243c39b222859b821f0ce}

Vervang in de `Visitor.getInstance` functie `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` door uw [!DNL Experience Cloud] organisatie-id. Als u uw organisatie-id niet kent, vindt u deze op de [!DNL Experience Cloud] beheerpagina. Zie ook, [Beleid - de Diensten](https://docs.adobe.com/content/help/nl-NL/core-services/interface/manage-users-and-products/admin-getting-started.html)van de Kern. Uw bewerkte functie kan er ongeveer zo uitzien als het onderstaande voorbeeld.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*Wijzig het hoofdlettergebruik van de tekens in uw organisatie-id niet* . De id is hoofdlettergevoelig en moet precies worden gebruikt zoals opgegeven.

## Stap 4: API-code van bezoeker toevoegen aan de pagina {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

Implementeer het `VisitorAPI.js` bestand op uw site in de `<head>` tags vóór de verwijzing naar het `mbox.js` bestand. De [!DNL Experience Cloud] dienst van identiteitskaart moet uitvoeren alvorens de eerste [!DNL Target] netwerkvraag wordt geproduceerd. Verplaats deze code naar productie na het testen en controleren.

## Stap 5: ID-servicecode testen en implementeren {#section-e81ee439bb8a4c2abea43d76f3112e9c}

U kunt als volgt testen en opstellen.

**Testen en verifiëren**

U kunt als volgt de implementatie van uw id-service testen:

* Controleer of de AMCV-cookie zich in het domein bevindt waar de pagina wordt gehost.
* Controleer of `mboxMCGVID` deze optie in uw [!DNL Target] verzoek wordt weergegeven en of deze de [!DNL Experience Cloud] id (MID) bevat.

Zie [Cookies en de Experience Cloud Identity Service](../introduction/cookies.md) voor meer informatie over de AMCV cookie en de MID.

**Implementeren**

Implementeer de code nadat deze voor het testen is geslaagd.
