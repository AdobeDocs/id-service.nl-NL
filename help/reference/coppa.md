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

# COPPA-ondersteuning in de Experience Cloud Identity Service {#coppa-support-in-the-experience-cloud-id-service}

De wet ter bescherming van de online privacy van kinderen (COPPA) verbiedt het online verzamelen van persoonsgegevens van kinderen onder de 13 jaar zonder controleerbare toestemming van de ouders. Klanten die zich zorgen maken over COPPA, kunnen een optionele variabele toevoegen aan hun code voor identiteitsservice van Experience Cloud, waardoor het niet mogelijk is cookies in het domein van derden van een browser in te stellen.

>[!NOTE]
>
>Voor versie 3.0.0 of hoger.

**Cookies en reeksspatiëring**

Wanneer een webpagina wordt geladen, wordt [!DNL Experience Cloud] ID-service roept een [!DNL Adobe] gegevensverzamelingsserver (DCS). De DCS-reactie bevat een Experience Cloud cookie en een demdex.net cookie.

* Het Experience Cloud-cookie wordt ingesteld in het eerste partijdomein. Het kan niet worden gebruikt om bezoekers over verschillende domeinen te volgen, tenzij die domeinen samenwerken om toegang toe te staan.
* Het cookie demdex.net wordt ingesteld in het domein van derden. Het bevat een unieke id die kan worden gebruikt om bezoekers in verschillende domeinen te volgen.

**Cookies en COPPA-compatibiliteit**

Cookies van derden die bezoekers in verschillende domeinen volgen op websites die naar (of primair voor) kinderen zijn gericht, activeren de vereisten voor toestemming door de ouders van de COPPA. Als u gemakkelijker wilt voldoen aan COPPA voor interne websiteanalyse, voegt u de variabele toe `disableThirdPartyCookies:true` aan de `Visitor.getInstance` zoals hieronder getoond.

```js
//Call the ID service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

Wanneer ingesteld op `true`de `disableThirdPartyCookies` object voorkomt dat de DCS het cookie demdex.net van een derde retourneert. Als een sitebezoeker deze cookie al in zijn browser heeft, gebruikt de id-service deze niet om een nieuwe cookie te maken [!DNL Experience Cloud] ID of retourneer een bestaande id. In plaats daarvan [!DNL Experience Cloud] De dienst van identiteitskaart leidt tot een nieuwe, willekeurige identiteitskaart in het eerste-partijkoekje. Als deze optie is ingeschakeld, kunt u gegevens verzamelen met de id-service en deze delen over verschillende [!DNL Experience Cloud] oplossingen, met inbegrip van andere interne operaties die door COPPA zijn toegestaan.

>[!MORELIKETHIS]
>
>* [Adobe Privacy Center](http://www.adobe.com/privacy.html)
>* [Wat is COPPA?](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

