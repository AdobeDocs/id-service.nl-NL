---
description: Alvorens de Dienst van de Identiteit van het Experience Cloud op te stellen, zou u moeten begrijpen hoe deze dienst bezoekers het volgen op veelvoudige domeinen en potentiële kwesties beïnvloedt als u gegevens met verschillende methodes of door de dossiers van JavaScript verzamelt.
keywords: ID-service
title: Experience Cloud Identity Service Migration Decision Points
exl-id: f2802db2-c95f-476f-8c60-f45e8312253c
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%

---

# Experience Cloud Identity Service Migration Decision Points

Alvorens de Dienst van de Identiteit van het Experience Cloud op te stellen, zou u moeten begrijpen hoe deze dienst bezoekers het volgen op veelvoudige domeinen en potentiële kwesties beïnvloedt als u gegevens met verschillende methodes of door de dossiers van JavaScript verzamelt.

Op basis van de antwoorden op de vragen in deze sectie kunt u bepalen welke aanvullende migratiestappen u moet uitvoeren.

## Hebt u een CNAME van de gegevensinzameling?

Vele klanten kunnen zich van een CNAME van de gegevensinzameling als deel van de de dienstmigratie van identiteitskaart migreren.

<table id="table_13F7C1E3D64D4F86B0149C9D3B54AADD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Methode voor gegevensverzameling </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Met een CNAME </p> </td> 
   <td colname="col2"> <p>Zie de volgende vraag om te beslissen als u zich vanaf een gegevensinzameling CNAME zou moeten migreren. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Zonder een CNAME </p> </td> 
   <td colname="col2"> <p>Overslaan naar <a href="../../reference/analytics-reference/migration-decisions.md#section-34dabde7780e4a339f134c0ca7768961" format="dita" scope="local"> Als u geen CNAME voor gegevensverzameling hebt, is dit dan de server voor gegevensverzameling *.2o7.net of *.sc.omtrdc.net?</a> . </p> </td> 
  </tr> 
 </tbody> 
</table>

## Als u een CNAME van de gegevensinzameling hebt, hebt u veelvoudige domeinen?

Als u veelvoudige domeinen hebt die gegevens naar *zelfde rapportreeks* verzenden, dan adviseren wij gegevensinzameling met een NAAM. Zo kunt u bezoekers in verschillende domeinen volgen. Als u gegevens over één enkel domein verzamelt, is er geen voordeel aan het handhaven van een CNAME van de gegevensinzameling.

<table id="table_D132BCA243E54657AEC930559343FDD3"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Gegevens verzamelen van </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Meerdere domeinen </p> </td> 
   <td colname="col2"> <p>Als u bezoekers in meerdere domeinen bijhoudt en u ook een hoofdinvoersite hebt waarop klanten kunnen worden geïdentificeerd voordat ze andere domeinen bezoeken, moet u de CNAME voor de gegevensverzameling blijven gebruiken. <!--See <a href="../../reference/analytics-reference/cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d" format="dita" scope="local"> Data Collection CNAMES and Cross Domain Tracking</a> for a detailed explanation.--> </p> <p>Merk op dat u twee extra het volgen-server parameters, <span class="codeph"> bezoekor.marketingCloudServer </span> en <span class="codeph"> bezoeker.marketingCloudServerSecure </span> moet specificeren, om een NAAM met de dienst van identiteitskaart te vormen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Eén domein </p> </td> 
   <td colname="col2"> <p>Als u met één domein werkt, kunt u migreren van een CNAME voor gegevensverzameling als u dit niet meer wilt beheren. Nochtans, is er geen vereiste om te veranderen als uw CNAME werkt. </p> <p>Als u CNAME verwijdert: </p> 
    <ul id="ul_12CDECEFC7BB41A18895B507CAA42315"> 
     <li id="li_32E2CD3E58454E20A642BADE507AE86E">Zorg ervoor uw nieuwe het volgen server <a href="https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html" format="https" scope="external"> RDC volgzaam </a> is. </li> 
     <li id="li_865BB6DAA3594EBBAB688E73C8343762">Ga van CNAME aan een RDC volgende server een paar maanden vóór uw migratie naar de <span class="keyword"> Experience Cloud </span> dienst van identiteitskaart over. </li> 
     <li id="li_284A015177554C848C8648DC5BBAA365"> <i> gebruik niet </i> a <span class="codeph"> *.2o7.net </span> volgende server. </li> 
     <li id="li_B1ABF03DC46C42059F61542CDE0FE5A1">Neem contact op met de <a href="https://helpx.adobe.com/marketing-cloud/contact-support.html" format="https" scope="external"> klantenservice </a> om een bezoekersmigratie in te stellen. Hierdoor is het aantal bezoekers consistent. </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Hebt u meerdere Analytics JavaScript-bestanden of volgt u Flash-toepassingen of -video&#39;s?

Als u de veelvoudige dossiers of de toepassingen of de video&#39;s van JavaScript van de Analyse over uw plaats hebt die gegevens naar de *zelfde rapportreeks* verzenden, zou u een respijtperiode moeten vormen zodat de bezoekers door analytische identiteitskaart blijven worden geïdentificeerd terwijl u de [!DNL Experience Cloud] dienst van identiteitskaart uitrollen.

<table id="table_8A4EA063AF4345B69BC98537E2E702BA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Gegevensverzameling met </th> 
   <th colname="col2" class="entry"> Vereiste handelingen </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> 
    <ul id="ul_910DD99E074E49C6907F86426EFA5BF2"> 
     <li id="li_4366CC8EB7A54A959568E3761ABBBF23">Meerdere JavaScript-analysebestanden </li> 
     <li id="li_B8A8132019EA48088E4F37E36F153D76">Andere methoden voor gegevensverzameling </li> 
    </ul> </td> 
   <td colname="col2"> <p>U moet een respijtperiode voor de bezoekersidentiteitsservice configureren, zodat u de service met de bezoekersidentiteitskaart kunt inzetten voor elk JavaScript-bestand en andere bibliotheken voor gegevensverzameling. Zie <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> Uitstelperiode van de Dienst van identiteitskaart </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Eén JavaScript-bestand voor Analytics </p> </td> 
   <td colname="col2"> <p>U kunt één JavaScript-bestand bijwerken zodat de service bezoekersidentiteitskaart zonder respijtperiode wordt gebruikt. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Gebruikt u niet-ondersteunde methoden voor gegevensverzameling?

Mogelijk moet u de manier bijwerken waarop u koppelingen bijhoudt of een migratie uitvoeren naar een andere locatie dan Sliverlight.

<table id="table_A72AEB92F48345DD83F136B9989F4EF9"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Methode voor gegevensverzameling </th> 
   <th colname="col2" class="entry"> Vereiste handelingen </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>JavaScript en/of Flash </p> </td> 
   <td colname="col2"> <p>Geen. De <span class="keyword"> Experience Cloud </span> dienst van identiteitskaart steunt deze methodes van de gegevensinzameling. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Silverlight </p> </td> 
   <td colname="col2"> <p>U moet weg van Silverlight migreren als de bezoekers tot inhoud Silverlight en andere secties van uw plaats kunnen toegang hebben die de <span class="keyword"> dienst van identiteitskaart van de Experience Cloud </span> gebruiken. Silverlight wordt niet ondersteund door de id-service. </p> <p> Als u een op Silverlight gebaseerde videospeler bijhoudt, biedt de leverancier waarschijnlijk JavaScript API's die u in plaats daarvan kunt gebruiken. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Gecodeerde afbeeldingstags </p> </td> 
   <td colname="col2"> <p>Werk hard-gecodeerde verbindingen bij om JavaScript te gebruiken. </p> </td> 
  </tr> 
 </tbody> 
</table>
