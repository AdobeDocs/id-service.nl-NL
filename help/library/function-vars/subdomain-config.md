---
description: Verander de standaarddomeinnaam die door vraag aan de Dienst van de Identiteit van het Experience Cloud in uw eigen subdomeinnaam met deze configuraties wordt gebruikt.
keywords: ID-service
title: publiekManagerServer en publiekManagerServerSecure
exl-id: b740eb5c-ac4e-46f4-ba7c-1080d8d9292d
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# publiekManagerServer en publiekManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

Verander de standaarddomeinnaam die door vraag aan de Dienst van de Identiteit van het Experience Cloud in uw eigen subdomeinnaam met deze configuraties wordt gebruikt.

**Syntaxis:**

* ` audienceManagerServer: " *` uw subdomeinnaam `*.demdex.net"`
* ` audienceManagerServerSecure: " *` uw subdomeinnaam `*.demdex.net"`

**Doel**

Normaal gesproken roept de [!DNL Experience Cloud] ID-service [!DNL Adobe] at `dpm.demdex.net` aan. Soms kunt u niet vraag aan deze bestemming willen maken omdat het te generisch of &quot;derde-partij.&quot;kijkt Als u wilt dat de aanroep van de id-service er meer uitziet als een aanroep van een eerste partij, gebruikt u deze configuraties om de [!DNL Audience Manager] subdomeinnaam aan `demdex.net` toe te voegen, zoals hieronder wordt weergegeven. Voor meer informatie over de `dpm.demdex.net` vraag, zie [ Begrijpende Vraag aan het Domein van de Index ](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=nl-NL).

**Vereisten**

Deze configuraties vereisen dat u gebruikt:

* De [!DNL Audience Manager] subdomeinnaam van record voor uw bedrijf. Verifieer of ontvang deze naam van uw consultant.
* De subdomeinnaam die aan uw [!UICONTROL Organization ID] is gekoppeld.
* *allebei* configuratieparameters met de zelfde subdomeinnaam.

**Steekproef van de Code**

In dit voorbeeld hebben we een mediabedrijf dat juridische zorgen heeft geuit over het oproepen van `dpm.demdex.net`. In [!DNL Audience Manager] is de subdomeinnaam van het bedrijf van record Music1. Het volgende codevoorbeeld toont aan hoe te om de de dienstgegevensvraag van identiteitskaart met deze klant-specifieke subdomeinnaam te merken.

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
