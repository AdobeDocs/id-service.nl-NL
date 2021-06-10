---
description: Een optionele, Booleaanse markering die voorkomt dat de id-service aanroepen naar andere domeinen uitvoert.
keywords: domeinoverschrijdende tracering;ID-service
title: disableThirdPartyCalls
exl-id: 1d5b4e80-1b2d-4401-9057-449a6abf5db5
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 2%

---

# disableThirdPartyCalls{#disablethirdpartycalls}

Een optionele, Booleaanse markering die voorkomt dat de id-service aanroepen naar andere domeinen uitvoert.

**Syntaxis:** ` `disableThirdPartyCalls: true|false&quot;(standaardwaarde is  `false`.)

Wanneer `disableThirdPartyCalls: true`, zal de dienst van identiteitskaart geen vraag aan andere domeinen maken.

**Doel**

Deze variabele is ontworpen voor klanten die:

* Om de dienst van identiteitskaart te verhinderen vraag van hun veilige, voor authentiek verklaarde pagina&#39;s te maken.
* Site-bezoekers moeten een Experience Cloud-id (MID) hebben.
* Hun andere Experience Cloud oplossingen werken naar behoren.

**Uitvoeringsstrategie**

Omdat andere Experience Cloud oplossingen zich op MID baseren, roept de dienst van identiteitskaart Adobe om deze identiteitskaart terug te keren en te plaatsen. Als u de dienst van identiteitskaart van het maken van vraag van voor authentiek verklaarde gedeelten van uw website moet tegenhouden, dan laat het deze vereiste vraag van pagina&#39;s maken die eerst geen authentificatie vereisen. Nadat de bezoeker van uw site een id heeft, kunt u `disableThirdPartyCalls= true` instellen in de code voor de id-service op de geverifieerde gedeelten van uw site. De veronderstelling hier is dat de meeste, zo niet alle, van uw klanten aan een authentificatiepagina zullen navigeren alvorens zij toegang tot de veilige delen van uw plaats krijgen.

**Codevoorbeeld**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCalls: true 
}); 
```
