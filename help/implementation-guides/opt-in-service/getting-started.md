---
description: Implementeer de Option-in-service als het enige referentiepunt dat wordt gebruikt door Experience Cloud-oplossingen (in Opt-in wordt aangeduid als Categorieën) om te bepalen of er al dan niet cookies moeten worden gemaakt op het apparaat van de bezoeker.
seo-description: Implementeer de Option-in-service als het enige referentiepunt dat wordt gebruikt door Experience Cloud-oplossingen (in Opt-in wordt aangeduid als Categorieën) om te bepalen of er al dan niet cookies moeten worden gemaakt op het apparaat van de bezoeker.
seo-title: Opt-in-service instellen
title: Opt-in-service instellen
uuid: f1c27139-cef2-4122-af12-c839cfc82e6e
translation-type: tm+mt
source-git-commit: 7d0df419c4af7f8a58ffa56b1176bf638bc0045b
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 0%

---


# Opt-in-service instellen{#setting-up-opt-in-service}

Implementeer de Option-in-service als het enige referentiepunt dat wordt gebruikt door Experience Cloud-oplossingen (in Opt-in wordt aangeduid als Categorieën) om te bepalen of er al dan niet cookies moeten worden gemaakt op het apparaat van de bezoeker.

De aanmeldingsservice is een JavaScript-bibliotheek die is gebundeld met Experience Cloud ID (ECID) en die bestaat in bezoeker JS in het algemene `adobe` object als het `adobe.optIn` object. Met de geïnstalleerde plug-in-service kunt u opgeven of een bezoeker zich tegelijk kan aanmelden bij Adobe-oplossingen of dat voor elke oplossing een volgnummer moet worden weergegeven. Met de functie voor het beheer van servicetoestemmingen (Opt-in) kunt u verschillende configuraties implementeren voor uw specifieke privacyvereisten.

Met de Inschakelen-service kunt u opgeven of een bezoeker zich tegelijk kan aanmelden bij Adobe-oplossingen of dat voor elke oplossing een volgnummer moet worden weergegeven. Zodra het goedkeuringsproces volledig is en door de klant wordt geregistreerd, kunnen de CMP bezoekersgoedkeuringen door alle oplossingen van Adobe worden teruggewonnen om met verwante toestemmingsvraag te antwoorden.

## Vereisten {#section-c39246f45e514c8ea9fdbe6f7ffa3ad0}

1. ECID versie 4.0.

   [Download](https://github.com/Adobe-Marketing-Cloud/id-service/releases) de nieuwste ECID-versie.

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

1. De privacyvereisten van uw bedrijf zijn specifiek voor de manier waarop u ervoor kiest om aan de GDPR-standaard te blijven voldoen. Houd er rekening mee welke bibliotheken uw privacyteams in uw bedrijf in een status vóór goedkeuring kunnen gebruiken.

Als het gebruiken van [Adobe Lancering](https://docs.adobelaunch.com/), voordeel halen uit de [Opt-in uitbreiding](../../implementation-guides/opt-in-service/launch.md) om de Opt-in dienst te vormen.

## Categorieën openen {#section-9ab0492ab4414f0ca16dc08d3a905f47}

De voorkeur van de Opt-in van een bezoeker is met betrekking tot een oplossing van Adobe Experience Cloud, waar elke oplossing als categorie wordt vertegenwoordigd. Categorieën worden opgegeven door het `adobe.OptInCategories` object waarin bijvoorbeeld de ECID-component wordt aangeduid als `adobe.OptInCategories`. `ECID`. Hieronder volgt de definitie van `adobe.OptInCategories`:

De instellingen voor Inschakelen blijven per categorie behouden, waarbij elke Experience Cloud-oplossing wordt aangeduid met een categorie:

```
adobe.OptInCategories = { 
    AAM: "aam", 
    TARGET: "target",  
    ANALYTICS: "aa", 
    ECID: "ecid", 
     
};
```

Met de Inschakelen-service kunt u de voorkeuren voor bezoekersmachtigingen instellen voor elke Adobe-oplossing die op uw site wordt gebruikt. Het omvat een bibliotheek om de montages van een bezoeker door goedgekeurde categorie te bewaren en steunt een opeenvolgende stroom, waar het goedkeuringsproces &quot;bevestigt&quot;of &quot;ontkent&quot;voorkeur voor elke categorie één voor één ontvangt. U kunt oplossingen/categorieën instellen om als geheel of als individuele oplossingen aan te melden.
De client-side bibliotheken van alle Adobe-oplossingen zijn afhankelijk van de Open-In-service en genereren geen cookies, tenzij de oplossing toestemming heeft gekregen. De optie-binnen steunt diverse benaderingen om de toestemmingsmontages voor de huidige bezoeker te verstrekken en bij te werken. Deze sectie bevat voorbeelden voor het instellen van servicevoorkeuren voor inschakelen. Zie de [Opt-in API-naslaggids](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) voor een volledige lijst met functies en parameters.

Opt-in de dienstconfiguraties worden verstrekt in de functie van JS van de Bezoeker die het globale `getInstance()` `adobe` voorwerp concretiseert. De volgende lijst maakt een lijst van de de [configuratiemontages](../../implementation-guides/opt-in-service/api.md#section-d66018342baf401389f248bb381becbf) van Bezoeker JS voor de Opt-in dienst.

**Voorbeeld van een plug-inconfiguratie bij initialisatie van het algemene `Visitor` object**

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

**Wijzigingen in toestemming verwerken**

Op elk gewenst moment tijdens de ervaring van een bezoeker op uw site kunnen deze voor het eerst voorkeuren instellen of hun voorkeuren wijzigen met uw CMP. Nadat bezoeker JS is geïnitialiseerd met initiële instellingen, kunnen de machtigingen van de bezoeker worden gewijzigd. Zie [Wijzigingen in toestemming](../../implementation-guides/opt-in-service/api.md#section-c3d85403ff0d4394bd775c39f3d001fc) voor een lijst met het beheer van toestemmingsfuncties.

<!--
<p> *** <b>sample code block </b>*** </p>
-->

## Inschakelen van workflows {#section-70cd243dec834c8ea096488640ae20a5}

De opt-in dienst steunt een werkschema waar de toestemmingen over meer dan één verzoekcyclus kunnen worden verzameld en de voorkeur wordt gegeven tegelijkertijd. Met behulp van de volgende functies en met *waar* voor `shouldWaitForComplete`als resultaat, kan uw oplossing toestemming verzamelen voor een of een subset van de totale categorieën en vervolgens toestemming verzamelen voor de volgende categorie of subset van categorieën. Beginnend op de eerste vraag, zal het `adobe.optIn.status` bezit *hangend* zijn tot `adobe.optIn.complete()` aan het eind van de stroom wordt geroepen. Zodra geroepen, wordt de status geplaatst om te *voltooien*.

```
adobe.optIn.approve(['AAM', 'ECID'], true); 
adobe.optIn.deny(['ANALYTICS'], true); 
adobe.optIn.complete();
```

Zie [Workflowconfiguratie-instellingen](../../implementation-guides/opt-in-service/api.md#section-2c5adfa5459c4e72b96d2693123a53c2).

## De aanmeldingsmachtigingen van uw bezoeker Inspect {#section-f136a9024e054d84881e6667fb7c94eb}

Wanneer uw bezoekers hun machtigingen wijzigen, hebt u inzicht in de resulterende machtigingen nodig om uw toestemmingswinkel te synchroniseren met de wijzigingen die u in de Inschakelen-service hebt aangebracht. Inspect de voorkeuren van uw bezoeker met behulp van de [machtigingsfuncties](../../implementation-guides/opt-in-service/api.md#section-7fe57279b5b44b4f8fe47e336df60155), bijvoorbeeld:

**voorbeeld met opgehaalde machtigingen**

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

Zie de [API-documentatie](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) voor meer informatie over deze en eventuele functies, eigenschappen of configuraties die in dit document worden genoemd.

## Voorkeuren bezoeker opslaan {#section-ef2884ae67e34879bf7c7c3372706c9f}

De open-in dienst verstrekt een optie om toestemmingsvoorkeur op te slaan die aan een ontwikkelomgeving of een milieu wordt aangepast waar het niet uitvoerbaar is om een CRM te gebruiken. Het specificeren van het configuratiebezit `isOptInStorageEnabled` als *ware* brengt de Opt-in dienst teweeg om een koekje op het systeem van de bezoeker binnen uw domein tot stand te brengen.

Het `adobe.optIn` object is stateless en biedt geen opslagmechanisme. Het is in plaats daarvan de bedoeling dat u de toestemmingsmontages van de Adobe in uw bestaand Platform van het Beheer van de Toestemming (CMP) beheert als het het opslaan van douanegegevens toestaat. U kunt bezoekersvoorkeuren ook in een cookie opslaan in de browser van de bezoeker. U hebt twee opties waarmee u de gebruikersvoorkeuren kunt instellen voor de aanmeldingsservice:

* Als uw oplossing voor het blijvend maken van toestemming, of het nu een CMP- of een cookie is in de browser van de bezoeker, het mogelijk maakt bezoekersvoorkeuren tijdig op te halen, kunt u deze tijdens de initialisatie van de bezoeker aan de Inschakelen-service aanbieden.
* Nochtans, als de terugwinning een langdurig proces kan zijn of anders het best als asynchroon proces wordt gediend, kunt u de `approve()` functie van de dienst gebruiken om die montages te verstrekken zodra zij met succes worden geladen.

