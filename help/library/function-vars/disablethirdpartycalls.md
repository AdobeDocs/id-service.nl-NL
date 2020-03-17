---
description: Een optionele, Booleaanse markering die voorkomt dat de id-service aanroepen naar andere domeinen uitvoert.
keywords: cross domain tracking;ID Service
seo-description: Een optionele, Booleaanse markering die voorkomt dat de id-service aanroepen naar andere domeinen uitvoert.
seo-title: disableThirdPartyCalls
title: disableThirdPartyCalls
uuid: e92ce1f5-67a4-476c-9d04-41d4e96b1592
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# disableThirdPartyCalls{#disablethirdpartycalls}

Een optionele, Booleaanse markering die voorkomt dat de id-service aanroepen naar andere domeinen uitvoert.

**Syntaxis:** ` `disableThirdPartyCalls: true|false&quot;(standaardwaarde is `false`.)

Wanneer `disableThirdPartyCalls: true`, zal de dienst van identiteitskaart geen vraag aan andere domeinen maken.

**Doel**

Deze variabele is ontworpen voor klanten die:

* Om de dienst van identiteitskaart te verhinderen vraag van hun veilige, voor authentiek verklaarde pagina&#39;s te maken.
* Sitebezoekers krijgen een Experience Cloud ID (MID).
* Hun andere oplossingen van de Ervaring Cloud om behoorlijk te werken.

**Uitvoeringsstrategie**

Omdat andere Experience Cloud-oplossingen afhankelijk zijn van de MID, roept de id-service Adobe aan om deze id te retourneren en in te stellen. Als u de dienst van identiteitskaart van het maken van vraag van voor authentiek verklaarde gedeelten van uw website moet tegenhouden, dan laat het deze vereiste vraag van pagina&#39;s maken die eerst geen authentificatie vereisen. Nadat de bezoeker van uw site een id heeft, kunt u `disableThirdPartyCalls= true` in de code voor de id-service de geverifieerde gedeelten van uw site instellen. De veronderstelling hier is dat de meeste, zo niet alle, van uw klanten aan een authentificatiepagina zullen navigeren alvorens zij toegang tot de veilige delen van uw plaats krijgen.

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

