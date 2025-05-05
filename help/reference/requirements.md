---
description: Herzie deze sectie om ervoor te zorgen u de juiste oplossingen, de diensten, en de codeversies gebruikt die door de Dienst van de Identiteit van het Experience Cloud worden vereist.
keywords: ID-service
title: Vereisten voor de identiteitsdienst van het Experience Cloud
exl-id: ebeac4c7-b36c-4a4e-9378-351fac5baf53
source-git-commit: 00ebcaa16ec6b432b480d96fbf79b6a745515b1b
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 1%

---

# Vereisten voor de identiteitsdienst van het Experience Cloud {#requirements-for-the-experience-cloud-id-service}

Herzie deze sectie om ervoor te zorgen u de juiste oplossingen, de diensten, en de codeversies gebruikt die door de Dienst van de Identiteit van het Experience Cloud worden vereist.

## Vereisten zorgen voor een succesvolle implementatie en ondersteuning {#section-15e54a9e9ad2443cb9dc950b4a78f1f1}

Een geslaagde, ondersteunde implementatie voldoet aan (of overschrijdt) de codevereisten en volgt de instructies die worden weergegeven in de [!DNL Adobe] Help. Een niet-ondersteunde implementatie levert onverwachte resultaten op en voorkomt dat de klantenservice en onze technische teams u helpen bij het oplossen van problemen met de id-service.

### Standaardimplementaties

Zie {de markeringen van 0} Experience Platform [&#128279;](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl) voor uw standaardimplementatie.

### Niet-standaardimplementaties

Voor niet-standaard, of handmatige implementaties, moet u de dienst van identiteitskaart opstelling zoals die door de procedures wordt beschreven deze gids. Net als bij de bovenstaande DTM-richtlijnen leidt onjuiste plaatsing en laden van code tot een niet-ondersteunde implementatie.

## Vereisten voor Experience Cloud: organisatie-id {#section-a02f537129a64ffbb690d5738d360c26}

Als u de id-service wilt gebruiken, moet uw bedrijf zijn ingeschakeld voor de [!DNL Experience Cloud] en beschikken over een organisatie-id. Controleer de volgende lijst als u niet zeker bent van de [!DNL Experience Cloud] status van uw bedrijf en uw organisatie-id moet vinden.

>[!IMPORTANT]
>
>De organisatie-id is hoofdlettergevoelig en moet precies worden gebruikt zoals opgegeven.

<table id="table_6C74B676EB094C568D2439FDCC9A7830"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Status van Experience Cloud </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b> Toegelaten </b> </p> </td> 
   <td colname="col2"> <p>Als uw bedrijf voor het <span class="keyword"> Experience Cloud </span> wordt toegelaten maar u hebt uw identiteitskaart van de Organisatie niet, zie <a href="https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html" format="https" scope="external"> Organisatorische IDs </a> (rol neer aan de sectie <i> vindt uw identiteitskaart van de Organisatie </i>). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> niet zeker </b> </p> </td> 
   <td colname="col2"> <p> Als u niet de status <span class="keyword"> Experience Cloud </span> van uw bedrijf kent, vraag wie uw rekening van de Adobe beheert als de leden van uw bedrijf zich bij <a href="https://experiencecloud.adobe.com" format="https" scope="external"> marketing.adobe.com </a> kunnen aanmelden gebruikend Adobe ID. Als u dat kunt, wordt u toegelaten en kan een beheerder uw Organisatie-id bekijken. Om organisatie identiteitskaart te vinden, zie de sectie van het "Beleid van de Pagina"in <a href="https://experienceleague.adobe.com/docs/core-services/interface/experience-cloud.html?lang=en" format="https" scope="external"> Beleid van het Experience Cloud </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> niet toegelaten </b> </p> </td> 
   <td colname="col2"> <p> Als uw bedrijf niet voor Experience Cloud wordt toegelaten, zie <a href="https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html" format="https" scope="external"> de Diensten van de Kern - toelatend Uw Oplossingen </a> om begonnen te worden. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Analysevereisten: regionale gegevensverzameling (RDC) {#section-7d04bb013bc84a25bae3b148bc0ca25f}

Alle trackingservers zijn omgezet in RDC, zodat de Analytics tracking-server niet hoeft te worden gewijzigd. [ Meer info... ](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html?lang=en)

## Codebibliotheken en versievereisten {#section-ad7542a4317d430fa79fc6b095beb84d}

In de volgende secties vindt u een overzicht van de minimale codesversies die vereist zijn voor het gebruik van de [!DNL Experience Cloud] ID-service.

>[!TIP]
>
>Wij adviseren dat u de recentste codeversies eerder dan de vereiste minimumversies gebruikt.

**JavaScript**

<table id="table_8E773F76DBCB4797A0C117080CA8707C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Experience Cloud </th> 
   <th colname="col3" class="entry"> Codebibliotheek </th> 
   <th colname="col4" class="entry"> Vereisten voor versie </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b> <span class="keyword"> Experience Cloud </span> ID-service </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> VisitorAPI.js </span> </p> </td> 
   <td colname="col4"> <p>2,0 of hoger </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="2"> <p> <b> <span class="keyword"> Analytics </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> AppMeasurement.js </span> </p> <p>Zie <a href="https://experienceleague.adobe.com/docs/analytics/implementation/js/overview.html" format="https" scope="external"> AppMeasurement voor JavaScript </a> . </p> </td> 
   <td colname="col4"> <p>1.6.4 of hoger. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> s_code.js </span> </p> </td> 
   <td colname="col4"> <p>H.27 </p> <p> <p>Opmerking: <span class="keyword"> Analytics </span> s_code version H.27 wordt niet meer ondersteund met de release van de ID-service versie 1.6.0. Voer een upgrade van uw code uit naar de nieuwste versie van het AppMeasurement. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p>Videohartslag </p> <p>Zie <a href="https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html" format="https" scope="external"> Videohartslag 2.x voor JavaScript </a> . </p> </td> 
   <td colname="col4"> <p>2,0 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> <span class="keyword"> Audience Manager </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> dil.js </span> </p> <p> Zie <a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-overview.html" format="https" scope="external"> Data Integration Library </a> (DIL). </p> </td> 
   <td colname="col4"> <p>5,0 </p></td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="1"> <p> <b> <span class="keyword"> Doel </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> mbox.js </span> </p> <p>Zie <a href="https://experienceleague.adobe.com/docs/target-dev/developer/client-side/at-js-implementation/overview.html?lang=en" format="https" scope="external"> mbox Code </a> . </p> </td> 
   <td colname="col4"> <p>61 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> at.js </span> </p> <p>Zie <a href="https://experienceleague.adobe.com/docs/target-dev/developer/client-side/at-js-implementation/at-js/how-atjs-works.html?lang=en" format="https" scope="external"> at.js Implementation </a>. </p> </td> 
   <td colname="col4"> <p>0,9,1 </p> </td> 
  </tr> 
 </tbody> 
</table>

## SDK-vereisten voor Android en iOS {#section-73b2446fba8e463888642c7d7dfd94f1}

De id-service vereist minimaal de hieronder vermelde SDK-versies.

* Android: 4.11.0
* iOS: 4.11.0

>[!TIP]
>
>Wij adviseren dat u de recentste codeversies eerder dan de vereiste minimumversies gebruikt.

De SDK-code moet zijn ingeschakeld voor de ID-service. Laat en download de recentste code van SDK voor elke app van uw [ Adobe Mobiele rekening van de Diensten ](https://mobilemarketing.adobe.com/) toe. Zie ook:

* [ vorm de Opties van de Dienst van identiteitskaart van de Bezoeker SDK ](https://experienceleague.adobe.com/docs/mobile-services/using/manage-app-settings-ug/configuring-app/t-config-visitor.html)
* [ de methodes van SDK van Android ](https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/c-marketing-cloud.html)
* [ de methodes van SKD van iOS ](https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/marketing-cloud.html)

>[!MORELIKETHIS]
>
>* [ de Bibliotheek van de Code ](../library/library.md#concept-ff27497375644a898d47984aefb21c97)
