---
description: Deze functie is vooral ontworpen voor klanten van A4T om problemen op te lossen die verband houden met het werken met id's op sites/schermen of apps van één pagina.
keywords: ID-service
title: resetState
exl-id: 8e8cb299-bb89-4bc1-8841-3091ce0cbd81
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# resetState{#resetstate}

Deze functie is vooral ontworpen voor klanten van A4T om problemen op te lossen die verband houden met het werken met id&#39;s op sites/schermen of apps van één pagina.

## Gebruiksscenario’s {#section-840b88a5cdb042488b340cad5d7b22a5}

Als klant A4T die de dienst van identiteitskaart gebruikt, kunt u willen gebruiken `visitor.resetState()` functie wanneer u wilt:

* Een aanvullende gegevens-id (SDID) of een andere id doorgeven van de ene pagina of het andere scherm via omleiding. Normaal, zal de dienst van identiteitskaart deze identiteitskaart zonder deze functie niet overgaan.
* Gebruik code die alleen specifieke secties van een pagina of app bijwerkt via Ajax-aanroepen en u wilt die handelingen bijhouden. Stel dat u een pagina hebt waarop u met klikken op een object alleen een speciale sectie laadt of wijzigt. In dit geval kan de id-service geen andere id aanvragen, tenzij de pagina opnieuw wordt geladen. Met `visitor.resetState()`, je kunt onder deze voorwaarden een nieuwe id aanvragen.

Zie de onderstaande codevoorbeelden.

## Syntaxis {#section-9e63503e178f4be28ac850abf44d6d91}

**Syntaxis:** ` visitor.resetState( *`state`*);`

## Codevoorbeelden {#section-d75b211bb4ea473887eb284de2ad838b}

De implementatie van uw id-service beïnvloedt hoe u deze functie zou gebruiken. Zie de onderstaande tabel voor voorbeelden.

**Implementatie op de server**

Een server-kant implementatie is voor klanten A4T met gemengde server- en cliënt-zijimplementaties van [!DNL Target], [!DNL Analytics]en de id-service. Als u de id-service met deze methode hebt ingesteld, hoeft u alleen maar toe te voegen `visitor.resetState()` naar de pagina. De vraag aan de dienst van identiteitskaart zal een nieuwe identiteitskaart en serverstaat automatisch terugkeren.

**Niet-standaardimplementatie** (met ID)

Als u de id-service hebt ingesteld met een [niet-standaardimplementatie](../../implementation-guides/implementation-guides.md#section-2c4f2db1f9704315a7cccab6d2e07113), moet u een veranderlijk voorwerp vormen om SDID (of andere IDs) te houden u met wilt overgaan `visitor.resetState()`. Zoals hieronder wordt getoond, omvat dit uw [organisatie-id](../../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26) en de id die u wilt doorgeven. Uw code kan er ongeveer als volgt uitzien.

```js
//Instantiate server state variable 
var serverState = { 
     "Insert Experience Cloud organization ID here": { 
          //Specify the SDID or other ID 
          supplementalDataIDCurrent: "1234", 
          supplementalDataIDCurrentConsumed: { 
               "payload:top-center": false 
          } 
     } 
}; 
 
//Instantiate ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here", { 
     ... 
}); 
 
//Reset server state to pass the SDID 
visitor.resetState(serverState);
```

**Niet-standaardimplementatie** (zonder een id door te geven)

In dit geval: `visitor.resetState()` kan worden gebruikt om een nieuwe id te genereren. Dit kan handig zijn in een app van één pagina wanneer een gebruiker naar een nieuw scherm navigeert zonder de pagina te vernieuwen en u een nieuwe id nodig hebt.

```js
 
//Instantiate ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here", { 
     ... 
}); 
 
//Request a supplemental Data ID for consumer1 and consumer2: 
var sdid1 = visitor.getSupplementalDataID("consumer1"); // sdid1: 1234 
var sdid2 = visitor.getSupplementalDataID("consumer2"); // sdid2: 1234 
 
//User navigates to a new screen in a single-page app, without refreshing the page. 
//To reset the Supplemental Data ID internal, call resetState without passing any parameters. 
//This way we will not be recycling the `1234` ID anymore. Instead Visitor will generate a new supplemental Data ID going forward. 
visitor.resetState(); 
 
//Request a supplemental Data ID for consumer3 and consumer4: 
var sdid1 = visitor.getSupplementalDataID("consumer3"); // sdid1: 5678 
 
var sdid2 = visitor.getSupplementalDataID("consumer4"); // sdid2: 5678
```

**Dynamisch tagbeheer (DTM)**

Er is momenteel geen DTM-configuratiepad voor `visitor.resetState()`.
