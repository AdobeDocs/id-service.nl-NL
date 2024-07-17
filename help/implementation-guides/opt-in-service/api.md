---
description: API voor de verwijzing naar de bibliotheek- en configuratie-instellingen voor Opt-in.
title: Inschakelen-verwijzing
exl-id: aa61aed7-695b-47e4-a922-9841e00aa09d
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '888'
ht-degree: 0%

---

# Inschakelen-verwijzing{#opt-in-reference}

API voor de verwijzing naar de bibliotheek- en configuratie-instellingen voor Opt-in.

De montages van de toestemming worden verstrekt aan de optiefuncties als categorieën:

```
adobe.OptInCategories = { 
    "AAM": "aam", 
    "ANALYTICS": "aa", 
    "ECID": "ecid", 
    "TARGET": "target" 
}
```

## Parameters van de Opt-in-configuratie {#section-d66018342baf401389f248bb381becbf}

In deze sectie wordt het gebruik van de API voor het configureren van Inschakelen besproken. Veel van de configuratie en de implementatie kan worden gedaan gebruikend de uitbreiding van het Experience Platform Launch.

Opt-inconfiguraties worden geleverd in de functie Visitor JavaScript `getInstance()` , die het algemene `adobe` -object instantieert. De volgende lijst maakt een lijst van de configuraties van JS van de Bezoeker met betrekking tot de open-in dienst.

**`doesOptInApply (boolean or function that evaluates to a boolean)`**:

Indien onwaar, geeft dit aan dat bezoekers niet hoeven aan te melden. Dit resulteert in Experiencen Cloud die cookies maken, ongeacht de categorieën die u in- of uitschakelt. Met deze configuratie kunt u de optie Inschakelen in- of uitschakelen.

**`preOptInApprovals (Object <adobe.OptInCategories enum: boolean>)`**

Bepaal welke categorieën worden goedgekeurd of ontkend wanneer nog geen voorkeur door de bezoeker is geplaatst, die als organisatorische gebreken wordt bedoeld.

**`previousPermissions (Object<adobe.OptInCategories enum: boolean>)`**

De expliciet ingestelde voorkeuren van de bezoeker. De machtigingen in deze configuratie overschrijven de standaardinstellingen van de organisatie ( `previousPermissions` overschrijft `preOptInApprovals` ).

**`isOptInStorageEnabled (boolean)`**

Opt-in inschakelen om de machtigingen op te slaan in een cookie van de eerste partij (binnen het domein van de huidige klant)

(Optioneel) **`optInCookiesDomain (string)`**

Domein van eerste partij of subdomein dat wordt gebruikt voor de Inschakelen-cookie (als `isOptInStorageEnabled` true is)

(Optioneel) **`optInStorageExpiry (integer)`**

Aantal seconden dat nodig is om de standaardvervaldatum van 13 maanden te overschrijven

## Wijzigingen in parameters voor goedkeuring {#section-c3d85403ff0d4394bd775c39f3d001fc}

Op elk gewenst moment tijdens hun ervaring op uw site kan een bezoeker voorkeuren instellen of zijn voorkeuren wijzigen met behulp van uw CMP. Nadat bezoeker JS is geïnitialiseerd met initiële instellingen, kunnen de machtigingen van de bezoeker worden gewijzigd met de volgende functies:

**`adobe.optIn.approve(categories, shouldWaitForComplete)`**

Functie die de bezoeker goedkeurt of in alle categorieën in een lijst kiest. Voor meer informatie over de parameter shouldWaitForComplete, zie [ Opt-in Werkschema ](../../implementation-guides/opt-in-service/getting-started.md#section-70cd243dec834c8ea096488640ae20a5).

**`adobe.optIn.deny(categories, shouldWaitForComplete)`**

Functie die de bezoeker uit alle opgegeven categorieën weergeeft of opkiest.

**`adobe.optIn.approveAll()`**:

Als uw verzoek om toestemming voor het maken van cookies door uw site zo wordt ingekort dat een bezoekersdeken uw site toestemming verleent of weigert om cookies te maken, gebruikt u `approveAll()` of `denyAll()` in verhouding tot hun reactie.

**`adobe.optIn.denyAll()`**:

Als uw verzoek om toestemming voor het maken van cookies door uw site zo wordt geformuleerd dat een bezoekersdeken uw site toestemming verleent of weigert om cookies te maken, gebruikt u `approveAll()` of `denyAll()` , afhankelijk van het antwoord.

## Parameters voor inkomende workflows {#section-2c5adfa5459c4e72b96d2693123a53c2}

Inschakelen ondersteunt een workflow waarin rechten kunnen worden verzameld over meerdere aanvraagcycli, bijvoorbeeld waar voorkeuren een voor een worden gegeven. Gebruikend de volgende functies en het verstrekken van *waar* voor `shouldWaitForComplete` plaatsen, kan uw oplossing toestemming voor één oplossing of een ondergroep van de totale categorieën verzamelen, dan toestemmingen voor volgende één of ondergroep van categorieën verzamelen. Vanaf de eerste aanroep is de eigenschap `adobe.optIn.status` in behandeling totdat `adobe.optIn.complete()` aan het einde van de flow wordt aangeroepen. Zodra geroepen, wordt de status geplaatst aan *Voltooid*.

**`adobe.optIn.approve(categories, shouldWaitForComplete)`**

Functie die de bezoeker goedkeurt of in alle categorieën in een lijst kiest.

`adobe.optIn.deny(categories, shouldWaitForComplete)`

Functie die de bezoeker uit alle opgegeven categorieën weergeeft of opkiest.

`adobe.optIn.complete()`

Functie die de samenvoeging van de voortschrijdende vraag om goed te keuren () en te ontkennen () in één verzoek teweegbrengt om de voorkeur van een bezoeker te plaatsen. Wanneer u zich abonneert op wijzigingen in Opt-in (zie `adobe.optIn.fetchPermissions(callback, shouldAutoSubscribe` ) hieronder, wordt de callback alleen geactiveerd wanneer deze functie wordt aangeroepen.

## Parameters voor machtigingen voor bezoekers {#section-7fe57279b5b44b4f8fe47e336df60155}

Verzamel opt-in toestemmingen voor een bezoeker op elk ogenblik gebruikend één van de toestemmingsfuncties:

`adobe.optIn.permissions`

Een object waarin alle oplossingen voor Experiencen Cloud, als categorieën, worden vermeld die door de bezoeker zijn toegekend of geweigerd.

`adobe.optIn.isApproved(categories)`

Als alle categorieën zijn goedgekeurd, retourneert deze functie true.

`adobe.optIn.fetchPermissions(callback, shouldAutoSubscribe)`

Haal de lijst met machtigingen asynchroon op. De callback wordt geroepen met de lijst van toestemmingen, zodra de toestemmingen die/ontkennend proces verlenen volledig is. Het verstrekken van een waarde van *waar* voor `shouldAutoSubscribe` registreert callback voor om het even welke Opt-binnen veranderingen die door:gaan. Hieronder vindt u eigenschappen van `adobe.OptIn` :

**`permissions`**

Een object met alle oplossingen voor Experiencen Cloud, als categorieën, die door de bezoeker zijn toegestaan of geweigerd. Voorbeeld: `{ aa: true, ecid: false, aam: true... }`

**`status`**

* hangend
* gewijzigd
* complete

**`doesOptInApply`**

Waar of onwaar, die de configuratie vertegenwoordigen u in initialisatie verstrekte

**`isPending`**

Waar of onwaar, afhankelijk van statuswaarde. Inschakelen rapporteert waar voor deze eigenschap voor een bezoeker die nog niet expliciet toestemming heeft geaccepteerd of geweigerd

**`isComplete`**

Waar of onwaar afhankelijk van statuswaarde. Inschakelen kan een fout voor deze eigenschap melden wanneer een toestemming in workflowstijl is gestart maar niet is voltooid.

## Methoden van het object Opt-in {#section-e0417801a82548d199d833010033e433}

**`approve(categories, shouldWaitForComplete)`**

**`categories`**: een of meer categorieën die moeten worden goedgekeurd. Bijvoorbeeld: `adobe.optIn.approve([adobe.OptInCategories.AAM, adobe.OptInCategories.ECID])`
**`shouldWaitForComplete`**: (optioneel) Booleaanse parameter, standaard false. Als u true doorgeeft, wordt het goedkeuringsproces pas voltooid wanneer u `adobe.optIn.complete()` aanroept. Dit proces is vergelijkbaar met een workflow.

```
<codeblock>
  adobe.optIn.approve(adobe.OptInCategories.ANALYTICS, 
         true); adobe.optIn.approve(adobe.OptInCategories.ECID, true); 
         adobe.optIn.complete() 
</codeblock>
```

**`deny(categories, shouldWaitForComplete)`**

* Geef 1 of meer categorieën door om te controleren of ze zijn goedgekeurd.
* Als er geen categorieën zijn doorgegeven, worden ALLE beschikbare categorieën gecontroleerd.

**`isApproved(categories)`**

Controleer of een of meer categorieën door de klant zijn goedgekeurd.

**`isPreApproved(categories)`**

Controleer of een of meer categorieën vooraf zijn goedgekeurd door de klant. (Als ze zijn doorgegeven in de `preOptInApprovals` config).

**`fetchPermissions(callback, shouldAutoSubscribe)`**

Async API om de lijst met machtigingen op te halen. De callback wordt geroepen met de lijst van toestemmingen, zodra de toestemmingen die/ontkennend proces verlenen volledig is. **`shouldAutoSubscribe`:** een helpernut, zal automatisch deze callback aan alle toekomstige gebeurtenissen intekenen. Betekenis callback zal worden geroepen telkens als een goedkeuring of ontkenning trekker in Opt binnen. Op deze manier wordt u altijd bijgewerkt, zonder zelf een abonnement op de gebeurtenissen te nemen.

**Voorbeeld**

`fetchPermissions`

```
optIn.fetchPermissions(function (permissions) { 
    // Here you can check if your category has been approved or not. 
    // We recommend using `optIn.isApproved()` to check for permissions because it abstracts  
       out the details of knowing exactly how the `permissions` list looks like. 
 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
});

// OR: You can pass in `shouldAutoSubscribe` as true, your callback will be used to subscribe  
to all OptIn events going forward:

function callback() { 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
} 
 
optIn.fetchPermissions(callback, true);
```

**`complete()`:**

>[!NOTE]
>
>Gebruik dit alleen als u de parameter `shouldWaitForComplete` hebt doorgegeven om goed te keuren of te weigeren. Deze API voltooit het goedkeuringsproces. Voorbeeld: `adobe.optIn.complete()` .

**`approveAll()`:**

Hiermee worden alle bestaande categorieën goedgekeurd.

**`denyAll()`**

Alle bestaande rubrieken weigeren.

## Gebeurtenissen van het object Opt-in {#section-06f25b33cab54bafb053183e937fb710}

**`complete`:**

De gebeurtenis complete wordt geactiveerd wanneer het goedkeuringsproces is voltooid. Als u Goedkeuren/Weigeren aanroept zonder `shouldWaitForComplete` of `approveAll` / `denyAll` door te geven, wordt deze gebeurtenis geactiveerd. Of als u `shouldWaitForComplete` doorgeeft, wordt deze gebeurtenis geactiveerd wanneer `complete` wordt aangeroepen.

**Voorbeeld**

```
<codeph>
  adobe.optIn.on("complete", callback); 
</codeph>
```
