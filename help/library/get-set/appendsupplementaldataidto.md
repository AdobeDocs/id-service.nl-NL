---
description: Met deze hulpmethode kunt u de SDID (Supplemental Data ID) toevoegen als een querytekenreeksparameter aan een omleidings-URL. Dit is handig wanneer u A4T gebruikt en u de SDID van de ene pagina naar de andere wilt behouden en deze afzonderlijke bezoeken aan elkaar wilt koppelen. Om deze functie te gebruiken, moet u de dienst van identiteitskaart met zelfde Organisatie identiteitskaart op de bron en bestemmingsdomeinen hebben uitgevoerd.
keywords: ID Service
seo-description: Met deze hulpmethode kunt u de SDID (Supplemental Data ID) toevoegen als een querytekenreeksparameter aan een omleidings-URL. Dit is handig wanneer u A4T gebruikt en u de SDID van de ene pagina naar de andere wilt behouden en deze afzonderlijke bezoeken aan elkaar wilt koppelen. Om deze functie te gebruiken, moet u de dienst van identiteitskaart met zelfde Organisatie identiteitskaart op de bron en bestemmingsdomeinen hebben uitgevoerd.
seo-title: appendSupplementalDataIDTo
title: appendSupplementalDataIDTo
uuid: f3504d82-8da3-4971-818b-3df57df4ec2d
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# appendSupplementalDataIDTo{#appendsupplementaldataidto}

Met deze hulpmethode kunt u de SDID (Supplemental Data ID) toevoegen als een querytekenreeksparameter aan een omleidings-URL. Dit is handig wanneer u A4T gebruikt en u de SDID van de ene pagina naar de andere wilt behouden en deze afzonderlijke bezoeken aan elkaar wilt koppelen. Om deze functie te gebruiken, moet u de dienst van identiteitskaart met zelfde Organisatie identiteitskaart op de bron en bestemmingsdomeinen hebben uitgevoerd.

Inhoud:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> Syntaxis en codevoorbeeld </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4" format="dita" scope="local"> Voorbeelduitvoer </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> Syntaxis en codevoorbeeld </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-99946715cefa4acc95200b093db5297e" format="dita" scope="local"> De time-out van de SDID wijzigen met sdidParamExpiry </a> </li> 
</ul>

## Syntaxis en codevoorbeeld {#section-cbb0b2f73bcc418386796c24c01b2365}

**Syntaxis:** ` appendSupplementalDataIDTo( *``*, *`URLSDID`*)`

**Codevoorbeeld**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219");
```

## Voorbeelduitvoer {#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4}

Zoals hieronder getoond, bevat het omleiden URL SDID van de bezoeker, uw identiteitskaart van de Organisatie, en een timestamp van UNIX in de vraag aan de ontvangende pagina.

<ul class="simplelist"> 
 <li> <span class="codeph"> www.domain.com/pageB?adobe_mc_sdid=SDID=123|MCORGID=123456789@AdobeOrg|TS=1498569322 </span> </li> 
</ul>

## De time-out van de SDID wijzigen met sdidParamExpiry {#section-99946715cefa4acc95200b093db5297e}

Met de [configuratie doParamExpiry](../../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458) kunt u het standaard SDID-vervalinterval wijzigen wanneer u die id doorgeeft van de ene pagina naar de andere met behulp van de `appendSupplementalDataIDTo` hulpfunctie. Standaard heeft de ID-servicecode op de ontvangende pagina 30 seconden om de SDID op te halen van de URL die door de verwijzende pagina wordt verzonden. Als de de dienstcode van identiteitskaart op de ontvangende pagina niet SDID in minder dan 30 seconden kan terugwinnen vraagt het om een nieuwe SDID. Deze functionaliteit is vooral voor klanten A4T die SDID van één pagina aan een andere moeten overgaan en controle over dit onderbrekingsinterval willen.

Als u de standaardtime-out voor SDID moet wijzigen, voegt u `sdidParamExpiry` de volgende syntaxis toe aan de `Visitor.getInstance` functie:

**Syntaxis:** ` sdidParamExpiry: *`tijd in seconden`*`

**Codevoorbeeld**

Wanneer uw de dienstcode van identiteitskaart wordt gevormd kon aan deze steekproef gelijkaardig kijken. In dit voorbeeld wordt de SDID-time-out ingesteld op 15 seconden.

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Change the default SDID timeout to 15 seconds 
   sdidParamExpiry: 15 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219"); 
```

