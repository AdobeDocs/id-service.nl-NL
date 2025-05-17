---
description: Naast de bezoeker-id van het Experience Cloud kunt u aanvullende klant-id's en een verificatiestatus aan elke bezoeker koppelen.
keywords: ID-service
title: Klant-id's en verificatiestatus
exl-id: 0215225c-20f5-4e44-a368-b2df683aca9d
source-git-commit: 159b37e360b586bbada13e34793009e3067de668
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 0%

---

# Klant-id&#39;s en verificatiestatus {#customer-ids-and-authentication-states}

Naast de bezoeker-id van het Experience Cloud kunt u aanvullende klant-id&#39;s en een verificatiestatus aan elke bezoeker koppelen.

## Verificatiestatus {#section-68ad4065dfaa437d9070832d6e2bf85c}

De methode `setCustomerIDs` accepteert meerdere klant-id&#39;s voor dezelfde bezoeker. Hierdoor kunt u een individuele gebruiker op verschillende apparaten herkennen of als doelgebruiker instellen. Bijvoorbeeld, kunt u deze IDs als [ klantenattributen ](https://experienceleague.adobe.com/docs/core-services/interface/customer-attributes/attributes.html?lang=nl-NL) aan [!DNL Experience Cloud] uploaden en tot dit gegeven over de verschillende oplossingen toegang hebben.

>[!IMPORTANT]
>
>`setCustomerIDs` (synchronisatie van klant-id) wordt vereist door de kenmerken van de klant en de kernservicefunctionaliteit. Het synchroniseren van klant-id&#39;s is een optionele identificatiemethode voor [!DNL Analytics] . [!DNL Target] vereist `Visitor.AuthState.AUTHENTICATED` voor klantkenmerken om te kunnen werken. Zie [ Diensten van de Kern - hoe te om Uw Oplossingen ](https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html) voor voorbeelden toe te laten.

Vanaf Experience Cloud Identity Service v1.5+ bevat `setCustomerIDs` het optionele `AuthState` -object. `AuthState` identificeert bezoekers op basis van hun verificatiestatus (bijvoorbeeld aangemeld, afgemeld). U stelt de verificatiestatus in met een statuswaarde in de tabel. De verificatiestatus wordt geretourneerd als een geheel getal.

<table id="table_8547671CC97145529981FBF6C302BEC5"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Status van verificatie </th> 
   <th colname="col2" class="entry"> Statusgeheel getal </th> 
   <th colname="col3" class="entry"> Gebruikersstatus </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.UNKNOWN </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 0 </span> </p> </td> 
   <td colname="col3"> <p>Onbekend of nooit geverifieerd. </p> <p> Onbekend wordt standaard toegepast wanneer <span class="codeph"> AuthState </span> niet wordt gebruikt met een bezoeker-id of niet expliciet wordt ingesteld op elke pagina- of toepassingscontext. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 1 </span> </p> </td> 
   <td colname="col3"> <p>Voor authentiek verklaard voor een bepaalde instantie, een pagina, of een toepassing. </p> <p> <p>Let op: deze status is vereist voor een correcte werking van de klantkenmerken voor <span class="keyword"> Target </span> . </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 2 </span> </p> </td> 
   <td colname="col3"> <p>Afgemeld. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Gevallen gebruiken voor verificatiestatussen {#section-fe9560cc490943b29dac2c4fb6efd72c}

U kunt verificatiestatussen toewijzen aan uw gebruikers, afhankelijk van de handelingen die zij uitvoeren op uw wegeigenschappen en of zij zijn geverifieerd. Zie enkele voorbeelden in de onderstaande tabel:

<table id="table_3769E79304014C4F87094B87A8ACE4E0"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Status van verificatie </th> 
   <th colname="col2" class="entry"> Hoofdletters gebruiken </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.UNKNOWN </span> </p> </td> 
   <td colname="col2"> <p>Deze status kan worden gebruikt voor scenario's zoals: </p> <p> 
     <ul id="ul_086C7446D258443DA7AF5BB96A6AAEC7"> 
      <li id="li_7845BBD62D7B4362AD3FE33DEDA8FBA1">Een e-mail lezen (deze handeling betekent mogelijk dat de lezer de beoogde ontvanger is, maar dat de e-mail ook had kunnen worden doorgestuurd). </li> 
      <li id="li_FAB7ACFC69624631BD01FC0ED84B23C5">Klik van een e-mail aan een landingspagina door. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p>De gebruiker is momenteel geverifieerd met een actieve sessie op uw website of app. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p>De gebruiker werd voor authentiek verklaard maar actief het programma geopend. De gebruiker bedoelde en bedoeld om van de voor authentiek verklaarde staat los te maken. De gebruiker wil niet meer worden beschouwd als geverifieerd. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Klant-id&#39;s en geverifieerde statussen instellen {#section-ec4b367d16ad4ac1a1baca9b01f4ee98}

Klant-id&#39;s kunnen combinaties van id&#39;s en geverifieerde statussen bevatten, zoals in de volgende voorbeelden wordt getoond.

>[!IMPORTANT]
>
>* Id&#39;s zijn hoofdlettergevoelig.
>* Gebruik alleen ongecodeerde waarden voor uw id&#39;s.
>* De klant-id&#39;s en verificatiestatus worden niet opgeslagen in het cookie van de bezoeker-id. Deze instellingen moeten worden ingesteld voor elke pagina- of toepassingscontext.
>* U zou geen Persoonlijk Identificeerbare Informatie (PII) in klant IDs moeten omvatten. Als u PII gebruikt om een bezoeker (zoals een e-mailadres) te identificeren, adviseren wij in plaats daarvan een gehakte of gecodeerde versie van de informatie op te slaan. De ECID-bibliotheek biedt ondersteuning voor het hashen van gebruikers-id&#39;s. Zie [ SHA256 het Hashing Steun voor setCustomerIDs ](/help/reference/hashing-support.md).

```js
// Single ID with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
/* 
Multiple IDs with only the first ID explicitly assigned an authentication state. 
The second ID is not explicitly assigned an authentication state and is implicitly 
assigned Visitor.AuthState.Unknown by default. 
*/ 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":"550e8400-e29b-41d4-a716-446655440000" 
}); 
 
// Multiple IDs with identical authentication states 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
// Multiple IDs with different authentication states 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":Visitor.AuthState.LOGGED_OUT 
    } 
}); 
```

## Klanten-id&#39;s en geverifieerde statussen retourneren {#section-71a610546188478fa9a3185a01d6e83b}

Gebruik `getCustomerIDs` om klant-id&#39;s en verwante geverifieerde statussen te retourneren. Deze methode retourneert de geverifieerde status van een bezoeker als een geheel getal.

**Syntaxis**

`getCustomerIDs` retourneert gegevens met de volgende syntaxis.

```js
{ 
    [customerIDType1]:{ 
        "id":[customerID1], 
        "authState":[authState1] 
    }, 
    [customerIDType2]:{ 
        "id":[customerID2], 
        "authState":[authState2] 
    } 
    ... 
}
```

**Voorbeelden**

Geretourneerde klant IDs en de gegevens van de authentificatiestatus zouden gelijkaardig aan de volgende voorbeelden moeten kijken.

```js
Object customerIDs = visitor.getCustomerIDs(); 
  
// No setCustomerIDs call on this instance 
{} 
  
// setCustomerIDs call on this instance with {"userid":{"id":"67312378756723456"}} 
{ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":0 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"id":"67312378756723456","authState":Visitor.AuthState.AUTHENTICATED}} 
{ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":1 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"authState":Visitor.AuthState.LOGGED_OUT}} 
{ 
    "userid":{ 
        "authState":2 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"authState":Visitor.AuthState.LOGGED_OUT},"dpuuid":{"id":"550e8400-e29b-41d4-a716-446655440000"}} 
{ 
    "userid":{ 
        "authState":2 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":0 
    } 
 }
```

## SDK-ondersteuning {#section-861c6b3b1ba645dda133dccb22ec7bb0}

De [!DNL Experience Cloud] ID-service ondersteunt de klant-id&#39;s en verificatiestatus in onze Android- en iOS SDK-code. Zie de volgende codebibliotheken:

* [ de methodes van SDK van Android ](https://experienceleague.adobe.com/docs/mobile-services/android/overview.html?lang=nl-NL)
* [ de methodes van SDK van iOS ](https://experienceleague.adobe.com/docs/mobile-services/ios/overview.html?lang=nl-NL)

## Bericht voor klanten van Analytics en van de Audience Manager {#section-3a8e9d51e71c4c6e865184b81ed9d99b}

Als u gedeclareerde id&#39;s doorgeeft aan [!DNL Audience Manager] , moet het `userid` -object overeenkomen met de integratiecode die is gekoppeld aan een gegevensbron. Voor meer informatie, zie de [!UICONTROL Visitor ID Service] sectie in [ vormt de documentatie van de Code van de Regels van de Fusie ](https://experienceleague.adobe.com/docs/audience-manager/user-guide/features/profile-merge-rules/merge-rules-start.html?lang=nl-NL#configure-merge-rule-code).
