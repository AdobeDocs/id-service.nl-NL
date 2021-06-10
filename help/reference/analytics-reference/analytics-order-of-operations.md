---
description: Nadat u de bezoekersidentiteitsservice hebt geïmplementeerd, zijn er vijf manieren waarop een bezoeker kan worden geïdentificeerd in Analytics.
keywords: ID-service
title: Bewerkingsvolgorde voor analytische id's
exl-id: 8ee340fe-ef3b-40e6-9441-7ee0c9e20357
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# Volgorde van bewerkingen voor analytische id&#39;s{#order-of-operations-for-analytics-ids}

Nadat u de bezoekersidentiteitsservice hebt geïmplementeerd, zijn er vijf manieren waarop een bezoeker kan worden geïdentificeerd in Analytics.

In veel scenario&#39;s zou u 2 of 3 verschillende IDs op een vraag kunnen zien, maar de Analytics zal eerste identiteitskaart gebruiken aanwezig van die lijst als officiële [!DNL Experience Cloud] identiteitskaart. Als u bijvoorbeeld een aangepaste bezoeker-id instelt (opgenomen in de query-parameter `vid`), wordt die id gebruikt vóór andere id&#39;s die op dezelfde hit aanwezig kunnen zijn. Zie [Analytics en Experience Cloud IDs](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6) plaatsen voor meer informatie.

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
   <td colname="col1"> <p> <b>1<sup>e</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/visitorid.html" format="http" scope="external"> vid (s.bezoekerID)</a> </p> </td> 
   <td colname="col3"> <p>De <span class="codeph"> s.bezoekerID</span> wordt geplaatst. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>2 <sup>de</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html" format="http" scope="external"> aid (s_vi cookie)</a> </p> </td> 
   <td colname="col3"> <p>De bezoeker had een bestaand s_vi koekje alvorens u de <span class="keyword"> Experience Cloud </span> de dienst van identiteitskaart opstelde, of u hebt een <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> gevormde reserveperiode</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>3<sup>de</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="../../introduction/cookies.md#section-7ff7d96d6e4141b08a84a75a63d7814c" format="dita" scope="local"> Experience Cloud-id (MID)  </a> </p> </td> 
   <td colname="col3"> <p>De browser van de bezoeker accepteert cookies van de eerste partij. Dit wordt ingesteld door het AMCV-cookie. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>4<sup>e</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/analytics-ids.html" format="http" scope="external"> fid (fallback-cookie op H.25.3 of hoger, of AppMeasurement voor JavaScript)</a> </p> </td> 
   <td colname="col3"> <p>Een browser accepteert geen cookies van derden en de Analytics tracking-server is ingesteld als een externe tracingserver. </p> <p> <p>Opmerking: De <span class="codeph"> fid</span> is een oudere id en wordt niet gebruikt als u de id-service op uw site hebt geïmplementeerd. In dit geval is de <span class="codeph"> fid</span> niet nodig omdat de cookie<a href="../../introduction/cookies.md" format="dita" scope="local"> AMCV cookie</a> van de eerste partij deze verouderd maakt. Het is om historische redenen en ter ondersteuning van de oude code gehandhaafd. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>5<sup>e</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/analytics/technotes/visitor-identification.html" format="http" scope="external"> IP Adres, de Agent van de Gebruiker, IP van de Gateway Adres</a> </p> </td> 
   <td colname="col3"> <p>De browser van de bezoeker accepteert geen cookies. </p> </td> 
  </tr> 
 </tbody> 
</table>
