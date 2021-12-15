---
description: Deze instructies gelden voor A4T-klanten met gemengde server- en client-side implementaties van Target, Analytics en de ID-service. De klanten die de dienst van identiteitskaart in een milieu NodeJS of Rhino moeten in werking stellen zouden deze informatie ook moeten herzien. Deze instantie van de id-service gebruikt een verkorte versie van de VisitorAPI.js-codebibliotheek, die u downloadt en installeert vanuit Node Package Manager (NPM). Lees deze sectie voor installatie-instructies en andere configuratievereisten.
keywords: ID-service
title: Het gebruiken van de Dienst van identiteitskaart met A4T en een server-zijimplementatie van Doel
exl-id: 6f201378-29a1-44b7-b074-6004246fc999
source-git-commit: e171c94ccfa1f4fe9b8d909d0204adb94f20cbb6
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 0%

---

# Het gebruiken van de Dienst van identiteitskaart met A4T en een server-zijimplementatie van Doel {#using-the-id-service-with-a-t-and-a-server-side-implementation-of-target}

Deze instructies gelden voor A4T-klanten met gemengde server- en client-side implementaties van Target, Analytics en de ID-service. De klanten die de dienst van identiteitskaart in een milieu NodeJS of Rhino moeten in werking stellen zouden deze informatie ook moeten herzien. Deze instantie van de id-service gebruikt een verkorte versie van de VisitorAPI.js-codebibliotheek, die u downloadt en installeert vanuit Node Package Manager (NPM). Lees deze sectie voor installatie-instructies en andere configuratievereisten.

## Inleiding {#section-ab0521ff5bbd44c592c3eaab31c1de8b}

A4T (en andere klanten) kan deze versie van de dienst van identiteitskaart gebruiken wanneer zij moeten:

* Inhoud van webpagina&#39;s op de servers renderen en doorgeven aan een browser voor definitieve weergave.
* Server-kant maken [!DNL Target] oproepen.
* Maak cliënt-kant (in browser) vraag aan [!DNL Analytics].
* Afzonderlijk synchroniseren [!DNL Target] en [!DNL Analytics] Id&#39;s om te bepalen of een bezoeker die door één oplossing wordt gezien dezelfde persoon is als die door de andere oplossing wordt gezien.

## Code downloaden en aangeboden interfaces {#section-32d75561438b4c3dba8861be6557be8a}

Zie de [ID-service NPM-opslagplaats](https://www.npmjs.com/package/@adobe-mcid/visitor-js-server) om het server-zijcodepakket te downloaden en de interfaces te herzien inbegrepen in de huidige bouwstijl.

## Workflow {#section-56b01017922046ed96536404239a272b}

Het diagram en de secties beschrijven hieronder wat gebeurt, en wat u, in elke stap van het server-zijimplementatieproces moet vormen.

![](assets/serverside.png)

## Stap 1: Aanvraagpagina {#section-c12e82633bc94e8b8a65747115d0dda8}

De serveractiviteit begint wanneer een bezoeker een HTTP- verzoek indient om een Web-pagina te laden. Tijdens deze stap ontvangt uw server dit verzoek en controleert de [AMCV cookie](../introduction/cookies.md). Het AMCV-cookie bevat de [!DNL Experience Cloud] ID (MID).

## Stap 2: Payload van id-service genereren {#section-c86531863db24bd9a5b761c1a2e0d964}

Vervolgens moet u een server maken *`payload request`* naar de id-service. Een aanvraag voor een payload:

* Geeft het AMCV-cookie door aan de id-service.
* Vereist gegevens die door Doel en Analytics in volgende hieronder beschreven stappen worden vereist.

>[!NOTE]
>
>Deze methode vraagt om één enkele box van [!DNL Target]. Als u veelvoudige dozen in één enkele vraag moet verzoeken, zie [generateBatchPayload](https://www.npmjs.com/package/@adobe-mcid/visitor-js-server#generatebatchpayload).

Uw payload-verzoek moet er als volgt uitzien: In het codevoorbeeld, `visitor.setCustomerIDs` functie is optioneel. Zie [Klant-id&#39;s en verificatiestatus](../reference/authenticated-state.md) voor meer informatie .

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

De dienst van identiteitskaart keert de lading in een voorwerp JSON terug gelijkend op het volgende voorbeeld. De gegevens van de lading worden vereist door [!DNL Target].

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

Nadat de server ladingsgegevens van de dienst van identiteitskaart ontvangt, moet u extra code concretiseren om het met gegevens samen te voegen die binnen worden overgegaan tot [!DNL Target]. Het laatste JSON-object dat is doorgegeven aan [!DNL Target] zou er ongeveer als volgt uitzien:

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

## Stap 4: Serverstatus ophalen voor de id-service {#section-8ebfd177d42941c1893bfdde6e514280}

De de staatsgegevens van de server bevatten informatie over het werk dat op de server is gedaan. Deze informatie is vereist voor de ID-servicecode aan de clientzijde. Klanten die de id-service via [!DNL Dynamic Tag Manager] (DTM) kan DTM zodanig configureren dat de gegevens van de serverstatus door dat hulpprogramma worden doorgegeven. Als u de dienst van identiteitskaart door een niet-standaardproces hebt opstelling, zult u serverstaat met uw eigen code moeten terugkeren. De client-side id-service en [!DNL Analytics] De code geeft statusgegevens door aan Adobe wanneer de pagina wordt geladen.

**Serverstatus ophalen via DTM**

Als u de id-service met DTM hebt geïmplementeerd, moet u code aan de pagina toevoegen en een naam-waardepaar opgeven in de DTM-instellingen.

**Paginacode**

Deze code toevoegen aan de `<head>` -tag van uw HTML-pagina:

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

**DTM-instellingen**

Voeg deze als naam-waardeparen toe aan de **[!UICONTROL General > Settings]** sectie van de ID-service-instantie:

* **[!UICONTROL Name:]** serverState
* **[!UICONTROL Value:]** %serverState%

   >[!IMPORTANT]
   >
   >De naam van de waarde moet overeenkomen met de naam van de variabele waarvoor u de waarde instelt `serverState` in uw paginacode.

Uw geconfigureerde instellingen moeten er als volgt uitzien:

![](assets/server_side_dtm.png)

**Serverstatus ophalen zonder DTM**

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

## Stap 5: Pagina&#39;s weergeven en Experience Cloud-gegevens retourneren {#section-4b5631a0d75a41febd6f43f8c214c263}

Op dit punt verzendt de webserver pagina-inhoud naar de browser van de bezoeker. Vanaf dit punt maakt de browser (niet de server) alle resterende id-service en [!DNL Analytics] oproepen. Bijvoorbeeld in de browser:

* De dienst van identiteitskaart ontvangt staatsgegevens van de server en gaat SDID tot AppMeasurement over.
* AppMeasurement verzendt gegevens over de aangeraakt pagina naar [!DNL Analytics], inclusief de SDID.
* [!DNL Analytics] en [!DNL Target] Vergelijk SDID&#39;s voor deze bezoeker. met een identieke SDID, [!DNL Target] en [!DNL Analytics] Verbind de server-zijvraag en de cliënt-zijvraag samen. Op dit punt wordt deze bezoeker nu door beide oplossingen als dezelfde persoon herkend.

>[!MORELIKETHIS]
>
>* [Server-Side ID Service Package van Node Package Manager](https://www.npmjs.com/package/@adobe-mcid/visitor-js-server)

