---
description: Met deze configuratie kunt u het standaardvervalinterval voor aanvullende gegevens-id (SDID) overschrijven wanneer u die id doorgeeft van de ene pagina naar de andere met de hulpfunctie appendSupplementalDataIDTo. Standaard heeft de ID-servicecode op de ontvangende pagina 30 seconden om de SDID op te halen van de URL die door de verwijzende pagina wordt verzonden. Als de de dienstcode van identiteitskaart op de ontvangende pagina niet SDID in minder dan 30 seconden kan terugwinnen vraagt het om een nieuwe SDID. Deze functionaliteit is vooral voor klanten A4T die SDID van één pagina aan een andere moeten overgaan en controle over dit onderbrekingsinterval willen.
keywords: ID-service
title: sdidParamExpiry
exl-id: 5458ffa5-03d1-4c52-907d-c50fe00ce35d
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# sdidParamExpiry{#sdidparamexpiry}

Met deze configuratie kunt u het standaardvervalinterval voor aanvullende gegevens-id (SDID) overschrijven wanneer u die id doorgeeft van de ene pagina naar de andere met de hulpfunctie appendSupplementalDataIDTo. Standaard heeft de ID-servicecode op de ontvangende pagina 30 seconden om de SDID op te halen van de URL die door de verwijzende pagina wordt verzonden. Als de de dienstcode van identiteitskaart op de ontvangende pagina niet SDID in minder dan 30 seconden kan terugwinnen vraagt het om een nieuwe SDID. Deze functionaliteit is vooral voor klanten A4T die SDID van één pagina aan een andere moeten overgaan en controle over dit onderbrekingsinterval willen.

**met voeten treedt de Onderbreking SDID**

Als u de standaardtime-out voor SDID wilt wijzigen, voegt u `sdidParamExpiry` toe aan de functie `Visitor.getInstance` met de volgende syntaxis:

**Syntaxis:** ` sdidParamExpiry: *` tijd in seconden `*`

**Steekproef van de Code**

Wanneer gevormd, kon uw de dienstcode van identiteitskaart aan deze steekproef gelijkaardig kijken. In dit voorbeeld wordt de SDID-time-out ingesteld op 15 seconden. Deze configuratie werkt met [ appendSupplementalDataIDTo ](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d) helpermethode.

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
