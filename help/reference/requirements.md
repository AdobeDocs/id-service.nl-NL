---
description: Herzie deze sectie om ervoor te zorgen u de juiste oplossingen, de diensten, en de codeversies gebruikt die door de Dienst van de Identiteit van de Experience Cloud worden vereist.
keywords: ID-service
title: Vereisten voor de Experience Cloud Identity Service
exl-id: ebeac4c7-b36c-4a4e-9378-351fac5baf53
source-git-commit: 159b37e360b586bbada13e34793009e3067de668
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 3%

---

# Vereisten voor de Experience Cloud Identity Service {#requirements-for-the-experience-cloud-id-service}

Herzie deze sectie om ervoor te zorgen u de juiste oplossingen, de diensten, en de codeversies gebruikt die door de Dienst van de Identiteit van de Experience Cloud worden vereist.

## Vereisten zorgen voor een succesvolle implementatie en ondersteuning {#section-15e54a9e9ad2443cb9dc950b4a78f1f1}

Een geslaagde, ondersteunde implementatie voldoet aan (of overschrijdt) de codevereisten en volgt de instructies die worden weergegeven in het dialoogvenster [!DNL Adobe] help. Een niet-ondersteunde implementatie levert onverwachte resultaten op en voorkomt dat de klantenservice en onze technische teams u helpen bij het oplossen van problemen met de id-service.

### Standaardimplementaties

Zie [Experience Platform-tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl) voor uw standaardimplementatie.

### Niet-standaardimplementaties

Voor niet-standaard, of handmatige implementaties, moet u de dienst van identiteitskaart opstelling zoals die door de procedures wordt beschreven deze gids. Net als bij de bovenstaande DTM-richtlijnen leidt onjuiste plaatsing en laden van code tot een niet-ondersteunde implementatie.

## Experience Cloud-eisen: Organisatie-id {#section-a02f537129a64ffbb690d5738d360c26}

Om de dienst van identiteitskaart te gebruiken, moet uw bedrijf voor worden toegelaten [!DNL Experience Cloud] en een organisatie-id hebben. Controleer de volgende lijst als u van uw bedrijf onzeker bent [!DNL Experience Cloud] status en moet uw organisatie-id vinden.

>[!IMPORTANT]
>
>De organisatie-id is hoofdlettergevoelig en moet precies worden gebruikt zoals opgegeven.

<table id="table_6C74B676EB094C568D2439FDCC9A7830"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Experience Cloud-status </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Ingeschakeld</b> </p> </td> 
   <td colname="col2"> <p>Als uw bedrijf voor <span class="keyword"> Experience Cloud</span> maar u hebt uw organisatie-id niet. Zie <a href="https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html" format="https" scope="external"> Organisatorische id's</a> (omlaag schuiven naar de sectie <i>Zoek uw organisatie-id</i>). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Niet zeker</b> </p> </td> 
   <td colname="col2"> <p> Als u de <span class="keyword"> Experience Cloud</span> status, vraag wie uw Adobe-account beheert of leden van uw bedrijf zich kunnen aanmelden bij <a href="https://experiencecloud.adobe.com" format="https" scope="external"> marketing.adobe.com</a> een Adobe ID gebruiken. Als u dat kunt, wordt u toegelaten en kan een beheerder uw Organisatie-id bekijken. Zie de sectie "Beheerpagina" in <a href="https://experienceleague.adobe.com/docs/core-services/interface/experience-cloud.html?lang=en" format="https" scope="external"> Experience Cloud-toediening</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Niet ingeschakeld</b> </p> </td> 
   <td colname="col2"> <p> Als uw bedrijf niet voor Experience Cloud wordt toegelaten, zie <a href="https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html" format="https" scope="external"> Core Services - Uw oplossingen inschakelen</a> om aan de slag te gaan. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Analysevereisten: Regionale gegevensverzameling (RDC) {#section-7d04bb013bc84a25bae3b148bc0ca25f}

Alle trackingservers zijn omgezet in RDC, zodat de Analytics tracking-server niet hoeft te worden gewijzigd. [Meer informatie...](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html?lang=en)

## Codebibliotheken en versievereisten {#section-ad7542a4317d430fa79fc6b095beb84d}

De volgende secties geven een overzicht van de minimale codesversies die vereist zijn om de [!DNL Experience Cloud] ID-service.

>[!TIP]
>
>Wij adviseren dat u de recentste codeversies eerder dan de vereiste minimumversies gebruikt.

**JavaScript**

<table id="table_8E773F76DBCB4797A0C117080CA8707C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Experience Cloud-oplossing </th> 
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
   <td colname="col1" morerows="2"> <p> <b> <span class="keyword"> Analytics </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> AppMeturement.js</span> </p> <p>Zie <a href="https://experienceleague.adobe.com/docs/analytics/implementation/js/overview.html" format="https" scope="external"> AppMeasurement voor JavaScript </a>. </p> </td> 
   <td colname="col4"> <p>1.6.4 of hoger. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> s_code.js</span> </p> </td> 
   <td colname="col4"> <p>H.27 </p> <p> <p>Opmerking:  <span class="keyword"> Analyse</span> s_code versie H.27 wordt niet meer ondersteund met de release van de ID-service versie 1.6.0. Voer een upgrade van uw code uit naar de nieuwste versie van AppMeasurement. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p>Videohartslag </p> <p>Zie <a href="https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html" format="https" scope="external"> Videohartslag 2.x voor JavaScript</a>. </p> </td> 
   <td colname="col4"> <p>2.0 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> <span class="keyword"> Audience Manager </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> dil.js</span> </p> <p> Zie <a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-overview.html" format="https" scope="external"> Data Integration Library</a> (DIL). </p> </td> 
   <td colname="col4"> <p>5.0 </p></td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="1"> <p> <b> <span class="keyword"> Target </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> mbox.js</span> </p> <p>Zie <a href="https://experienceleague.adobe.com/docs/target/using/implement-target/client-side/mbox-implement/mbox-technical.html" format="https" scope="external"> mbox-code</a>. </p> </td> 
   <td colname="col4"> <p>61 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> at.js</span> </p> <p>Zie <a href="https://experienceleague.adobe.com/docs/target/using/implement-target/client-side/at-js/how-atjs-works.html" format="https" scope="external"> om.js Implementatie</a>. </p> </td> 
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

De SDK-code moet zijn ingeschakeld voor de ID-service. De nieuwste SDK-code voor elke toepassing inschakelen en downloaden vanuit uw [Adobe mobiele services](https://mobilemarketing.adobe.com/) account. Zie ook:

* [Serviceopties voor SDK-bezoeker-id configureren](https://experienceleague.adobe.com/docs/mobile-services/using/manage-app-settings-ug/configuring-app/t-config-visitor.html)
* [Methoden van Android SDK](https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/c-marketing-cloud.html)
* [iOS SKD-methoden](https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/marketing-cloud.html)

>[!MORELIKETHIS]
>
>* [Codebibliotheek](../library/library.md#concept-ff27497375644a898d47984aefb21c97)

