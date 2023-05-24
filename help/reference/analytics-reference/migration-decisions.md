---
description: Voordat u de Experience Cloud Identity Service gaat implementeren, moet u begrijpen hoe deze service het bijhouden van bezoekers op meerdere domeinen en mogelijke problemen beïnvloedt als u gegevens met verschillende methoden of via JavaScript-bestanden verzamelt.
keywords: ID-service
title: Experience Cloud-beslissingspunten voor identiteitsservicemigratie
exl-id: f2802db2-c95f-476f-8c60-f45e8312253c
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 1%

---

# Experience Cloud-beslissingspunten voor identiteitsservicemigratie

Voordat u de Experience Cloud Identity Service gaat implementeren, moet u begrijpen hoe deze service het bijhouden van bezoekers op meerdere domeinen en mogelijke problemen beïnvloedt als u gegevens met verschillende methoden of via JavaScript-bestanden verzamelt.

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
   <td colname="col2"> <p>Overslaan naar <a href="../../reference/analytics-reference/migration-decisions.md#section-34dabde7780e4a339f134c0ca7768961" format="dita" scope="local"> Als u geen CNAME van de gegevensinzameling hebt, is uw server van de gegevensinzameling *.2o7.net of *.sc.omtr dc.net?</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Als u een CNAME van de gegevensinzameling hebt, hebt u veelvoudige domeinen?

Als u meerdere domeinen hebt die gegevens naar de *zelfde rapportsuite*, dan adviseren wij gegevensinzameling met een CNAME. Zo kunt u bezoekers in verschillende domeinen volgen. Als u gegevens over één enkel domein verzamelt, is er geen voordeel aan het handhaven van een CNAME van de gegevensinzameling.

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
   <td colname="col2"> <p>Als u bezoekers over veelvoudige domeinen volgt, en u ook een belangrijkste ingangsplaats hebt waar de klanten kunnen worden geïdentificeerd alvorens zij andere domeinen bezoeken, dan zou u uw gegevensinzameling CNAME moeten blijven gebruiken. <!--See <a href="../../reference/analytics-reference/cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d" format="dita" scope="local"> Data Collection CNAMES and Cross Domain Tracking</a> for a detailed explanation.--> </p> <p>Merk op dat u twee extra het volgen-server parameters moet specificeren, <span class="codeph"> bezoeker.marketingCloudServer</span> en <span class="codeph"> bezoeker.marketingCloudServerSecure</span>, om een NAAM met de dienst van identiteitskaart te vormen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Eén domein </p> </td> 
   <td colname="col2"> <p>Als u met één domein werkt, kunt u migreren van een CNAME voor gegevensverzameling als u dit niet meer wilt beheren. Nochtans, is er geen vereiste om te veranderen als uw CNAME werkt. </p> <p>Als u CNAME verwijdert: </p> 
    <ul id="ul_12CDECEFC7BB41A18895B507CAA42315"> 
     <li id="li_32E2CD3E58454E20A642BADE507AE86E">Controleer of uw nieuwe trackingserver <a href="https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html" format="https" scope="external"> RDC-conform</a>. </li> 
     <li id="li_865BB6DAA3594EBBAB688E73C8343762">Een paar maanden voor de migratie van de CNAME naar een RDC-trackingserver gaan <span class="keyword"> Experience Cloud</span> ID-service. </li> 
     <li id="li_284A015177554C848C8648DC5BBAA365"> <i>Niet gebruiken</i> een <span class="codeph"> *.2o7.net</span> trackingserver. </li> 
     <li id="li_B1ABF03DC46C42059F61542CDE0FE5A1">Contact <a href="https://helpx.adobe.com/marketing-cloud/contact-support.html" format="https" scope="external"> Klantenservice</a> om een bezoekersmigratie in te stellen. Hierdoor is het aantal bezoekers consistent. </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Hebt u meerdere Analytics JavaScript-bestanden of volgt u Flash-toepassingen of video&#39;s?

Als u meerdere Analytics JavaScript-bestanden of Flash-toepassingen of video&#39;s op uw site hebt die gegevens naar de *zelfde rapportsuite* dient u een respijtperiode te configureren zodat bezoekers door een Analytics-id kunnen worden geïdentificeerd terwijl u de [!DNL Experience Cloud] ID-service.

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
   <td colname="col2"> <p>Configureer een respijtperiode voor de bezoekersidentiteitsservice zodat u de service met de bezoekersidentiteitskaart kunt inzetten voor elk JavaScript-bestand en andere bibliotheken voor gegevensverzameling. Zie <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> Respijtperiode ID-service</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Eén JavaScript-analysebestand </p> </td> 
   <td colname="col2"> <p>U kunt uw enige JavaScript-bestand zonder een respijtperiode bijwerken en zo de service bezoekersidentiteitskaart gebruiken. </p> </td> 
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
   <td colname="col2"> <p>Geen. De <span class="keyword"> Experience Cloud</span> De dienst van identiteitskaart steunt deze methodes van de gegevensinzameling. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Silverlight </p> </td> 
   <td colname="col2"> <p>U dient te migreren van Silverlight als bezoekers toegang hebben tot Silverlight-inhoud en andere gedeelten van uw site die gebruikmaken van de <span class="keyword"> Experience Cloud</span> ID-service. Silverlight wordt niet ondersteund door de id-service. </p> <p> Als u een op Silverlight gebaseerde videospeler bijhoudt, biedt de leverancier waarschijnlijk JavaScript-API's die u in plaats daarvan kunt gebruiken. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Gecodeerde afbeeldingstags </p> </td> 
   <td colname="col2"> <p>Werk hard-gecodeerde verbindingen bij om JavaScript te gebruiken. </p> </td> 
  </tr> 
 </tbody> 
</table>
