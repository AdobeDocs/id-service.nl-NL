---
description: Deze instructies gelden voor Target-klanten die de Experience Cloud Identity Service willen gebruiken en geen gebruik maken van Dynamic Tag Management (DTM). Wij raden u echter sterk aan DTM te gebruiken om de id-service te implementeren. DTM stroomlijnt de implementatieworkflow en zorgt automatisch voor de juiste plaatsing van code en de juiste volgorde van code.
keywords: ID-service
title: Voer de Dienst van de Identiteit Experience Cloud voor Doel uit
exl-id: 7a387e98-c8fc-4904-942a-be5e527eada2
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 1%

---

# Voer de Dienst van de Identiteit Experience Cloud voor Doel uit{#implement-the-experience-cloud-id-service-for-target}

Deze instructies gelden voor Target-klanten die de Experience Cloud Identity Service willen gebruiken en geen gebruik maken van Dynamic Tag Management (DTM). Wij raden u echter sterk aan DTM te gebruiken om de id-service te implementeren. DTM stroomlijnt de implementatieworkflow en zorgt automatisch voor de juiste plaatsing van code en de juiste volgorde van code.

>[!IMPORTANT]
>
>* [Lees de vereisten](../reference/requirements.md) voordat u begint.
>* Vorm en test deze code in een ontwikkelomgeving alvorens het in productie uit te voeren.


## Stap 1: De ID-servicecode ophalen {#section-b32ba0548aa546a79dd38be59832a53e}

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

## Stap 3: Voeg uw Experience Cloud Organisatie-id toe aan Visitor.getInstance {#section-522b1877be9243c39b222859b821f0ce}

In de `Visitor.getInstance` functie, vervangen `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` met uw [!DNL Experience Cloud] organisatie-id. Als u uw organisatie-id niet kent, kunt u deze vinden op de [!DNL Experience Cloud] beheerpagina. Zie ook: [Beheer - Core Services](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html). Uw bewerkte functie kan er ongeveer zo uitzien als het onderstaande voorbeeld.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*Niet gebruiken* Wijzig het hoofdlettergebruik van de tekens in uw organisatie-id. De id is hoofdlettergevoelig en moet precies worden gebruikt zoals opgegeven.

## Stap 4: API-code van bezoeker toevoegen aan de pagina {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

Implementeer de `VisitorAPI.js` bestand naar uw site in `<head>` -tags vóór de verwijzing naar de `mbox.js` bestand. De [!DNL Experience Cloud] De id-service moet worden uitgevoerd vóór de eerste [!DNL Target] netwerkaanroep wordt gegenereerd. Verplaats deze code naar productie na het testen en controleren.

## Stap 5: ID-servicecode testen en implementeren {#section-e81ee439bb8a4c2abea43d76f3112e9c}

U kunt als volgt testen en opstellen.

**Testen en verifiëren**

U kunt als volgt de implementatie van uw id-service testen:

* Controleer of de AMCV-cookie zich in het domein bevindt waar de pagina wordt gehost.
* Verifiëren `mboxMCGVID` verschijnt in uw [!DNL Target] en dat het de [!DNL Experience Cloud] ID (MID).

Zie [Cookies en de Experience Cloud Identity Service](../introduction/cookies.md) voor meer informatie over de AMCV-cookie en de MID.

**Implementeren**

Implementeer de code nadat deze voor het testen is geslaagd.
