---
description: De Dienst van identiteitskaart van het Experience Cloud (ECID) steunt het shashing algoritme SHA-256 dat u toestaat om klant IDs of e-mailadressen over te gaan, en gehakt IDs door te geven. Dit is een optionele Javascript-methode voor het verzenden van onderbroken id's naar Experience Cloud. U kunt uw eigen methodes blijven gebruiken om te hakken alvorens klanten IDs te verzenden.
keywords: ID-service
title: SHA256 Hashing Support for setCustomerIDs
exl-id: fd30634e-6435-4d14-8804-649c1ad3aaaa
source-git-commit: 159b37e360b586bbada13e34793009e3067de668
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 0%

---

# SHA256 Hashing-ondersteuning voor `setCustomerIDs` {#hashing-support}

De Dienst van identiteitskaart van het Experience Cloud (ECID) steunt het shashing algoritme SHA-256 dat u toestaat om klant IDs of e-mailadressen over te gaan, en gehakt IDs door te geven. Dit is een optionele Javascript-methode voor het verzenden van onderbroken id&#39;s naar Experience Cloud. U kunt uw eigen methodes blijven gebruiken om te hakken alvorens klanten IDs te verzenden.
Er zijn twee manieren om hashing-ondersteuning te implementeren met setCustomerID&#39;s, zoals beschreven in de volgende secties:

* [De methode setCustomerIDs in ECID gebruiken](/help/reference/hashing-support.md#use-setcustomerids-method)
* [Een handeling toevoegen in Adobe Experience Platform Launch](/help/reference/hashing-support.md#add-action-launch)

## De methode `setCustomerIDs` in ECID gebruiken {#use-setcustomerids-method}

De eerste methode gebruikt de methode [`setCustomerIDs`](/help/library/get-set/setcustomerids.md) (`customerIDs<object>`, `hashType<string>`).

Voordat u hasht, voert de ECID-bibliotheek gegevensnormalisatie uit op de clientID&#39;s. Dit proces maakt de whitespaces van klantIDs op beide einden weg, en zet alle karakters in kleine letters om. Bijvoorbeeld in het geval van e-mailadressen: &quot; ecid@adobe.com &quot; wordt &quot;ecid@adobe.com&quot;

Zie hieronder een codevoorbeeld van hoe u één enkele klant identiteitskaart (het e-mailadres hierboven) met SHA-256 het hashing plaatst.

```
// Set single customerID with SHA-256 hashing
visitor.setCustomerIDs({email: {id: "ecid@adobe.com", authState: 1}}, "SHA-256");
```

<br> 

Samen met de bezoeker-id van het Experience Cloud kunt u aanvullende klant-id&#39;s, verificatiestatus en hashtype (SHA-256) koppelen aan elke bezoeker. Als u geen hashtype verstrekt, zal het als geen hash worden beschouwd.

De methode `setCustomerIDs` accepteert meerdere klant-id&#39;s voor dezelfde bezoeker. Hierdoor kunt u een individuele gebruiker op verschillende apparaten herkennen of als doelgebruiker instellen. Bijvoorbeeld, kunt u deze IDs als [ klantenattributen ](https://experienceleague.adobe.com/docs/core-services/interface/customer-attributes/attributes.html) aan het Experience Cloud uploaden en tot dit gegeven over de verschillende oplossingen toegang hebben.

Identiteitskaart van de klant, voor authentiek verklaarde staten en knoeiboeltype *worden niet* opgeslagen in een koekje dat later moet worden gebruikt. In plaats daarvan, zouden identiteitskaart van de Klant, voor authentiek verklaarde staten en knoeiboeltype in een instantievariabele moeten worden opgeslagen, die moet worden teruggewonnen gebruikend [`getCustomerIDs`](/help/library/get-set/getcustomerids.md), zoals hieronder getoond:

```
> visitor.getCustomerIDs();
< {email: {…}}
    email: {id: "a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097", authState: 1, hashType: "SHA-256"}
    __proto__: Object
```

<br> 

Het gebruik van de methode `setCustomerIDs` resulteert in een aanroep van de Experience Cloud-id-service naar `dpm.demdex.net` , met toevoeging van de parameter `d_cid_ic` query, die de gehashte klant-id bevat. Een voorbeeldvraag zou als hieronder kunnen kijken. Voor de duidelijkheid zijn regeleinden toegevoegd.

```
http://dpm.demdex.net/id?d_visid_ver=4.4.0&d_fieldgroup=AAM&d_rtbd=json&d_ver=2&
d_orgid=12A3F3F459CE0AD80A495CBE%40AdobeOrg&d_nsid=0&d_mid=12349850857640731290890207735189050123&
d_blob=6G1ynYcLPuiQxYZrsz_pkqfLG9yMXBpb2zX5dvJdYQJzPXImdj0y&
d_cid_ic=email%a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097%011&
ts=1563299964843
```

<br> 

Zie de tabel hieronder voor een beschrijving van de parameter `d_cid_ic` en de verificatiestatus.

| Parameter | Beschrijving |
|------------|----------|
| `d_cid_ic` | Geeft de integratiecode, de unieke gebruikersnaam (DPUUID) en een geverifieerde statusid door aan de id-service. Scheid de integratiecode en de DPUUID met het niet-afdrukbare besturingsteken, <code>%01</code>: <br> Voorbeeld: <code> d_cid_ic=Integration_code%01DPUUID%01Authentication_state</code> <br> <b> de Staat van de Authentificatie </b> <br> Dit is een optionele id in de parameter d_cid_ic. Wordt uitgedrukt als een geheel getal en geeft gebruikers aan op basis van hun verificatiestatus, zoals hieronder wordt weergegeven: <br> <ul><li>0 (onbekend of nooit geverifieerd)</li><li>1 (momenteel geverifieerd voor deze instantie/pagina/toepassingscontext)</li><li>2 (Afgemeld)</li></ul> <br> Voorbeelden: <br> <ul><li>Onbekend: ...d_cid=123%01456%01 <b> 0 </b></li><li>Voor authentiek verklaard: ...d_cid=123%01456%01 <b> 1 </b></li><li>Afgemeld: ...d_cid=123%01456%01 <b> 2 </b></li></ul> |

## Een handeling toevoegen in Adobe Experience Platform Launch {#add-action-launch}

Experience Platform Launch is de volgende generatie mogelijkheden voor tagbeheer van Adobe. Lees meer over Platform launch in de [ productdocumentatie van de Lancering ](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl).

Om een actie in Lancering toe te voegen, leest de [ documentatie van Regels ](https://experienceleague.adobe.com/docs/experience-platform/tags/ui/rules.html) in de Lancering van de Adobe en zie het scherm hieronder vangen:

![](/help/reference/assets/hashing-support.png)

<br> 

Nadat u de configuratie hebt bevestigd, plaatst u de gegevens in een object als hieronder:

```
{
    integration_code: {
        id: "value",
        authState: auth_state,
        hashType: "hash_algorithm"
    }
}
```

Hier volgt een codevoorbeeld:

```
// Set single customer ID with hash type
setCustomerIDs(Ingeration code: {
    id: "string_value",
    authState: auth_state,
    hashType: "hash_algorithm"
});
```

Net als de methode `setCustomerIDs` die in de eerste sectie wordt beschreven, resulteert dit in een vraag aan de Dienst van identiteitskaart van het Experience Cloud, met de toevoeging van de `d_cid_ic` vraagparameter.
