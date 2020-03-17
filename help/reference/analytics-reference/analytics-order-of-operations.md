---
description: Nadat u de bezoekersidentiteitsservice hebt geïmplementeerd, zijn er vijf manieren waarop een bezoeker kan worden geïdentificeerd in Analytics.
keywords: ID Service
seo-description: Nadat u de bezoekersidentiteitsservice hebt geïmplementeerd, zijn er vijf manieren waarop een bezoeker kan worden geïdentificeerd in Analytics.
seo-title: Bewerkingsvolgorde voor analytische id's
title: Bewerkingsvolgorde voor analytische id's
uuid: cb1d136e-093f-43b0-a7e1-96f1e61fdad0
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# Bewerkingsvolgorde voor analytische id&#39;s{#order-of-operations-for-analytics-ids}

Nadat u de bezoekersidentiteitsservice hebt geïmplementeerd, zijn er vijf manieren waarop een bezoeker kan worden geïdentificeerd in Analytics.

In veel scenario&#39;s zou u 2 of 3 verschillende IDs op een vraag kunnen zien, maar de Analytics zal eerste identiteitskaart gebruiken huidig van die lijst als officiële [!DNL Experience Cloud] identiteitskaart. Als u bijvoorbeeld een aangepaste bezoeker-id instelt (die in de `vid` queryparameter is opgenomen), wordt die id gebruikt vóór andere id&#39;s die op dezelfde hit aanwezig kunnen zijn. Zie [Analytics instellen en Cloud-id&#39;s](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6) voor meer informatie instellen.

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
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_custom" format="http" scope="external"> vid (s.bezoekerID)</a> </p> </td> 
   <td colname="col3"> <p>De <span class="codeph"> s.bezoekerID</span> is ingesteld. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>2<sup>de</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_analytics" format="http" scope="external"> aid (s_vi cookie)</a> </p> </td> 
   <td colname="col3"> <p>De bezoeker had een bestaand s_vi koekje alvorens u de dienst van identiteitskaart van de <span class="keyword"> Ervaring Cloud</span> opstelde, of u hebt een <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> gevormde respijtperiode</a> . </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>3<sup>de</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="../../introduction/cookies.md#section-7ff7d96d6e4141b08a84a75a63d7814c" format="dita" scope="local"> Experience Cloud ID (MID) </a> </p> </td> 
   <td colname="col3"> <p>De browser van de bezoeker accepteert cookies van de eerste partij. Dit wordt ingesteld door het AMCV-cookie. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>4<sup>e</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> fid (fallback-cookie op H.25.3 of hoger, of AppMeasurement voor JavaScript)</a> </p> </td> 
   <td colname="col3"> <p>Een browser accepteert geen cookies van derden en de Analytics tracking-server is ingesteld als een externe tracingserver. </p> <p> <p>Opmerking: Het bestand <span class="codeph"> Fid</span> is een oudere id en wordt niet gebruikt als u de id-service op uw site hebt geïmplementeerd. In dit geval is het <span class="codeph"> bestand</span> niet nodig omdat het door de eerste partij, <a href="../../introduction/cookies.md" format="dita" scope="local"> AMCV-cookie</a> , verouderd is. Het is om historische redenen en ter ondersteuning van de oude code gehandhaafd. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>5<sup>e</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> IP Adres, de Agent van de Gebruiker, IP van de Gateway Adres</a> </p> </td> 
   <td colname="col3"> <p>De browser van de bezoeker accepteert geen cookies. </p> </td> 
  </tr> 
 </tbody> 
</table>

