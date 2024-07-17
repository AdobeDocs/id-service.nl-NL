---
description: De wet ter bescherming van de online privacy van kinderen (COPPA) verbiedt het online verzamelen van persoonsgegevens van kinderen onder de 13 jaar zonder controleerbare toestemming van de ouders. Klanten die zich zorgen maken over COPPA kunnen een optionele variabele toevoegen aan hun code voor identiteitsservice van Experiencen Cloud die verhindert dat deze cookies kan instellen in het domein van derden van een browser.
keywords: ID-service
title: COPPA-ondersteuning in de identiteitsservice van het Experience Cloud
exl-id: c7579f90-3011-4e26-b908-08907bf12ba2
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# COPPA-ondersteuning in de identiteitsservice van het Experience Cloud {#coppa-support-in-the-experience-cloud-id-service}

De wet ter bescherming van de online privacy van kinderen (COPPA) verbiedt het online verzamelen van persoonsgegevens van kinderen onder de 13 jaar zonder controleerbare toestemming van de ouders. Klanten die zich zorgen maken over COPPA kunnen een optionele variabele toevoegen aan hun code voor identiteitsservice van Experiencen Cloud die verhindert dat deze cookies kan instellen in het domein van derden van een browser.

>[!NOTE]
>
>Voor versie 3.0.0 of hoger.

**Cookies en het Volgen**

Wanneer een webpagina wordt geladen, roept de [!DNL Experience Cloud] ID-service een [!DNL Adobe] Data Collection Server (DCS) aan. De DCS-reactie bevat een Experience Cloud cookie en een demdex.net cookie.

* Het Experience Cloud cookie wordt ingesteld in het eerste partijdomein. Het kan niet worden gebruikt om bezoekers over verschillende domeinen te volgen, tenzij die domeinen samenwerken om toegang toe te staan.
* Het cookie demdex.net wordt ingesteld in het domein van derden. Het bevat een unieke id die kan worden gebruikt om bezoekers in verschillende domeinen te volgen.

**Cookies en de Naleving COPPA**

Cookies van derden die bezoekers in verschillende domeinen volgen op websites die naar (of primair voor) kinderen zijn gericht, activeren de vereisten voor toestemming door de ouders van de COPPA. Als u gemakkelijker wilt voldoen aan COPPA voor interne websiteanalyse, voegt u de variabele `disableThirdPartyCookies:true` toe aan de functie `Visitor.getInstance` , zoals hieronder wordt weergegeven.

```js
//Call the ID service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

Wanneer dit object is ingesteld op `true` , voorkomt het `disableThirdPartyCookies` -object dat de DCS het cookie van de externe gebruiker demdex.net retourneert. Als een sitebezoeker deze cookie al in zijn browser heeft, gebruikt de id-service deze niet om een nieuwe [!DNL Experience Cloud] -id te maken of een bestaande id te retourneren. In plaats daarvan maakt de [!DNL Experience Cloud] ID-service een nieuwe, willekeurige id in het cookie van de eerste partij. Als deze optie is ingeschakeld, kunt u gegevens verzamelen met de id-service en deze delen met verschillende [!DNL Experience Cloud] -oplossingen, waaronder andere interne bewerkingen die zijn toegestaan door COPPA.

>[!MORELIKETHIS]
>
>* [ het Centrum van de Privacy van de Adobe ](http://www.adobe.com/privacy.html)
>* [ wat is COPPA?](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)
