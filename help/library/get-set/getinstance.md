---
description: getInstance retourneert een bezoeker-ID-object voor de opgegeven Experience Cloud-organisatie-id. Dit is vereist om het bezoekersidentiteitskaart- voorwerp te initialiseren dat aan AppMeasurement door s.bezoeker wordt verstrekt.
keywords: ID-service
title: getInstance
exl-id: 4941cf51-a8d0-4796-a102-4cd13cd5574d
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# getInstance{#getinstance}

getInstance retourneert een bezoeker-ID-object voor de opgegeven Experience Cloud-organisatie-id. Dit is vereist om het bezoekersidentiteitskaart- voorwerp te initialiseren dat aan AppMeasurement door s.bezoeker wordt verstrekt.

**Syntaxis**

**JavaScript**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

>[!CAUTION]
>
>*concretiseer niet* de functie van de Bezoeker met `var visitor = new Visitor`. U moet de juiste hier genoteerde functievraag gebruiken. Is van toepassing op [!UICONTROL VisitorAPI.js] codebibliotheek v3.0 of hoger.

**ActionScript/Flash**

```js
import com.adobe.mc.Visitor; 
... 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

Wanneer `getInstance` geen bestaande instantie vindt, wordt een nieuwe instantie gemaakt en geretourneerd. Dit is vergelijkbaar met de functie [`s_gi()` ](https://experienceleague.adobe.com/docs/analytics/implementation/vars/functions/s-gi.html) in [!DNL AppMeasurement] .

**Algemeen Gebruik**

De [!DNL Experience Cloud] ID service-API onderhoudt een lijst met alle instanties die voor elke [!DNL Adobe Experience Cloud] organisatie-id zijn gemaakt. Als de toepassing die de id-service-API gebruikt, geen verwijzing naar de instantie doorgeeft, kan deze de instantie vinden door `getInstance` aan te roepen in plaats van een nieuwe instantie te maken. Dit biedt ook ondersteuning voor meerdere instanties voor verschillende organisaties in dezelfde webpagina of toepassing.

Dit is nuttig voor toepassingen die geen duidelijke `init` fase hebben, maar in de dienst API van identiteitskaart op veelvoudige plaatsen moeten roepen. U kunt `getInstance` op al die plaatsen roepen en de eerste uit te voeren zal tot de instantie leiden. De bestaande instantie zal door verdere vraag zijn teruggekeerd.
