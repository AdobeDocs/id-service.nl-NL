---
description: Voordat u de Experience Cloud Identity Service gaat implementeren, moet u begrijpen hoe deze service het bijhouden van bezoekers op meerdere domeinen en mogelijke problemen beïnvloedt als u gegevens verzamelt met verschillende methoden of via JavaScript-bestanden.
keywords: ID Service
seo-description: Voordat u de Experience Cloud Identity Service gaat implementeren, moet u begrijpen hoe deze service het bijhouden van bezoekers op meerdere domeinen en mogelijke problemen beïnvloedt als u gegevens verzamelt met verschillende methoden of via JavaScript-bestanden.
seo-title: Ervaar de beslissingspunten voor migratie van de cloudidentiteitsservice
title: Ervaar de beslissingspunten voor migratie van de cloudidentiteitsservice
uuid: ee56b5de-fcf3-4cfb-9e53-762af7c4d2ff
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Ervaar de beslissingspunten voor migratie van de cloudidentiteitsservice

Voordat u de Experience Cloud Identity Service gaat implementeren, moet u begrijpen hoe deze service het bijhouden van bezoekers op meerdere domeinen en mogelijke problemen beïnvloedt als u gegevens verzamelt met verschillende methoden of via JavaScript-bestanden.

Op basis van antwoorden op de vragen in deze sectie kunt u bepalen welke aanvullende migratiestappen u moet uitvoeren.

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
   <td colname="col2"> <p>Ga over naar <a href="../../reference/analytics-reference/migration-decisions.md#section-34dabde7780e4a339f134c0ca7768961" format="dita" scope="local"> Als u geen CNAME voor gegevensverzameling hebt, gaat het om de gegevensverzamelingsserver *.2o7.net of *.sc.omtr dc.net?</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Als u een CNAME van de gegevensinzameling hebt, hebt u veelvoudige domeinen?

Als u veelvoudige domeinen hebt die gegevens naar *zelfde rapportreeks* verzenden, dan adviseren wij gegevensinzameling met een CNAME. Zo kunt u bezoekers in verschillende domeinen volgen. Als u gegevens over één enkel domein verzamelt, is er geen voordeel aan het handhaven van een CNAME van de gegevensinzameling.

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
   <td colname="col2"> <p>Als u bezoekers over veelvoudige domeinen volgt, en u ook een belangrijkste ingangsplaats hebt waar de klanten kunnen worden geïdentificeerd alvorens zij andere domeinen bezoeken, dan zou u uw gegevensinzameling CNAME moeten blijven gebruiken. Zie <a href="../../reference/analytics-reference/cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d" format="dita" scope="local"> de NAMEN van de Inzameling van Gegevens en het Volgen</a> van Domeinen voor een gedetailleerde verklaring. </p> <p>Merk op dat u twee extra het volgen-serverparameters, <span class="codeph"> bezoeker.marketingCloudServer</span> en <span class="codeph"> bezoeker.marketingCloudServerSecure</span>moet specificeren, om een NAAM met de dienst van identiteitskaart te vormen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Eén domein </p> </td> 
   <td colname="col2"> <p>Als u met één domein werkt, kunt u migreren van een CNAME voor gegevensverzameling als u dit niet meer wilt beheren. Nochtans, is er geen vereiste om te veranderen als uw CNAME werkt. </p> <p>Als u CNAME verwijdert: </p> 
    <ul id="ul_12CDECEFC7BB41A18895B507CAA42315"> 
     <li id="li_32E2CD3E58454E20A642BADE507AE86E">Zorg ervoor dat uw nieuwe trackingserver voldoet aan de <a href="https://marketing.adobe.com/resources/help/en_US/whitepapers/rdc/" format="https" scope="external"> RDC-standaard</a>. </li> 
     <li id="li_865BB6DAA3594EBBAB688E73C8343762">Ga van CNAME aan een RDC volgende server een paar maanden voorafgaand aan uw migratie naar de dienst van identiteitskaart van de <span class="keyword"> Ervaring Cloud</span> . </li> 
     <li id="li_284A015177554C848C8648DC5BBAA365"> <i>Gebruik geen</i> trackingserver <span class="codeph"> *.2o7.net</span> . </li> 
     <li id="li_B1ABF03DC46C42059F61542CDE0FE5A1">Neem contact op met de <a href="https://helpx.adobe.com/marketing-cloud/contact-support.html" format="https" scope="external"> klantenservice</a> om een bezoekersmigratie in te stellen. Hierdoor is het aantal bezoekers consistent. </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Hebt u meerdere JavaScript-analysebestanden of volgt u Flash-toepassingen of -video&#39;s?

Als u meerdere Analytics JavaScript-bestanden of Flash-toepassingen of -video&#39;s op uw site hebt die gegevens naar *dezelfde rapportsuite* verzenden, moet u een respijtperiode zodanig configureren dat bezoekers door een Analytics-id worden geïdentificeerd terwijl u de [!DNL Experience Cloud] id-service uitvoert.

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
   <td colname="col2"> <p>Configureer een respijtperiode voor de bezoekersidentiteitsservice zodat u de service met de bezoekersidentiteitskaart kunt inzetten voor elk JavaScript-bestand en andere bibliotheken voor gegevensverzameling. Zie Respijtperiode <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"></a>voor service-ID. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Eén JavaScript-analysebestand </p> </td> 
   <td colname="col2"> <p>U kunt uw enige JavaScript-bestand zonder een respijtperiode bijwerken zodat u de service bezoekersidentiteitskaart kunt gebruiken. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Gebruikt u niet-ondersteunde methoden voor gegevensverzameling?

Mogelijk moet u de manier bijwerken waarop u koppelingen bijhoudt of een migratie van Sliverlight uitvoeren.

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
   <td colname="col2"> <p>Geen. De service <span class="keyword"> Experience Cloud</span> ID ondersteunt deze methoden voor gegevensverzameling. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Silverlight </p> </td> 
   <td colname="col2"> <p>U moet weg van Silverlight migreren als bezoekers tot inhoud Silverlight en andere secties van uw plaats kunnen toegang hebben die de dienst van identiteitskaart van de <span class="keyword"> Ervaring Cloud</span> gebruiken. Silverlight wordt niet ondersteund door de id-service. </p> <p> Als u een op Silverlight gebaseerde videospeler bijhoudt, biedt de leverancier waarschijnlijk JavaScript-API's die u in plaats daarvan kunt gebruiken. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Gecodeerde afbeeldingstags </p> </td> 
   <td colname="col2"> <p>Werk hard-gecodeerde verbindingen bij om JavaScript te gebruiken. </p> </td> 
  </tr> 
 </tbody> 
</table>

