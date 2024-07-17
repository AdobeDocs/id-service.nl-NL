---
description: Deze instructies gelden voor A4T-klanten met gemengde server- en client-side implementaties van Target, Analytics en de ID-service. De klanten die de dienst van identiteitskaart in een milieu NodeJS of Rhino moeten in werking stellen zouden deze informatie ook moeten herzien. Deze instantie van de id-service gebruikt een verkorte versie van de VisitorAPI.js-codebibliotheek, die u downloadt en installeert vanuit Node Package Manager (NPM). Lees deze sectie voor installatie-instructies en andere configuratievereisten.
keywords: ID-service
title: Het gebruiken van de Dienst van identiteitskaart met A4T en een server-zijimplementatie van Doel
exl-id: 6f201378-29a1-44b7-b074-6004246fc999
source-git-commit: e171c94ccfa1f4fe9b8d909d0204adb94f20cbb6
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 0%

---

# Het gebruiken van de Dienst van identiteitskaart met A4T en een server-zijimplementatie van Doel {#using-the-id-service-with-a-t-and-a-server-side-implementation-of-target}

Deze instructies gelden voor A4T-klanten met gemengde server- en client-side implementaties van Target, Analytics en de ID-service. De klanten die de dienst van identiteitskaart in een milieu NodeJS of Rhino moeten in werking stellen zouden deze informatie ook moeten herzien. Deze instantie van de id-service gebruikt een verkorte versie van de VisitorAPI.js-codebibliotheek, die u downloadt en installeert vanuit Node Package Manager (NPM). Lees deze sectie voor installatie-instructies en andere configuratievereisten.

## Inleiding {#section-ab0521ff5bbd44c592c3eaab31c1de8b}

A4T (en andere klanten) kan deze versie van de dienst van identiteitskaart gebruiken wanneer zij moeten:

* De inhoud van webpagina&#39;s op de servers weergeven en deze doorgeven aan een browser voor de uiteindelijke weergave.
* Maak serveraanroepen [!DNL Target] .
* Maak client-side (in-browser) aanroepen naar [!DNL Analytics] .
* Synchroniseer afzonderlijke id&#39;s [!DNL Target] en [!DNL Analytics] om te bepalen of een bezoeker die door een oplossing wordt gezien dezelfde persoon is als de andere oplossing.

## Code downloaden en aangeboden interfaces {#section-32d75561438b4c3dba8861be6557be8a}

Zie de [ dienstNPM bewaarplaats van identiteitskaart ](https://www.npmjs.com/package/@adobe-mcid/visitor-js-server) om het server-zijcodepakket te downloaden en de interfaces te herzien inbegrepen in de huidige bouwstijl.

## Workflow {#section-56b01017922046ed96536404239a272b}

Het diagram en de secties beschrijven hieronder wat gebeurt, en wat u, in elke stap van het server-zijimplementatieproces moet vormen.

![](assets/serverside.png)

## Stap 1: pagina Aanvragen {#section-c12e82633bc94e8b8a65747115d0dda8}

De activiteit aan de serverzijde begint wanneer een bezoeker een HTTP- verzoek indient om een Web-pagina te laden. Tijdens deze stap, ontvangt uw server dit verzoek en controles voor het [ koekje van AMCV ](../introduction/cookies.md). Het AMCV-cookie bevat de [!DNL Experience Cloud] ID (MID) van de bezoeker.

## Stap 2: Produceer de nuttige lading van de Dienst van identiteitskaart {#section-c86531863db24bd9a5b761c1a2e0d964}

Vervolgens moet u een server-side *`payload request`* maken voor de id-service. Een aanvraag voor een payload:

* Geeft het AMCV-cookie door aan de id-service.
* Vereist gegevens die door Doel en Analytics in volgende hieronder beschreven stappen worden vereist.

>[!NOTE]
>
>Deze methode vraagt om één enkele box van [!DNL Target]. Als u veelvoudige dozen in één enkele vraag moet verzoeken, zie [ generateBatchPayload ](https://www.npmjs.com/package/@adobe-mcid/visitor-js-server#generatebatchpayload).

Uw payload-verzoek moet er als volgt uitzien: In het codevoorbeeld is de functie `visitor.setCustomerIDs` optioneel. Zie [ identiteitskaarts van de Klant en de Staten van de Authentificatie ](../reference/authenticated-state.md) voor meer informatie.

```js
//Import the ID service server package 
var Visitor = require("@adobe-mcid/visitor-js-server"); 
 
//Pass in your Organization ID to instantiate Visitor 
var visitor = new Visitor("Insert Experience Cloud ID here"); 
 
// 
<i>(Optional)</i> Set a custom customer ID 
visitor.setCustomerIDs({ 
     userid:{ 
          id:"1234", 
          authState: Visitor.AuthState.UNKNOWN //AuthState is a static property of the Visitor class 
     } 
}); 
 
//Parse the visitor's HTTP request for the AMCV cookie 
var cookies = cookie.parse(req.headers.cookie || ""); 
var cookieName = visitor.getCookieName(); // Visitor API that returns the cookie name. 
var amcvCookie = cookies[cookieName]; 
 
//Generate the payload request pass your mbox name and the AMCV cookie if present 
var visitorPayload = visitor.generatePayload({ 
     mboxName: "bottom-banner-mbox", 
     amcvCookie: amcvCookie 
});
```

De dienst van identiteitskaart keert de lading in een voorwerp JSON terug gelijkend op het volgende voorbeeld. Payload-gegevens worden vereist door [!DNL Target] .

```js
{ 
    "marketingCloudVisitorId": "02111696918527575543455026275721941645", 
    "mboxParameters": { 
        "mboxAAMB": "abcd1234", 
        "mboxMCGLH": "9", 
        "mboxMCSDID": "56BE026543F7E211-1CC51BCAAE88F0D2", 
        "vst.userid.id": "1234567890", 
        "vst.userid.authState": 0 
    } 
}
```

Als uw bezoeker geen cookie van AMCV heeft, worden deze sleutelwaardeparen bij de payload weggelaten:

* `marketingCloudvisitorId`
* `mboxAAMB`
* `mboxMCGLH`

## Stap 3: Voeg nuttige lading aan de vraag van het Doel toe {#section-62451aa70d2f44ceb9fd0dc2d4f780f7}

Nadat de server ladingsgegevens van de dienst van identiteitskaart ontvangt, moet u extra code concretiseren om het met gegevens samen te voegen die tot [!DNL Target] worden overgegaan. Het uiteindelijke JSON-object dat aan [!DNL Target] wordt doorgegeven, ziet er ongeveer als volgt uit:

```js
{ 
"mbox" : "target-global-mbox", 
"marketingCloudVisitorId":"02111696918527575543455026275721941645", 
"requestLocation" : { 
     "pageURL" : "http://www.domain.com/test/demo.html", 
     "host" : "localhost:3000" 
     }, 
"mboxParameters" : { 
     "mboxAAMB" : "abcd1234", 
     "mboxMCGLH" : "9", 
     "mboxMCSDID": "56BE026543F7E211-1CC51BCAAE88F0D2", 
     "vst.userid.id": "1234567890", 
     "vst.userid.authState": 0, 
     } 
} 
```

## Stap 4: Krijg serverstaat voor de Dienst van identiteitskaart {#section-8ebfd177d42941c1893bfdde6e514280}

De de staatsgegevens van de server bevatten informatie over het werk dat op de server is gedaan. Deze informatie is vereist voor de ID-servicecode aan de clientzijde. Klanten die de id-service via [!DNL Dynamic Tag Manager] (DTM) hebben geïmplementeerd, kunnen DTM zodanig configureren dat de gegevens van de serverstatus door dat hulpprogramma worden doorgegeven. Als u de dienst van identiteitskaart door een niet-standaardproces hebt opstelling, zult u serverstaat met uw eigen code moeten terugkeren. De client-side id-service en [!DNL Analytics] -code geven statusgegevens door aan de Adobe wanneer de pagina wordt geladen.

**krijgt serverstaat via DTM**

Als u de id-service met DTM hebt geïmplementeerd, moet u code aan de pagina toevoegen en een naam-waardepaar opgeven in de DTM-instellingen.

**Code van de Pagina**

Voeg deze code toe aan de tag `<head>` van de pagina HTML:

```js
//Get server state 
var serverState = visitor.getState(); 
 
Response.send(" 
... 
<head> 
     <script> 
          //Add 'serverState' as a stringified JSON global variable. 
          "var serverState = "+ JSON.stringify(serverState) +";  
     </script> 
     <script src = "DTM script (satellite JS)"> 
     </script> 
</head> 
...
```

**Montages DTM**

Voeg deze als naam-waardeparen aan de **[!UICONTROL General > Settings]** sectie van uw de dienstinstantie van identiteitskaart toe:

* **[!UICONTROL Name:]** serverState
* **[!UICONTROL Value:]** %serverState%

  >[!IMPORTANT]
  >
  >De naam van de waarde moet overeenkomen met de variabelenaam die u instelt voor `serverState` in de paginacode.

Uw geconfigureerde instellingen moeten er als volgt uitzien:

![](assets/server_side_dtm.png)

**krijgt serverstaat zonder DTM**

Als u een niet-standaardimplementatie van de dienst van identiteitskaart hebt, moet u deze code vormen om op uw server te lopen terwijl het de gevraagde pagina assembleert:

```js
//Get server state 
var serverState = visitor.getState(); 
 
Response.send(" 
... 
<head> 
     <script src="VisitorAPI.js"></script> 
     <script> 
          var visitor = Visitor.getInstance(orgID, { 
          serverState: serverState  
          ... 
     </script> 
</head> 
...
```

## Stap 5: Geef een pagina en de gegevens van het Experience Cloud terug {#section-4b5631a0d75a41febd6f43f8c214c263}

Op dit punt verzendt de webserver pagina-inhoud naar de browser van de bezoeker. Vanaf dit punt voert de browser (niet de server) alle resterende id-service en [!DNL Analytics] -aanroepen uit. In de browser:

* De dienst van identiteitskaart ontvangt staatsgegevens van de server en gaat SDID tot AppMeasurement over.
* AppMeasurement verzendt gegevens over de aangeraakt pagina naar [!DNL Analytics], met inbegrip van SDID.
* [!DNL Analytics] en [!DNL Target] vergelijk SDID&#39;s voor deze bezoeker. Met een identieke SDID [!DNL Target] en [!DNL Analytics] hecht u de serveraanroep en de client-side aanroep aan elkaar. Op dit punt wordt deze bezoeker nu door beide oplossingen als dezelfde persoon herkend.

>[!MORELIKETHIS]
>
>* [ server-zij het Pakket van de Dienst van identiteitskaart van de Manager van het Pakket van de Knoop ](https://www.npmjs.com/package/@adobe-mcid/visitor-js-server)
