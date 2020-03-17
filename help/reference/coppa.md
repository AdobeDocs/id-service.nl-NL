---
description: De wet ter bescherming van de online privacy van kinderen (COPPA) verbiedt het online verzamelen van persoonsgegevens van kinderen onder de 13 jaar zonder controleerbare toestemming van de ouders. Klanten die zich zorgen maken over COPPA, kunnen een optionele variabele toevoegen aan hun Code Experience Cloud Identity Service, waardoor deze geen cookies kan instellen in het domein van derden van een browser.
keywords: ID Service
seo-description: De wet ter bescherming van de online privacy van kinderen (COPPA) verbiedt het online verzamelen van persoonsgegevens van kinderen onder de 13 jaar zonder controleerbare toestemming van de ouders. Klanten die zich zorgen maken over COPPA, kunnen een optionele variabele toevoegen aan hun Code Experience Cloud Identity Service, waardoor deze geen cookies kan instellen in het domein van derden van een browser.
seo-title: Ondersteuning voor COPPA in de Experience Cloud Identity Service
title: Ondersteuning voor COPPA in de Experience Cloud Identity Service
uuid: 621b5ebd-92e7-4635-be85-8d7e36589fcb
translation-type: tm+mt
source-git-commit: c4c0b791230422f17292b72fd45ba5689a60adae

---


# COPPA Support in the Experience Cloud Identity Service {#coppa-support-in-the-experience-cloud-id-service}

De wet ter bescherming van de online privacy van kinderen (COPPA) verbiedt het online verzamelen van persoonsgegevens van kinderen onder de 13 jaar zonder controleerbare toestemming van de ouders. Klanten die zich zorgen maken over COPPA, kunnen een optionele variabele toevoegen aan hun Code Experience Cloud Identity Service, waardoor deze geen cookies kan instellen in het domein van derden van een browser.

>[!NOTE]
>
>Voor versie 3.0.0 of hoger.

**Cookies en reeksspatiëring**

Wanneer een Web-pagina laadt, roept de dienst van [!DNL Experience Cloud] identiteitskaart een server van de [!DNL Adobe] gegevensinzameling (DCS). De DCS-reactie bevat een Experience Cloud-cookie en een demdex.net-cookie.

* Het cookie van de Experience Cloud wordt ingesteld in het domein van de eerste partij. Het kan niet worden gebruikt om bezoekers over verschillende domeinen te volgen, tenzij die domeinen samenwerken om toegang toe te staan.
* Het cookie demdex.net wordt ingesteld in het domein van derden. Het bevat een unieke id die kan worden gebruikt om bezoekers in verschillende domeinen te volgen.

**Cookies en COPPA-compatibiliteit**

Cookies van derden die bezoekers in verschillende domeinen volgen op websites die naar (of primair voor) kinderen zijn gericht, activeren de vereisten voor toestemming door de ouders van de COPPA. Als u gemakkelijker wilt voldoen aan COPPA voor interne websiteanalyse, voegt u de variabele `disableThirdPartyCookies:true` aan de `Visitor.getInstance` functie toe, zoals hieronder wordt weergegeven.

```js
//Call the ID service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

Wanneer ingesteld op `true`, stopt het `disableThirdPartyCookies` object de DCS van het retourneren van het cookie demdex.net van derden. Als een sitebezoeker deze cookie al in zijn browser heeft, gebruikt de id-service deze niet om een nieuwe [!DNL Experience Cloud] id te maken of een bestaande id te retourneren. In plaats daarvan maakt de [!DNL Experience Cloud] id-service een nieuwe, willekeurige id in het cookie van de eerste partij. Zodra toegelaten, kunt u gegevens met de dienst van identiteitskaart verzamelen en het over verschillende [!DNL Experience Cloud] oplossingen, met inbegrip van andere interne verrichtingen delen die door COPPA worden toegestaan.

>[!MORELIKETHIS]
>
>* [Adobe Privacy Center](http://www.adobe.com/privacy.html)
>* [Wat is COPPA?](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

