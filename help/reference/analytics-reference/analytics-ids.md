---
description: De Experience Cloud Identity Service vervangt de oude ID-methoden van Analytics-bezoekers.
keywords: ID Service
seo-description: De Experience Cloud Identity Service vervangt de oude ID-methoden van Analytics-bezoekers.
seo-title: Analytics en Experience Cloud ID's instellen
title: Analytics en Experience Cloud ID's instellen
uuid: 421cf597-a3e0-4ca3-8ce8-d0c80cbb6aca
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: tm+mt
source-wordcount: '972'
ht-degree: 1%

---


# Analytics en Experience Cloud ID&#39;s instellen{#setting-analytics-and-experience-cloud-ids}

De Experience Cloud Identity Service vervangt de oude ID-methoden van Analytics-bezoekers.

Nadat de id-service is geïmplementeerd, wordt deze code uitgevoerd vóór AppMeasurement. De dienst van identiteitskaart wint Experience Cloud en Analytics IDs terug zodat zijn deze waarden klaar wanneer AppMeasurement laadt.

Wanneer AppMeasurement laadt, worden de waarden van Experience Cloud en Analytics IDs gevraagd van de dienst van identiteitskaart en verzonden naar gegevensinzameling met elke servervraag. Aangezien de id-service de bezoeker-id bepaalt en deze gewoon doorgeeft aan AppMeasurement, moet de id-service op elke pagina worden opgenomen en geïmplementeerd voordat het JavaScript-bestand voor AppMeasurement wordt gestart.

## Wijzigingen in het proces Analytics ID {#section-79bb86ae63f546419bb1a7ef5e710462}

De belangrijkste wijziging bij het migreren naar de [!DNL Experience Cloud] id-service is dat het ID-cookie wordt ingesteld met JavaScript in plaats van in de HTTP-header die wordt geretourneerd van de webserver voor gegevensverzameling. Om deze wijziging te begrijpen, wordt in de volgende secties beschreven hoe cookies met deze twee methoden worden ingesteld.

**HTTP-header**

Een HTTP-reactie van een webserver stelt cookies in een browser in. Zo wordt het `s_vi` cookie ingesteld. Het `s_vi` cookie identificeert bezoekers van Analytics. Nadat een cookie is ingesteld, wordt deze met alle volgende HTTP-aanvragen naar die server verzonden.

Wanneer een verzoek naar de server van de de gegevensinzameling van de Adobe wordt verzonden, wordt de kopbal gecontroleerd voor het `s_vi` koekje. Als deze cookie in de aanvraag staat, wordt deze gebruikt om de bezoeker te identificeren. Als het cookie zich niet in de aanvraag bevindt, genereert de server een unieke [!DNL Experience Cloud] id, stelt deze in als een cookie in de HTTP-antwoordheader en stuurt deze terug met de aanvraag. Het cookie wordt opgeslagen in de browser en wordt teruggestuurd naar de server voor gegevensverzameling tijdens volgende bezoeken aan de site. Hierdoor kan de bezoeker worden geïdentificeerd bij verschillende bezoeken.

Sommige browsers, zoals Apple Safari, accepteren cookies van andere bedrijven echter niet. Dit zijn cookies die in de browser zijn ingesteld vanuit andere domeinen dan de huidige website. Bovendien blokkeert Safari cookies op domeinen van derden als een bezoeker niet eerder naar dat domein is geweest. Bijvoorbeeld, als u bent `mysite.com` en uw server van de gegevensinzameling is `mysite.omtrdc.net`, zou het koekje dat in de kopbal van HTTP van is teruggekeerd door browser `mysite.omtrdc.net` kunnen worden verworpen.

Om dit te vermijden, hebben vele klanten CNAME verslagen voor hun servers van de gegevensinzameling uitgevoerd. Dit kan een effectief onderdeel zijn van een [implementatiestrategie](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-first-party.html) voor cookies van de eerste partij. Als een CNAME-record is geconfigureerd om een hostnaam in het domein van de klant toe te wijzen aan de server voor gegevensverzameling (bijv. toewijzing `metrics.mysite.com` aan `mysite.omtrdc.net`), wordt het [!DNL Experience Cloud] ID-cookie opgeslagen omdat het domein van de gegevensverzameling nu overeenkomt met het domein van de website. Hierdoor wordt de kans groter dat het cookie van de ID-service wordt opgeslagen. Nochtans, introduceert dit sommige overheadkosten omdat u CNAME- verslagen moet vormen en SSL certificaten voor de servers van de gegevensinzameling handhaven.

**JavaScript**

JavaScript kan cookies lezen en schrijven die zijn ingesteld in het domein van de eerste partij (het domein van de huidige website). De [!DNL Experience Cloud] id-service gebruikt deze methode om het `AMCV_###@AdobeOrg` cookie in te stellen dat alle bezoeker-id&#39;s bevat. Het domein van de traceringsserver hoeft dus niet langer overeen te komen met het domein van de website om het cookie van de bezoeker-id te kunnen opslaan. In de meeste gevallen is dit de aangewezen manier om het de dienstkoekje van identiteitskaart te plaatsen omdat het de overheadkosten van CNAME- verslagen en SSL- certificaten elimineert.

Er zijn echter een paar situaties waarin het instellen van het cookie in de HTTP-header gunstig is voor het bijhouden van meerdere domeinen. Dit wordt beschreven in CNAME&#39;s voor [gegevensverzameling en het bijhouden](../../reference/analytics-reference/cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d)van andere domeinen.

## Aangepaste analyse-id&#39;s {#section-b6a7bd19e9ff432390010062450808f6}

Het instellen van een klant-id met behulp van `s.visitorID` is een manier om gebruikers in Analytics te identificeren. Integraties waarin analysegegevens worden geëxporteerd of geïmporteerd met de id-service werken echter niet wanneer een bezoeker wordt geïdentificeerd met `s.visitorID`.

Dit omvat, maar is niet beperkt tot, gedeeld publiek, Analytics voor Doel (A4T), en de Attributen van de Klant. Voor deze integraties wordt het instellen van een aangepaste Analytics-id niet ondersteund.

## Bestelling van Bezoeker-id voor analyse {#section-de1dc9fc9b6d4388995b70e35b8bcddf}

Nadat u de bezoeker-id-service hebt geïmplementeerd, zijn er vijf manieren waarop een bezoeker kan worden geïdentificeerd in Analytics (vermeld in de volgende tabel in volgorde van voorkeur):

<table id="table_D267D36451F643D1BB68AF6FEAA6AD1A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Volgorde gebruikt </th> 
   <th colname="col2" class="entry"> Query-parameter (verzamelingsmethode) </th> 
   <th colname="col3" class="entry"> presenteren als </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <img id="image_9F3E58898A1B4F40BBDEF5ADE362E55C" src="assets/step1_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://docs.adobe.com/content/help/en/analytics/implementation/vars/config-vars/visitorid.html" format="http" scope="external"> vid (s.bezoekerID)</a> </p> </td> 
   <td colname="col3"> <p>s.bezoekerID is ingesteld </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_77A06981672745B6AEA8BB4D55911CCA" src="assets/step2_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-analytics.html" format="http" scope="external"> aid (s_vi cookie)</a> </p> </td> 
   <td colname="col3"> <p>De bezoeker had een bestaand s_vi koekje alvorens u de dienst van identiteitskaart van de <span class="keyword"> Experience Cloud</span> opstelde, of u hebt een <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> gevormde graadperiode</a> . </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_0A950B1A6B004387AFEE8EED882739CB" src="assets/step3_icon.png" /> </p> </td> 
   <td colname="col2"> <p>mid (AMCV_ cookie ingesteld door Experience Cloud bezoeker ID service) </p> </td> 
   <td colname="col3"> <p>Browser van de bezoeker keurt eerste-partijkoekjes goed </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_6F0ED8FE3EF846CA8E6ECCC3C0070D85" src="assets/step4_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://docs.adobe.com/content/help/en/id-service/using/reference/analytics-reference/analytics-ids.html" format="http" scope="external"> fid (fallback-cookie op H.25.3 of hoger, of AppMeasurement voor JavaScript)</a> </p> </td> 
   <td colname="col3"> <p>Een browser accepteert geen cookies van derden en de Analytics tracking-server is ingesteld als een externe tracingserver. </p> <p> <p>Opmerking: Het bestand <span class="codeph"> Fid</span> is een oudere id en wordt niet gebruikt als u de id-service op uw site hebt geïmplementeerd. In dit geval is het <span class="codeph"> bestand</span> niet nodig omdat het door de eerste partij, <a href="../../introduction/cookies.md" format="dita" scope="local"> AMCV-cookie</a> , verouderd is. Het is om historische redenen en ter ondersteuning van de oude code gehandhaafd. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_23D8C0EB69EC4084BC237B5B98C036F4" src="assets/step5_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://docs.adobe.com/content/help/en/analytics/technotes/visitor-identification.html" format="http" scope="external"> IP Adres, de Agent van de Gebruiker, IP van de Gateway Adres</a> </p> </td> 
   <td colname="col3"> <p>De browser van de bezoeker accepteert geen cookies. </p> </td> 
  </tr> 
 </tbody> 
</table>

In veel scenario&#39;s zou u 2 of 3 verschillende IDs op een vraag kunnen zien, maar de Analytics zal eerste identiteitskaart gebruiken huidig van die lijst als officiële [!DNL Experience Cloud] identiteitskaart. Als u bijvoorbeeld een aangepaste bezoeker-id instelt (opgenomen in de query-parameter &quot;vid&quot;), wordt die id gebruikt vóór andere id&#39;s die op dezelfde hit aanwezig kunnen zijn.

>[!MORELIKETHIS]
>
>* [Bewerkingsvolgorde voor analytische id&#39;s](../../reference/analytics-reference/analytics-order-of-operations.md#concept-b92935b4fff545adb4773f3728bc15ef)

