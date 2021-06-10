---
description: Verander de standaarddomeinnaam die door vraag aan de Dienst van de Identiteit van de Experience Cloud wordt gebruikt in uw eigen subdomeinnaam met deze configuraties die.
keywords: ID-service
title: publiekManagerServer en publiekManagerServerSecure
exl-id: b740eb5c-ac4e-46f4-ba7c-1080d8d9292d
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 1%

---

# publiekManagerServer en publiekManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

Verander de standaarddomeinnaam die door vraag aan de Dienst van de Identiteit van de Experience Cloud wordt gebruikt in uw eigen subdomeinnaam met deze configuraties die.

**Syntaxis:**

* ` audienceManagerServer: " *`uw subdomeinnaam`*.demdex.net"`
* ` audienceManagerServerSecure: " *`uw subdomeinnaam`*.demdex.net"`

**Doel**

Normaal, doet de [!DNL Experience Cloud] dienst van identiteitskaart vraag aan [!DNL Adobe] bij `dpm.demdex.net`. Soms kunt u niet vraag aan deze bestemming willen maken omdat het te generisch of &quot;derde-partij.&quot;kijkt Om de de dienstvraag van identiteitskaart meer als een vraag van de eerste partij te maken, gebruik deze configuraties om uw [!DNL Audience Manager] subdomeinnaam aan `demdex.net` zoals hieronder getoond toe te voegen. Voor meer informatie over de `dpm.demdex.net` vraag, zie [Begrijpende Vraag aan het Domein van de Index](https://docs.adobe.com/content/help/en/audience-manager/user-guide/reference/demdex-calls.html).

**Vereisten**

Deze configuraties vereisen dat u gebruikt:

* De [!DNL Audience Manager] subdomeinnaam van verslag voor uw bedrijf. Verifieer of ontvang deze naam van uw consultant.
* De subdomeinnaam die is gekoppeld aan uw [!UICONTROL Organization ID].
* ** Beide configuratieparameters met dezelfde subdomeinnaam.

**Codevoorbeeld**

In dit voorbeeld hebben we een mediabedrijf dat juridische zorgen heeft geuit over het oproepen van `dpm.demdex.net`. In [!DNL Audience Manager] is de subdomeinnaam van het bedrijf van verslag Music1. Het volgende codevoorbeeld toont aan hoe te om de de dienstgegevensvraag van identiteitskaart met deze klant-specifieke subdomeinnaam te merken.

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
