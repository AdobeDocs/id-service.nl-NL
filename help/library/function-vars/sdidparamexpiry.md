---
description: Met deze configuratie kunt u het standaardvervalinterval voor aanvullende gegevens-id (SDID) overschrijven wanneer u die id doorgeeft van de ene pagina naar de andere met de hulpfunctie appendSupplementalDataIDTo. Standaard heeft de ID-servicecode op de ontvangende pagina 30 seconden om de SDID op te halen van de URL die door de verwijzende pagina wordt verzonden. Als de de dienstcode van identiteitskaart op de ontvangende pagina niet SDID in minder dan 30 seconden kan terugwinnen vraagt het om een nieuwe SDID. Deze functionaliteit is vooral voor klanten A4T die SDID van één pagina aan een andere moeten overgaan en controle over dit onderbrekingsinterval willen.
keywords: ID Service
seo-description: Met deze configuratie kunt u het standaardvervalinterval voor aanvullende gegevens-id (SDID) overschrijven wanneer u die id doorgeeft van de ene pagina naar de andere met de hulpfunctie appendSupplementalDataIDTo. Standaard heeft de ID-servicecode op de ontvangende pagina 30 seconden om de SDID op te halen van de URL die door de verwijzende pagina wordt verzonden. Als de de dienstcode van identiteitskaart op de ontvangende pagina niet SDID in minder dan 30 seconden kan terugwinnen vraagt het om een nieuwe SDID. Deze functionaliteit is vooral voor klanten A4T die SDID van één pagina aan een andere moeten overgaan en controle over dit onderbrekingsinterval willen.
seo-title: sdidParamExpiry
title: sdidParamExpiry
uuid: cdaf7e2d-b196-4c70-936d-8a98191cbb85
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---


# sdidParamExpiry{#sdidparamexpiry}

Met deze configuratie kunt u het standaardvervalinterval voor aanvullende gegevens-id (SDID) overschrijven wanneer u die id doorgeeft van de ene pagina naar de andere met de hulpfunctie appendSupplementalDataIDTo. Standaard heeft de ID-servicecode op de ontvangende pagina 30 seconden om de SDID op te halen van de URL die door de verwijzende pagina wordt verzonden. Als de de dienstcode van identiteitskaart op de ontvangende pagina niet SDID in minder dan 30 seconden kan terugwinnen vraagt het om een nieuwe SDID. Deze functionaliteit is vooral voor klanten A4T die SDID van één pagina aan een andere moeten overgaan en controle over dit onderbrekingsinterval willen.

**De time-out voor SDID overschrijven**

Als u de standaardtime-out voor SDID moet wijzigen, voegt u `sdidParamExpiry` de volgende syntaxis toe aan de `Visitor.getInstance` functie:

**Syntaxis:** ` sdidParamExpiry: *`tijd in seconden`*`

**Codevoorbeeld**

Wanneer gevormd, kon uw de dienstcode van identiteitskaart aan deze steekproef gelijkaardig kijken. In dit voorbeeld wordt de SDID-time-out ingesteld op 15 seconden. Deze configuratie werkt met de [hulpmethode appendSupplementalDataIDTo](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d) .

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

