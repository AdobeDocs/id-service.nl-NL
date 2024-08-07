---
description: Een optionele, Booleaanse vlag die bepaalt hoe de browser bronnen van de dienst Identiteit van het Experience Cloud vraagt.
keywords: ID-service
title: useCORSOnly
exl-id: 049a082a-8e6b-44cc-bd05-c12aaf3cbe4d
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---

# useCORSOnly{#usecorsonly}

Een optionele, Booleaanse vlag die bepaalt hoe de browser bronnen van de dienst Identiteit van het Experience Cloud vraagt.

**Syntaxis:** `useCORSOnly: true|false` (gebrek is `false`.)

**Overzicht**

Wanneer ingesteld op `false` , voert de browser resourcecontroles uit met CORS of JSONP. Nochtans, probeert de dienst van identiteitskaart altijd om middelen met CORS eerst te verzoeken. Het keert aan JSONP op oudere browsers terug die geen CORS steunen. Als u de browser wilt dwingen alleen CORS te gebruiken, stelt u `useCORSOnly:true` in de functieaanroep `Visitor.getInstance` in.

>[!IMPORTANT]
>
>`Set useCORSOnly: true` als u strikte beveiligingsvereisten hebt. Schakel deze modus alleen in als u zeker weet dat alle bezoekers browsers gebruiken die ondersteuning bieden voor CORS. De gebruikerservaring wordt niet beïnvloed door browsers die geen ondersteuning bieden voor CORS. Browsers zonder CORS-ondersteuning kunnen echter geen bronnen aanvragen of gegevens uitwisselen met de [!DNL Adobe Experience Cloud] .

**Steekproef van de Code**

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
