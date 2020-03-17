---
description: Een beleid van de Veiligheid van de Inhoud (CSP) is een kopbal en veiligheidseigenschap van HTTP die browsers controle over geeft welk type van middelen op een Web-pagina worden geladen. Herzie deze sectie als u de dienst van identiteitskaart gebruikt en strikte CSPs hebt die whitelists gebruiken om middelen van vertrouwde op domeinen goed te keuren. U moet de Adobe-domeinen die hier worden vermeld, toevoegen aan uw CSP-whitelist.
keywords: ID Service
seo-description: Een beleid van de Veiligheid van de Inhoud (CSP) is een kopbal en veiligheidseigenschap van HTTP die browsers controle over geeft welk type van middelen op een Web-pagina worden geladen. Herzie deze sectie als u de dienst van identiteitskaart gebruikt en strikte CSPs hebt die whitelists gebruiken om middelen van vertrouwde op domeinen goed te keuren. U moet de Adobe-domeinen die hier worden vermeld, toevoegen aan uw CSP-whitelist.
seo-title: Beleid voor inhoudsbeveiliging en de Experience Cloud Identity Service
title: Beleid voor inhoudsbeveiliging en de Experience Cloud Identity Service
uuid: 7399edf3-01c1-4730-834e-e2dd2c5791ff
translation-type: tm+mt
source-git-commit: 7255228470a59a537251c3a3eec686f52a2b76ec

---


# Beleid voor inhoudsbeveiliging en de Experience Cloud Identity Service {#content-security-policies-and-the-experience-cloud-id-service}

Een beleid van de Veiligheid van de Inhoud (CSP) is een kopbal en veiligheidseigenschap van HTTP die browsers controle over geeft welk type van middelen op een Web-pagina worden geladen. Herzie deze sectie als u de dienst van identiteitskaart gebruikt en strikte CSPs hebt die whitelists gebruiken om middelen van vertrouwde op domeinen goed te keuren. U moet de Adobe-domeinen die hier worden vermeld, toevoegen aan uw CSP-whitelist.

## CSP-revisie {#section-5fde5c00a678455c914b8307a8caab82}

CSPs gebruikt de kopbal van HTTP `Content-Security-Policy` om het type van middelen te controleren een browsers goedkeuren of laden op een pagina. Het toepassen van een CDV kan u helpen voorkomen:

* JavaScript-bestanden die worden geladen als de bron onbekend is of niet in een whitelist is opgenomen.
* XS-aanvallen (cross-site scripting).
* Aanvallen op gegevensinjectie.
* Aanvallen op verval van de site.
* Distributie van malware.

Het gebruik van CDV’s is gebruikelijk en goed begrepen. Het is niet de bedoeling van deze documentatie om CDV&#39;s in detail uit te leggen (zie de gerelateerde informatiekoppelingen hieronder voor meer informatie). Belangrijk is dat u begrijpt welke Adobe-domeinnamen u aan een CSP moet toevoegen als u deze gebruikt en een strak beveiligingsbeleid hebt. Als u deze domeinen toevoegt, kunnen bezoekersbrowsers die toegang hebben tot uw site die belangrijke aanroepen naar de bronnen van de Experience Cloud die u gebruikt.

## Ervaar Cloud Domains voor whitelisting {#section-30693e9a96834edfbf04de9e698cf2aa}

Voeg deze domeinnamen of URL&#39;s toe aan uw CSP voor elke lijst Experience Cloud-oplossing of -service die u gebruikt.

<table id="table_EC9FC999A62D4B7A830CE73B0AB9EF3C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Ervaar Cloud-oplossing of -service </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>AppMeasurement</b> </p> </td> 
   <td colname="col2"> <p>Wijzig uw CSP om het volgende op te nemen: </p> <p> 
     <ul id="ul_7522AE83A03A4115A84DF5B32D6DD79B"> 
      <li id="li_AB1EC161FB154BEDA1BEFE76C8A38A90"> <span class="codeph"> *.2o7.net</span> </li> 
      <li id="li_4B12A283716746949201528CD6AF529E"> <span class="codeph"> *.omtr dc.net</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Doel</b> </p> </td> 
   <td colname="col2"> <p>Wijzig uw CSP om <span class="codeph"> *.tt.omtr dc.net</span>op te nemen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Experience Cloud ID Service en Audience Manager</b> </p> </td> 
   <td colname="col2"> <p>Wijzig uw CSP om de hieronder domeinen te omvatten.</p> 
   <p><ul>
   <li>connect-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>img-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>script-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>frame-src 'self' <code>https://*.demdex.net;</code></li>
   <li>Als u labels implementeert met Adobe Launch, moet u deze ook toevoegen <code>https://assets.adobedtm.com</code> aan de lijst met domeinen.</li></ul></p> <p>Aanroepen naar het <span class="codeph"> domein demdex.net</span> worden gebruikt om de <a href="../introduction/cookies.md" format="dita" scope="local"> cookies en de Experience Cloud Identity Service</a> en voor ID-syncs te genereren. Zie ook, het <a href="https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html" format="https" scope="external"> Begrijpen van Vraag aan het Domein</a>van de Index. </p> </td> </tr> 
 <tr>
 <td colname="col1"> <p> <b>Insteekmodule Activity Map</b> </p> </td> 
 <td colname="col2"> <p>Wijzig uw CSP om *.adobe.com te omvatten. **Opmerking**: Als u Activiteitenkaart al vóór Januari, 2020 had geïnstalleerd, zal uw browser nog een eerste verzoek aan *.omniture.com zien, maar zal aan *.adobe.com worden opnieuw gericht. </p></td> 
 </tr>
 </tbody> 
</table>

>[!MORELIKETHIS]
>* [Content Security Policy Reference](https://content-security-policy.com/)
>* [MDN: Beveiligingsbeleid voor inhoud](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP)
>* [Wikipedia: Beveiligingsbeleid voor inhoud](https://en.wikipedia.org/wiki/Content_Security_Policy)
