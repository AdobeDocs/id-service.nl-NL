---
description: Verander de standaarddomeinnaam die door vraag aan de Dienst van de Identiteit van de Experience Cloud wordt gebruikt in uw eigen subdomeinnaam met deze configuraties die.
keywords: ID Service
seo-description: Verander de standaarddomeinnaam die door vraag aan de Dienst van de Identiteit van de Experience Cloud wordt gebruikt in uw eigen subdomeinnaam met deze configuraties die.
seo-title: publiekManagerServer en publiekManagerServerSecure
title: publiekManagerServer en publiekManagerServerSecure
uuid: e21cacbf-5151-4d34-b0f7-9e90275f4c7c
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 1%

---


# publiekManagerServer en publiekManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

Verander de standaarddomeinnaam die door vraag aan de Dienst van de Identiteit van de Experience Cloud wordt gebruikt in uw eigen subdomeinnaam met deze configuraties die.

**Syntaxis:**

* ` audienceManagerServer: " *`uw subdomeinnaam`*.demdex.net"`
* ` audienceManagerServerSecure: " *`uw subdomeinnaam`*.demdex.net"`

**Doel**

Normaal, doet de dienst van [!DNL Experience Cloud] identiteitskaart vraag aan [!DNL Adobe] bij `dpm.demdex.net`. Soms kunt u niet vraag aan deze bestemming willen maken omdat het te generisch of &quot;derde-partij.&quot;kijkt Om de de dienstvraag van identiteitskaart meer als een eerste vraag te maken kijken, gebruik deze configuraties om uw [!DNL Audience Manager] subdomeinnaam aan `demdex.net` zoals hieronder getoond toe te voegen. Voor meer informatie over de `dpm.demdex.net` vraag, zie het [Begrip van Vraag aan het Domein](https://docs.adobe.com/content/help/en/audience-manager/user-guide/reference/demdex-calls.html)van de Index.

**Vereisten**

Deze configuraties vereisen dat u gebruikt:

* De [!DNL Audience Manager] subdomeinnaam van verslag voor uw bedrijf. Verifieer of ontvang deze naam van uw consultant.
* De subdomeinnaam die aan uw [!UICONTROL Organization ID]bestand is gekoppeld.
* *Beide* configuratieparameters met de zelfde subdomeinnaam.

**Codevoorbeeld**

In dit voorbeeld hebben we een mediabedrijf dat juridische zorgen heeft geuit over het maken van oproepen naar `dpm.demdex.net`. In [!DNL Audience Manager], is de bedrijf subdomain naam van verslag Music1. Het volgende codevoorbeeld toont aan hoe te om de de dienstgegevensvraag van identiteitskaart met deze klant-specifieke subdomeinnaam te merken.

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

