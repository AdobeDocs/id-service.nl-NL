---
description: Met deze configuratie kunt u de cloud-id's (ECID's) voor weesse of oudere beleving wissen op basis van de versie van de id-service die wordt bijgewerkt.
keywords: ID Service
seo-description: Met deze configuratie kunt u de cloud-id's (ECID's) voor weesse of oudere beleving wissen op basis van de versie van de id-service die wordt bijgewerkt.
seo-title: resetBeforeVersion
title: resetBeforeVersion
uuid: b00d18b8-6720-42f9-9c83-bd306184cc0c
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# resetBeforeVersion{#resetbeforeversion}

Met deze configuratie kunt u de cloud-id&#39;s (ECID&#39;s) voor weesse of oudere beleving wissen op basis van de versie van de id-service die wordt bijgewerkt.

Het verstrekken van uw versie van de Dienst van identiteitskaart als waarde van de `resetBeforeVersion` variabele zal ervoor zorgen dat verouderde ECIDs van cliënt-kant IDs wordt ontruimd.

Sommige voorwaarden, zoals sessietime-outs, kunnen er soms toe leiden dat een client-side id wordt gegenereerd zonder dat de id-service een server-side id heeft opgehaald. Wanneer dit gebeurt, wordt een verweesde cliënt-zijidentiteitskaart gevolgd door de Dienst van identiteitskaart zonder de capaciteit over domeinen of behoorlijk synchronisatie met andere oplossingen worden gevolgd. Het gedrag vergelijkt de versie in het huidige cookie van AMCV met de waarde van `resetBeforeVersion`. Als het cookie niet bestaat of als de versie van het cookie minder (ouder) is dan de meest recente versie van `resetBeforeVersion`het cookie, wordt het AMCV-cookie verwijderd en vraagt de ID-service om een nieuwe ECID.

Voor bezoekers die demdex-cookies van derden in hun browser hebben, wordt de ECID gecontroleerd om te zien of deze correct is gegenereerd met de UUID in het demdex-cookie. Als die controle waar blijkt te zijn, zal de nieuwe ECID hetzelfde zijn en zal de bezoeker als nieuw worden beschouwd. Als om een of andere reden de ECID die wordt gewist niet is gegenereerd met het demdex-cookie, of als er geen Demdex-cookie is, zal de bezoeker een nieuwe ECID ontvangen en als nieuw worden beschouwd.

**Syntaxis:** `resetBeforeVersion = "3.3"`

**Codevoorbeeld**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Marketing Cloud organization ID here", { 
  
    //Same as s.trackingServer 
    trackingServer: "Insert tracking server here ", 
  
    //Same as s.trackingServerSecure 
    trackingServerSecure: "Insert secure tracking server here", 
  
    //For CNAME support only. Exclude these variables if you're not using CNAME 
    marketingCloudServer: "Insert tracking server here", 
    marketingCloudServerSecure: "Insert secure tracking server here", 
  
    //Changing the version 
    resetBeforeVersion: "3.3" 
});
```

