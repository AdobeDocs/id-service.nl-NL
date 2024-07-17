---
description: Met deze hulpmethode kunt u de SDID (Supplemental Data ID) toevoegen als een querytekenreeksparameter aan een omleidings-URL. Dit is handig wanneer u A4T gebruikt en u de SDID van de ene pagina naar de andere wilt behouden en deze afzonderlijke bezoeken aan elkaar wilt koppelen. Om deze functie te gebruiken, moet u de dienst van identiteitskaart met zelfde Organisatie identiteitskaart op de bron en bestemmingsdomeinen hebben uitgevoerd.
keywords: ID-service
title: appendSupplementalDataIDTo
exl-id: 7f0e7fca-4551-4165-a12b-c7e5514d6818
source-git-commit: 5710539b45a81394061cd4af2ef3edc27b49092e
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# appendSupplementalDataIDTo{#appendsupplementaldataidto}

Met deze hulpmethode kunt u de SDID (Supplemental Data ID) toevoegen als een querytekenreeksparameter aan een omleidings-URL. Dit is handig wanneer u A4T gebruikt en u de SDID van de ene pagina naar de andere wilt behouden en deze afzonderlijke bezoeken aan elkaar wilt koppelen. Om deze functie te gebruiken, moet u de dienst van identiteitskaart met zelfde Organisatie identiteitskaart op de bron en bestemmingsdomeinen hebben uitgevoerd.

Inhoud:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> Syntaxis en codevoorbeeld </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4" format="dita" scope="local"> Voorbeelduitvoer </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> Syntaxis en codevoorbeeld </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-99946715cefa4acc95200b093db5297e" format="dita" scope="local"> De time-out van de SDID wijzigen met soundParamExpiry </a> </li> 
</ul>

## Syntaxis en codevoorbeeld {#section-cbb0b2f73bcc418386796c24c01b2365}

**Syntaxis:** ` appendSupplementalDataIDTo( *` URL `*, *` SDID `*)`

**Steekproef van de Code**

```js
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here"); 

//Get current supplemental data id
var theCurrentSDID = visitor._supplementalDataIDCurrent ? visitor._supplementalDataIDCurrent : "";

//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, theCurrentSDID));
```

## Voorbeelduitvoer {#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4}

Zoals hieronder getoond, bevat het omleiden URL SDID van de bezoeker, uw identiteitskaart van de Organisatie, en een timestamp van UNIX in de vraag aan de ontvangende pagina.

<ul class="simplelist"> 
 <li> <span class="codeph"> www.domain.com/pageB?adobe_mc_sdid=SDID=7996F0B028999505-13DA591039D6226|MCORGID=123456789@AdobeOrg|TS=1498569322 </span> </li> 
</ul>

## De time-out van de SDID wijzigen met sdidParamExpiry {#section-99946715cefa4acc95200b093db5297e}

De ](../../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458) configuratie 0} sdidParamExpiry laat u het standaardinterval van de vervaldatum veranderen SDID wanneer het overgaan van die identiteitskaart van één pagina aan een andere gebruikend de `appendSupplementalDataIDTo` hulpfunctie. [ Standaard heeft de ID-servicecode op de ontvangende pagina 30 seconden om de SDID op te halen van de URL die door de verwijzende pagina wordt verzonden. Als de de dienstcode van identiteitskaart op de ontvangende pagina niet SDID in minder dan 30 seconden kan terugwinnen vraagt het om een nieuwe SDID. Deze functionaliteit is vooral voor klanten A4T die SDID van één pagina aan een andere moeten overgaan en controle over dit onderbrekingsinterval willen.

Als u de standaardtime-out voor SDID wilt wijzigen, voegt u `sdidParamExpiry` toe aan de functie `Visitor.getInstance` met de volgende syntaxis:

**Syntaxis:** ` sdidParamExpiry: *` tijd in seconden `*`

**Steekproef van de Code**

Wanneer uw de dienstcode van identiteitskaart wordt gevormd kon aan deze steekproef gelijkaardig kijken. In dit voorbeeld wordt de SDID-time-out ingesteld op 15 seconden.

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Change the default SDID timeout to 15 seconds 
   sdidParamExpiry: 15 
}); 
 
//Get current supplemental data id
var theCurrentSDID = visitor._supplementalDataIDCurrent ? visitor._supplementalDataIDCurrent : "";

//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, theCurrentSDID)); 
```
