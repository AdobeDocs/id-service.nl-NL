---
description: getInstance retourneert een bezoeker-id-object voor de opgegeven Experience Cloud organisatie-id. Dit is vereist om het object met de bezoeker-id te initialiseren dat aan AppMeasurement wordt geleverd via s.bezoekor.
keywords: ID Service
seo-description: getInstance retourneert een bezoeker-id-object voor de opgegeven Experience Cloud organisatie-id. Dit is vereist om het object met de bezoeker-id te initialiseren dat aan AppMeasurement wordt geleverd via s.bezoekor.
seo-title: getInstance
title: getInstance
uuid: 259b88a6-e3d0-4aab-b935-566099bdab98
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: tm+mt
source-wordcount: '253'
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
>*Instantieer de functie Visitor niet* met `var visitor = new Visitor`. U moet de juiste hier genoteerde functievraag gebruiken. Is van toepassing op [!UICONTROL VisitorAPI.js] codebibliotheek v3.0 of hoger.

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

Wanneer `getInstance` geen bestaande instantie wordt gevonden, wordt een nieuwe instantie gemaakt en geretourneerd. Dit is vergelijkbaar met de [ functie `s_gi()` in ](https://docs.adobe.com/content/help/en/analytics/implementation/vars/functions/s-gi.html) [!DNL AppMeasurement].

**Algemeen gebruik**

De [!DNL Experience Cloud] id-service-API onderhoudt een lijst met alle instanties die voor elke [!DNL Adobe Experience Cloud] organisatie-id zijn gemaakt. Als de toepassing die de dienst-API van identiteitskaart gebruikt geen verwijzing naar de instantie overgaat, kan het die instantie vinden door te roepen `getInstance` in plaats van het creëren van nieuwe. Dit biedt ook ondersteuning voor meerdere instanties voor verschillende organisaties in dezelfde webpagina of toepassing.

Dit is nuttig voor toepassingen die geen duidelijke `init` fase hebben, maar in de dienst API van identiteitskaart in veelvoudige plaatsen moeten roepen. U kunt `getInstance` op al die plaatsen roepen en de eerste uit te voeren zal tot de instantie leiden. De bestaande instantie zal door verdere vraag zijn teruggekeerd.
