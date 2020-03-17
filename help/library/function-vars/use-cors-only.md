---
description: Een optionele, Booleaanse vlag die bepaalt hoe de browser bronnen opvraagt bij de Experience Cloud Identity Service.
keywords: ID Service
seo-description: Een optionele, Booleaanse vlag die bepaalt hoe de browser bronnen opvraagt bij de Experience Cloud Identity Service.
seo-title: useCORSOnly
title: useCORSOnly
uuid: 607dc035-dffc-4f4d-be51-08ef6c0a8fad
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# useCORSOnly{#usecorsonly}

Een optionele, Booleaanse vlag die bepaalt hoe de browser bronnen opvraagt bij de Experience Cloud Identity Service.

**Syntaxis:** `useCORSOnly: true|false` (standaardwaarde is `false`.)

**Overzicht**

Wanneer geplaatst aan `false`, voert browser middelcontroles met CORS of JSONP uit. Nochtans, probeert de dienst van identiteitskaart altijd om middelen met CORS eerst te verzoeken. Het keert aan JSONP op oudere browsers terug die geen CORS steunen. Als u de browser wilt dwingen alleen CORS te gebruiken, stelt u deze in `useCORSOnly:true` de `Visitor.getInstance` functieaanroep in.

>[!IMPORTANT]
>
>`Set useCORSOnly: true` als u strikte beveiligingsvereisten hebt. Schakel deze modus alleen in als u zeker weet dat alle bezoekers browsers gebruiken die ondersteuning bieden voor CORS. De gebruikerservaring wordt niet beïnvloed door browsers die geen ondersteuning bieden voor CORS. Browsers zonder CORS-ondersteuning kunnen echter geen bronnen aanvragen of gegevens uitwisselen met de [!DNL Adobe Experience Cloud]server.

**Codevoorbeeld**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   useCORSOnly: true 
});
```

