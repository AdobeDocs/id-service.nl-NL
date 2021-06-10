---
description: De wet ter bescherming van de online privacy van kinderen (COPPA) verbiedt het online verzamelen van persoonsgegevens van kinderen onder de 13 jaar zonder controleerbare toestemming van de ouders. Klanten die zich zorgen maken over COPPA, kunnen een optionele variabele toevoegen aan hun code voor identiteitsservice van Experience Cloud, waardoor het niet mogelijk is cookies in het domein van derden van een browser in te stellen.
keywords: ID-service
title: COPPA-ondersteuning in de Experience Cloud Identity Service
exl-id: c7579f90-3011-4e26-b908-08907bf12ba2
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# COPPA-ondersteuning in de Experience Cloud Identity-service {#coppa-support-in-the-experience-cloud-id-service}

De wet ter bescherming van de online privacy van kinderen (COPPA) verbiedt het online verzamelen van persoonsgegevens van kinderen onder de 13 jaar zonder controleerbare toestemming van de ouders. Klanten die zich zorgen maken over COPPA, kunnen een optionele variabele toevoegen aan hun code voor identiteitsservice van Experience Cloud, waardoor het niet mogelijk is cookies in het domein van derden van een browser in te stellen.

>[!NOTE]
>
>Voor versie 3.0.0 of hoger.

**Cookies en reeksspatiëring**

Wanneer een webpagina wordt geladen, roept de [!DNL Experience Cloud]-id-service een [!DNL Adobe]-gegevensverzamelingsserver (DCS) aan. De DCS-reactie bevat een Experience Cloud cookie en een demdex.net cookie.

* Het Experience Cloud-cookie wordt ingesteld in het eerste partijdomein. Het kan niet worden gebruikt om bezoekers over verschillende domeinen te volgen, tenzij die domeinen samenwerken om toegang toe te staan.
* Het cookie demdex.net wordt ingesteld in het domein van derden. Het bevat een unieke id die kan worden gebruikt om bezoekers in verschillende domeinen te volgen.

**Cookies en COPPA-compatibiliteit**

Cookies van derden die bezoekers in verschillende domeinen volgen op websites die naar (of primair voor) kinderen zijn gericht, activeren de vereisten voor toestemming door de ouders van de COPPA. Als u gemakkelijker wilt voldoen aan COPPA voor interne websiteanalyse, voegt u de variabele `disableThirdPartyCookies:true` toe aan de functie `Visitor.getInstance`, zoals hieronder wordt weergegeven.

```js
//Call the ID service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

Wanneer ingesteld op `true`, stopt het object `disableThirdPartyCookies` de DCS van het retourneren van het cookie demdex.net van derden. Als een sitebezoeker dit cookie al in zijn browser heeft, gebruikt de id-service dit niet om een nieuwe [!DNL Experience Cloud]-id te maken of een bestaande id te retourneren. In plaats daarvan maakt de [!DNL Experience Cloud] ID-service een nieuwe, willekeurige id in het cookie van de eerste partij. Zodra toegelaten, kunt u gegevens met de dienst van identiteitskaart verzamelen en het over verschillende [!DNL Experience Cloud] oplossingen, met inbegrip van andere interne verrichtingen delen die door COPPA worden toegestaan.

>[!MORELIKETHIS]
>
>* [Adobe Privacy Center](http://www.adobe.com/privacy.html)
>* [Wat is COPPA?](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

