---
description: Verander de standaarddomeinnaam die door vraag aan de Dienst van de Identiteit van de Experience Cloud wordt gebruikt in uw eigen subdomeinnaam met deze configuraties die.
keywords: ID-service
title: publiekManagerServer en publiekManagerServerSecure
exl-id: b740eb5c-ac4e-46f4-ba7c-1080d8d9292d
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 1%

---

# publiekManagerServer en publiekManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

Verander de standaarddomeinnaam die door vraag aan de Dienst van de Identiteit van de Experience Cloud wordt gebruikt in uw eigen subdomeinnaam met deze configuraties die.

**Syntaxis:**

* ` audienceManagerServer: " *`uw subdomeinnaam`*.demdex.net"`
* ` audienceManagerServerSecure: " *`uw subdomeinnaam`*.demdex.net"`

**Doel**

Normaal gesproken worden de [!DNL Experience Cloud] De dienst van identiteitskaart doet vraag aan [!DNL Adobe] om `dpm.demdex.net`. Soms kunt u niet vraag aan deze bestemming willen maken omdat het te generisch of &quot;derde-partij.&quot;kijkt Om de de dienstvraag van identiteitskaart te maken kijkt meer als een eerste-partijvraag, gebruik deze configuraties om uw toe te voegen [!DNL Audience Manager] subdomeinnaam naar `demdex.net` zoals hieronder weergegeven. Voor meer informatie over de `dpm.demdex.net` oproepen, zie [Inzicht krijgen in oproepen van het demdex-domein](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html).

**Vereisten**

Deze configuraties vereisen dat u gebruikt:

* De [!DNL Audience Manager] subdomeinnaam van record voor uw bedrijf. Verifieer of ontvang deze naam van uw consultant.
* De subdomeinnaam die aan uw [!UICONTROL Organization ID].
* *Beide* configuratieparameters met dezelfde subdomeinnaam.

**Codevoorbeeld**

In dit voorbeeld hebben we een mediabedrijf dat juridische zorgen heeft geuit over het oproepen van `dpm.demdex.net`. In [!DNL Audience Manager], de subdomeinnaam van het bedrijf van verslag is Music1. Het volgende codevoorbeeld toont aan hoe te om de de dienstgegevensvraag van identiteitskaart met deze klant-specifieke subdomeinnaam te merken.

```
//Instantiate Visitor 
var visitor = Visitor.getInstance("Insert Experience Cloud Organization ID here",{ 
     ... 
     //Configure ID service call 
     audienceManagerServer: "Music1.demdex.net", 
     audienceManagerServerSecure: "Music1.demdex.net" 
     } 
);
```
