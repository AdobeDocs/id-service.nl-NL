---
description: Controleer deze sectie om te controleren of u de juiste oplossingen, services en codeversies gebruikt die zijn vereist door de Experience Cloud Identity Service.
keywords: ID Service
seo-description: Controleer deze sectie om te controleren of u de juiste oplossingen, services en codeversies gebruikt die zijn vereist door de Experience Cloud Identity Service.
seo-title: Vereisten voor de Experience Cloud Identity Service
title: Vereisten voor de Experience Cloud Identity Service
uuid: 608b1082-6e9e-4101-b6cb-60027950109b
translation-type: tm+mt
source-git-commit: c4c0b791230422f17292b72fd45ba5689a60adae

---


# Requirements for the Experience Cloud Identity Service {#requirements-for-the-experience-cloud-id-service}

Controleer deze sectie om te controleren of u de juiste oplossingen, services en codeversies gebruikt die zijn vereist door de Experience Cloud Identity Service.

## Vereisten zorgen voor een succesvolle implementatie en ondersteuning {#section-15e54a9e9ad2443cb9dc950b4a78f1f1}

Een geslaagde, ondersteunde implementatie voldoet aan (of overschrijdt) de codevereisten en volgt de instructies zoals deze in de [!DNL Adobe] Help worden weergegeven. Een niet-ondersteunde implementatie levert onverwachte resultaten op en voorkomt dat de klantenservice en onze technische teams u helpen bij het oplossen van problemen met de id-service.

<table id="table_2216C44AA66248DCAA13BF64BDF2D88A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Type implementatie </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445" format="dita" scope="local"> Standaard</a> </p> </td> 
   <td colname="col2"> <p>Voor een standaardimplementatie met Dynamic Tag Management (DTM) moet u: </p> 
    <ul id="ul_59CDE179566844B494F3068FF6333809"> 
     <li id="li_CCCB6AFC08EE405F94C42216D3CE50AC"> Plaats de code van de ingesloten kop in de sectie <span class="codeph"> &lt;head&gt;</span> van de pagina. </li> 
     <li id="li_13962F2CB1764091A84863BE499675A2">Plaats de insluitcode voor de voettekst vóór de afsluitende <span class="codeph"> &lt;/body&gt;</span> -tag. </li> 
    </ul> <p>Een standaardimplementatie wordt niet ondersteund wanneer u: </p> 
    <ul id="ul_3B62559317ED4C7AA548C3B8DBA281F7"> 
     <li id="li_1F16C6D412944197BEA56BC24730782C"> Plaats een van deze DTM-insluitcodes elders in de markering en/of de paginacode. </li> 
     <li id="li_05615C01F3A947BBBD41046E68377224"> Voeg, voeg, of ladingsDTM code met asynchrone methodes, vraag/callback methodes, of omslag toe. </li> 
     <li id="li_B2137DFF627B473FA876580449026D2B">Meerdere versies van insluitcode op dezelfde pagina opnemen. </li> 
    </ul> <p>Zie ook <a href="https://marketing.adobe.com/resources/help/en_US/dtm/?f=deployment.html" format="https" scope="external"> Code insluiten en Hosting Options</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <a href="../implementation-guides/implementation-guides.md#section-2c4f2db1f9704315a7cccab6d2e07113" format="dita" scope="local"> Niet-standaardimplementaties </a> </p> </td> 
   <td colname="col2"> <p>Voor niet-standaard, of handmatige implementaties, moet u de dienst van identiteitskaart opstelling zoals die door de procedures wordt beschreven deze gids. Net als bij de bovenstaande DTM-richtlijnen leidt onjuiste plaatsing en laden van code tot een niet-ondersteunde implementatie. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Vereisten voor de cloud: Organisatie-id {#section-a02f537129a64ffbb690d5738d360c26}

Om de dienst van identiteitskaart te gebruiken, moet uw bedrijf voor [!DNL Experience Cloud] en een identiteitskaart van de Organisatie worden toegelaten. Controleer de volgende lijst als u niet zeker bent van de [!DNL Experience Cloud] status van uw bedrijf en uw organisatie-id moet vinden.

>[!IMPORTANT]
>
>De organisatie-id is hoofdlettergevoelig en moet precies worden gebruikt zoals opgegeven.

<table id="table_6C74B676EB094C568D2439FDCC9A7830"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Cloudstatus ervaren </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Ingeschakeld</b> </p> </td> 
   <td colname="col2"> <p>Als uw bedrijf is ingeschakeld voor de <span class="keyword"> Experience Cloud</span> maar u beschikt niet over uw organisatie-id, raadpleegt u <a href="https://marketing.adobe.com/resources/help/en_US/mcloud/organizations.html" format="https" scope="external"> Organisatorische id's</a> (schuif omlaag naar de sectie <i>Zoek uw organisatie-id</i>). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Niet zeker</b> </p> </td> 
   <td colname="col2"> <p> Als u de <span class="keyword"> Experience Cloud</span> van uw bedrijf niet kent, vraag dan aan wie uw Adobe-account wordt beheerd of leden van uw bedrijf zich met een Adobe-id kunnen aanmelden op <a href="https://marketing.adobe.com" format="https" scope="external"> marketing.adobe.com</a> . Als u dat kunt, wordt u toegelaten en kan een beheerder uw Organisatie-id bekijken. Zie de sectie "Beheerpagina" in <a href="https://marketing.adobe.com/resources/help/en_US/mcloud/?f=admin_getting_started" format="https" scope="external"> Experience Cloud Administration</a>voor informatie over de organisatie-id. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Niet ingeschakeld</b> </p> </td> 
   <td colname="col2"> <p> Als uw bedrijf niet geschikt is voor Experience Cloud, raadpleegt u <a href="https://marketing.adobe.com/resources/help/en_US/mcloud/?f=core_services.html" format="https" scope="external"> Core Services - Uw oplossingen</a> inschakelen om aan de slag te gaan. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Analysevereisten: Regionale gegevensverzameling (RDC) {#section-7d04bb013bc84a25bae3b148bc0ca25f}

Alle trackingservers zijn omgezet in RDC, zodat de Analytics tracking-server niet hoeft te worden gewijzigd. [Meer informatie...](https://docs.adobe.com/content/help/en/analytics/admin/data-collection/regional-data-collection/regional-data-collection.html)

## Codebibliotheken en versievereisten {#section-ad7542a4317d430fa79fc6b095beb84d}

De volgende secties maken een lijst van de minimumcodeversies die worden vereist om de dienst van [!DNL Experience Cloud] identiteitskaart te gebruiken.

>[!TIP]
>
>Wij adviseren dat u de recentste codeversies eerder dan de vereiste minimumversies gebruikt.

**JavaScript**

<table id="table_8E773F76DBCB4797A0C117080CA8707C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Experience Cloud Solution </th> 
   <th colname="col3" class="entry"> Codebibliotheek </th> 
   <th colname="col4" class="entry"> Vereisten voor versie </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b> <span class="keyword"> Experience Cloud</span> ID-service</b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> VisitorAPI.js</span> </p> </td> 
   <td colname="col4"> <p>2,0 of hoger </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="2"> <p> <b> <span class="keyword"> Analyse </span></b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> AppMeturement.js</span> </p> <p>Zie <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=appmeasure_mjs.html" format="https" scope="external"> AppMeasurement voor JavaScript </a>. </p> </td> 
   <td colname="col4"> <p>1.6.4 of hoger. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> s_code.js</span> </p> </td> 
   <td colname="col4"> <p>H.27 </p> <p> <p>Opmerking:  <span class="keyword"> Analytics</span> s_code versie H.27 wordt niet meer gesteund met de versie van de dienstversie van identiteitskaart 1.6.0. Voer een upgrade van uw code uit naar de nieuwste versie van AppMeasurement. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p>Videohartslag </p> <p>Zie <a href="https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/hbvideo/index.html" format="https" scope="external"> Videohartslag 2.x voor JavaScript</a>. </p> </td> 
   <td colname="col4"> <p>2.0 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> <span class="keyword"> Auditiebeheer </span></b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> dil.js</span> </p> <p> Zie <a href="https://marketing.adobe.com/resources/help/en_US/aam/?f=c_dil.html" format="https" scope="external"> Data Integration Library</a> (DIL). </p> </td> 
   <td colname="col4"> <p>5.0 </p> <p> 
     <draft-comment>
       bijgewerkt vanaf 4.9 
     </draft-comment> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="1"> <p> <b> <span class="keyword"> Doel </span></b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> mbox.js</span> </p> <p>Zie <a href="https://marketing.adobe.com/resources/help/en_US/target/ov/?f=c_mbox_technical.html" format="https" scope="external"> postcode</a>. </p> </td> 
   <td colname="col4"> <p>61 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> at.js</span> </p> <p>Zie <a href="https://marketing.adobe.com/resources/help/en_US/target/ov2/c_target-atjs-implementation.html" format="https" scope="external"> at.js Implementation</a>. </p> </td> 
   <td colname="col4"> <p>0.9.1 </p> </td> 
  </tr> 
 </tbody> 
</table>

## SDK-vereisten voor Android en iOS {#section-73b2446fba8e463888642c7d7dfd94f1}

De id-service vereist minimaal de hieronder vermelde SDK-versies.

* Android: 4.11.0.
* iOS: 4.11.0.

>[!TIP]
>
>Wij adviseren dat u de recentste codeversies eerder dan de vereiste minimumversies gebruikt.

De SDK-code moet zijn ingeschakeld voor de ID-service. Schakel de nieuwste SDK-code voor elke toepassing in en download deze vanaf uw [Adobe Mobile Services](https://mobilemarketing.adobe.com/) -account. Zie ook:

* [Serviceopties voor SDK-bezoeker-id configureren](https://marketing.adobe.com/resources/help/en_US/mobile/t_config_visitor.html)
* [Methoden van Android SDK](https://marketing.adobe.com/resources/help/en_US/mobile/android/c_marketing_cloud.html)
* [iOS-SKD-methoden](https://marketing.adobe.com/resources/help/en_US/mobile/ios/marketing_cloud.html)

>[!MORELIKETHIS]
>
>* [Codebibliotheek](../library/library.md#concept-ff27497375644a898d47984aefb21c97)

