---
description: getInstance retourneert een bezoeker-id-object voor de opgegeven Experience Cloud organisatie-id. Dit is vereist om het object met de bezoeker-id te initialiseren dat aan AppMeasurement wordt geleverd via s.bezoekor.
keywords: ID-service
title: getInstance
exl-id: 4941cf51-a8d0-4796-a102-4cd13cd5574d
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# getInstance{#getinstance}

getInstance retourneert een bezoeker-id-object voor de opgegeven Experience Cloud organisatie-id. Dit is vereist om het object met de bezoeker-id te initialiseren dat aan AppMeasurement wordt geleverd via s.bezoekor.

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
>*Niet gebruiken* instantiëren van de functie Visitor met `var visitor = new Visitor`. U moet de juiste hier genoteerde functievraag gebruiken. Van toepassing op [!UICONTROL VisitorAPI.js] codebibliotheek v3.0 of hoger.

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

Indien `getInstance` vindt geen bestaande instantie, wordt een nieuwe instantie gecreeerd en teruggekeerd. Dit is vergelijkbaar met het [ `s_gi()` function ](https://experienceleague.adobe.com/docs/analytics/implementation/vars/functions/s-gi.html) in [!DNL AppMeasurement].

**Algemeen gebruik**

De [!DNL Experience Cloud] ID-service-API houdt een lijst bij van alle instanties die voor elke [!DNL Adobe Experience Cloud] organisatie-id. Als de toepassing die de dienst-API van identiteitskaart gebruikt geen verwijzing naar de instantie overgaat, kan het die instantie vinden door te roepen `getInstance` in plaats van een nieuwe te maken. Dit biedt ook ondersteuning voor meerdere instanties voor verschillende organisaties in dezelfde webpagina of toepassing.

Dit is nuttig voor toepassingen die geen duidelijk `init` fase, maar moet in de dienst API van identiteitskaart op veelvoudige plaatsen roepen. U kunt bellen `getInstance` op al die plaatsen en de eerste uit te voeren zal tot de instantie leiden. De bestaande instantie zal door verdere vraag zijn teruggekeerd.
