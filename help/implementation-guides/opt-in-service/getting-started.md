---
description: Implementeer de Option-in-service als het enige referentiepunt dat wordt gebruikt door oplossingen voor Experiencen Cloud (in Opt-in wordt de categorie Categorieën genoemd) om te bepalen of er al dan niet cookies moeten worden gemaakt op het apparaat van de bezoeker.
title: Opt-in-service instellen
exl-id: 6e8a6531-9924-4523-a842-cb4614a7a7a0
source-git-commit: 070390ec0534c9066d717fe52ff572f34c110137
workflow-type: tm+mt
source-wordcount: '913'
ht-degree: 0%

---

# Opt-in-service instellen{#setting-up-opt-in-service}

Implementeer de Option-in-service als het enige referentiepunt dat wordt gebruikt door oplossingen voor Experiencen Cloud (in Opt-in wordt de categorie Categorieën genoemd) om te bepalen of er al dan niet cookies moeten worden gemaakt op het apparaat van de bezoeker.

De Option-in-service is een JavaScript-bibliotheek die is gebundeld met Experience Cloud-id (ECID) en wordt gebruikt in bezoeker JS in het algemene `adobe` -object als het `adobe.optIn` -object. Met de geïnstalleerde plug-in-service kunt u opgeven of een bezoeker zich tegelijk kan aanmelden bij Adobe-oplossingen of dat voor elke oplossing een volgorde moet worden gebruikt waarin de juiste machtigingen worden gegeven. Met de functie voor het beheer van servicetoestemmingen (Opt-in) kunt u verschillende configuraties implementeren voor uw specifieke privacyvereisten.

Met de Inschakelen-service kunt u opgeven of een bezoeker zich tegelijk kan aanmelden bij Adobe-oplossingen of dat voor elke oplossing een volgnummer moet worden weergegeven. Zodra het goedkeuringsproces volledig is en door de klant wordt geregistreerd, kunnen de toestemmingen van de bezoeker CMP door alle oplossingen van de Adobe worden teruggewonnen om met verwante toestemmingsvraag te antwoorden.

## Vereisten {#section-c39246f45e514c8ea9fdbe6f7ffa3ad0}

1. ECID versie 4.0.

   [ Download ](https://github.com/Adobe-Marketing-Cloud/id-service/releases) de recentste versie ECID.

1. Bibliotheken ondersteunen:

   * ECID 4.0 of hoger
   * AppMeasurement 2.11 of hoger
   * DIL 9.0
   * AT.js versie 1.7.0
   * AT.js Extensie 9.0 starten
   * Voor Analytics, App Measurement 2.11 met extension 1.6
   * Voor Doel, extensie 0.9.1

1. Word goed-geverteerd in het kader van het toestemmingsbeheer dat u met Opt-in zult gebruiken en om het even welke extra voorwaarden te begrijpen.

   <!--
   For IAB, see here for additional pre-reqs.
   -->

1. De privacyvereisten van uw bedrijf zijn specifiek voor de manier waarop u ervoor kiest om te blijven voldoen aan GDPR. Houd er rekening mee welke bibliotheken uw privacyteams in uw bedrijf in een status vóór goedkeuring kunnen gebruiken.

Als het gebruiken van [ Markeringen in Adobe Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl), voordeel halen uit de [ Opt-binnen uitbreiding ](../../implementation-guides/opt-in-service/launch.md) om de Opt-binnen dienst te vormen.

## Categorieën openen {#section-9ab0492ab4414f0ca16dc08d3a905f47}

De voorkeur van de Opt-in van een bezoeker is met betrekking tot een oplossing van Adobe Experience Cloud, waar elke oplossing als categorie wordt vertegenwoordigd. Categorieën worden opgegeven door het object `adobe.OptInCategories` , waarbij de ECID-component bijvoorbeeld `adobe.OptInCategories` wordt genoemd. `ECID`. Hier volgt de definitie van `adobe.OptInCategories` :

De instellingen voor Inschakelen blijven per categorie behouden, waarbij elke oplossing van het Experience Cloud wordt aangeduid met een categorie:

```
adobe.OptInCategories = { 
    AAM: "aam", 
    TARGET: "target",  
    ANALYTICS: "aa", 
    ECID: "ecid", 
     
};
```

Met de Inschakelen-service kunt u de voorkeuren voor bezoekersmachtigingen instellen voor elke Adobe die op uw site wordt gebruikt. Het omvat een bibliotheek om de montages van een bezoeker door goedgekeurde categorie te bewaren en steunt een opeenvolgende stroom, waar het goedkeuringsproces &quot;bevestigt&quot;of &quot;ontkent&quot;voorkeur voor elke categorie één voor één ontvangt. U kunt oplossingen/categorieën instellen om als geheel of als individuele oplossingen aan te melden.
De client-side bibliotheken van alle oplossingen voor Adoben zijn afhankelijk van de Open-In-service en genereren geen cookies, tenzij aan de oplossing toestemming is verleend. De optie-binnen steunt diverse benaderingen om de toestemmingsmontages voor de huidige bezoeker te verstrekken en bij te werken. Deze sectie bevat voorbeelden voor het instellen van servicevoorkeuren voor inschakelen. Zie [ Opt-in API Verwijzing ](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) voor volledige lijst van functies en parameters.

Opt-in serviceconfiguraties worden geleverd in de JS `getInstance()` -functie van bezoeker die het algemene `adobe` -object instantieert. Het volgende maakt een lijst van de bezoeker JS [ configuratiemontages ](../../implementation-guides/opt-in-service/api.md#section-d66018342baf401389f248bb381becbf) voor de open-binnen dienst.

**Voorbeeld Opt-binnen configuratie in initialisering van het globale `Visitor` voorwerp**

```
// FORMAT: Object<adobe.OptInCategories enum: boolean> 
var preOptInApprovalsConfig = {}; 
preOptInApprovals[adobe.OptInCategories.ANALYTICS] = true; 
  
// FORMAT: Object<adobe.OptInCategories enum: boolean> 
// If you are storing the OptIn permissions on your side (in a cookie you manage or in a CMP), 
// you have to provide those permissions through the previousPermissions config. 
// previousPermissions will overwrite preOptInApprovals. 
var previousPermissionsConfig = {}; 
previousPermissionsConfig[adobe.OptInCategories.AAM] = true; 
previousPermissionsConfig[adobe.OptInCategories.ANALYTICS] = false; 
  
Visitor.getInstance("YOUR_ORG_ID", { 
    "doesOptInApply": true, // NOTE: This can be a function that evaluates to true or false. 
    "preOptInApprovals": preOptInApprovalsConfig, 
    "previousPermissions": previousPermissionsConfig, 
    "isOptInStorageEnabled": true 
});
```

**de veranderingen van het Handvat in toestemming**

Op elk gewenst moment tijdens de ervaring van een bezoeker op uw site kunnen deze voor het eerst voorkeuren instellen of hun voorkeuren wijzigen met uw CMP. Nadat bezoeker JS is geïnitialiseerd met initiële instellingen, kunnen de machtigingen van de bezoeker worden gewijzigd. Zie [ Veranderingen in Toestemming ](../../implementation-guides/opt-in-service/api.md#section-c3d85403ff0d4394bd775c39f3d001fc) voor een lijst van het beheren van toestemmingsfuncties.

<!--
<p> *** <b>sample code block </b>*** </p>
-->

## Inschakelen van workflows {#section-70cd243dec834c8ea096488640ae20a5}

De opt-in dienst steunt een werkschema waar de toestemmingen over meer dan één verzoekcyclus kunnen worden verzameld en de voorkeur wordt gegeven tegelijkertijd. Gebruikend de volgende functies en het verstrekken van *waar* voor `shouldWaitForComplete`, kan uw oplossing toestemming voor één of een ondergroep van de totale categorieën verzamelen, dan toestemmingen voor volgende of ondergroep van categorieën verzamelen. Beginnend op de eerste vraag, zal het `adobe.optIn.status` bezit *hangend* zijn tot `adobe.optIn.complete()` aan het eind van de stroom wordt geroepen. Zodra geroepen, wordt de status geplaatst aan *volledig*.

```
adobe.optIn.approve(['AAM', 'ECID'], true); 
adobe.optIn.deny(['ANALYTICS'], true); 
adobe.optIn.complete();
```

Zie [ de configuratiemontages van het Werkschema ](../../implementation-guides/opt-in-service/api.md#section-2c5adfa5459c4e72b96d2693123a53c2).

## De aanmeldingsmachtigingen van uw bezoeker Inspect {#section-f136a9024e054d84881e6667fb7c94eb}

Wanneer uw bezoekers hun machtigingen wijzigen, hebt u inzicht in de resulterende machtigingen nodig om uw toestemmingswinkel te synchroniseren met de wijzigingen die u in de Inschakelen-service hebt aangebracht. Inspect de voorkeur van uw bezoeker gebruikend de [ toestemmingenfuncties ](../../implementation-guides/opt-in-service/api.md#section-7fe57279b5b44b4f8fe47e336df60155), bijvoorbeeld:

**fetchPermissions steekproef**

```
optIn.fetchPermissions(function (permissions) { 
    // Here you can check if your category has been approved or not. 
    // We recommend using optIn.isApproved() to check for permissions because it abstracts out the details of knowing exactly how the permissions list looks like. 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
});

OR: You can pass in shouldAutoSubscribe as true, your callback will be used to subscribe to all OptIn events going forward:

function callback() { 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
}

optIn.fetchPermissions(callback, true);
```

Zie [ API documentatie ](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) voor meer details over deze en om het even welke functies, eigenschappen, of configuraties die in dit document worden vermeld.

## Voorkeuren voor bezoekers opslaan {#section-ef2884ae67e34879bf7c7c3372706c9f}

De open-in dienst verstrekt een optie om toestemmingsvoorkeur op te slaan die aan een ontwikkelomgeving of een milieu wordt aangepast waar het niet uitvoerbaar is om een CRM te gebruiken. Het specificeren van het configuratiebezit `isOptInStorageEnabled` als *waar* trekkers opent de dienst om een koekje op het systeem van de bezoeker binnen uw domein tot stand te brengen.

Het `adobe.optIn` -object is stateless en biedt geen opslagmechanisme. Het is in plaats daarvan de bedoeling dat u de instellingen voor de toestemming van de Adobe beheert in uw bestaande CMP (Consent Management Platform) als dit het opslaan van aangepaste gegevens toestaat. U kunt bezoekersvoorkeuren ook in een cookie opslaan in de browser van de bezoeker. U hebt twee opties waarmee u de gebruikersvoorkeuren kunt instellen voor de aanmeldingsservice:

* Als uw oplossing voor het blijvend maken van toestemming, of het nu een CMP- of een cookie is in de browser van de bezoeker, het mogelijk maakt bezoekersvoorkeuren tijdig op te halen, kunt u deze tijdens de initialisatie van de bezoeker aan de Inschakelen-service aanbieden.
* Als het ophalen echter een langdurig proces kan zijn of op een andere manier het beste als asynchroon proces kan worden gebruikt, kunt u de functie `approve()` van de service gebruiken om die instellingen op te geven zodra ze zijn geladen.
