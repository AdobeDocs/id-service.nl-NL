---
description: Een beleid van de Veiligheid van de Inhoud (CSP) is een kopbal en veiligheidseigenschap van HTTP die browsers controle over geeft welk type van middelen op een Web-pagina worden geladen. Herzie deze sectie als u de dienst van identiteitskaart gebruikt en strikte CSPs hebt die whitelists gebruiken om middelen van vertrouwde op domeinen goed te keuren. U moet de hier vermelde Adobe-domeinen toevoegen aan uw CSP-whitelist.
keywords: ID Service
seo-description: Een beleid van de Veiligheid van de Inhoud (CSP) is een kopbal en veiligheidseigenschap van HTTP die browsers controle over geeft welk type van middelen op een Web-pagina worden geladen. Herzie deze sectie als u de dienst van identiteitskaart gebruikt en strikte CSPs hebt die whitelists gebruiken om middelen van vertrouwde op domeinen goed te keuren. U moet de hier vermelde Adobe-domeinen toevoegen aan uw CSP-whitelist.
seo-title: Het Beleid van de Veiligheid van de inhoud en de Dienst van de Identiteit van de Experience Cloud
title: Het Beleid van de Veiligheid van de inhoud en de Dienst van de Identiteit van de Experience Cloud
uuid: 7399edf3-01c1-4730-834e-e2dd2c5791ff
translation-type: tm+mt
source-git-commit: ddff95876722b981f22c7e3196ff2ce9b696010e
workflow-type: tm+mt
source-wordcount: '619'
ht-degree: 0%

---


# Het Beleid van de Veiligheid van de inhoud en de Dienst van de Identiteit van de Experience Cloud {#content-security-policies-and-the-experience-cloud-id-service}

Een beleid van de Veiligheid van de Inhoud (CSP) is een kopbal en veiligheidseigenschap van HTTP die browsers controle over geeft welk type van middelen op een Web-pagina worden geladen. Herzie deze sectie als u de dienst van identiteitskaart gebruikt en strikte CSPs hebt die whitelists gebruiken om middelen van vertrouwde op domeinen goed te keuren. U moet de hier vermelde Adobe-domeinen toevoegen aan uw CSP-whitelist.

## CSP-revisie {#section-5fde5c00a678455c914b8307a8caab82}

CSPs gebruikt de kopbal van HTTP `Content-Security-Policy` om het type van middelen te controleren een browsers goedkeuren of laden op een pagina. Het toepassen van een CDV kan u helpen voorkomen:

* JavaScript-bestanden die worden geladen als de bron onbekend is of niet in een whitelist is opgenomen.
* XS-aanvallen (cross-site scripting).
* Aanvallen op gegevensinjectie.
* Aanvallen op verval van de site.
* Distributie van malware.

Het gebruik van CDV’s is gebruikelijk en goed begrepen. Het is niet de bedoeling van deze documentatie om CDV&#39;s in detail uit te leggen (zie de gerelateerde informatiekoppelingen hieronder voor meer informatie). Wat belangrijk is, is dat u begrijpt welke Adobe domeinnamen u aan CSP zou moeten toevoegen als u deze gebruikt en strak veiligheidsbeleid hebt. Door deze domeinen toe te voegen, kunnen bezoekersbrowsers die toegang hebben tot uw site, die belangrijke aanroepen uitvoeren naar Experience Cloud-bronnen die u gebruikt.

## Experience Cloud Domeinen voor wittekentabel {#section-30693e9a96834edfbf04de9e698cf2aa}

Voeg deze domeinnamen of URLs aan uw CSP voor elke Experience Cloud oplossing of de dienst toe van de lijst die u gebruikt.

<table id="table_EC9FC999A62D4B7A830CE73B0AB9EF3C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Experience Cloud-oplossing of -service </th> 
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
   <td colname="col1"> <p> <b>Target</b> </p> </td> 
   <td colname="col2"> <p>Wijzig uw CSP om <span class="codeph"> *.tt.omtr dc.net</span>op te nemen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Experience Cloud ID-service en Audience Manager</b> </p> </td> 
   <td colname="col2"> <p>Wijzig uw CSP om de hieronder domeinen te omvatten.</p> 
   <p><ul>
   <li>connect-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>img-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>script-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>frame-src 'self' <code>https://*.demdex.net;</code></li>
   <li>Als u Adobe Launch gebruikt om tags te implementeren, moet u deze ook toevoegen <code>https://assets.adobedtm.com</code> aan de lijst met domeinen.</li></ul></p> <p>De vraag aan het <span class="codeph"> demdex.net</span> domein wordt gebruikt om de <a href="../introduction/cookies.md" format="dita" scope="local"> Koekjes en de Dienst</a> van de Identiteit van de Experience Cloud en voor de syncs van identiteitskaart te produceren. See also, <a href="https://docs.adobe.com/content/help/en/audience-manager/user-guide/reference/demdex-calls.html" format="https" scope="external"> Understanding Calls to the Demdex Domain</a>. </p> </td> </tr> 
 <tr>
 <td colname="col1"> <p> <b>Activity Map-insteekmodule</b> </p> </td> 
 <td colname="col2"> <p>Wijzig uw CSP om *.adobe.com te omvatten. **Opmerking**: Als er al Activity Map is geïnstalleerd vóór januari 2020, wordt er een eerste aanvraag voor *.omniture.com weergegeven in uw browser, maar wordt deze omgeleid naar *.adobe.com. </p></td> 
 </tr>
 <tr>
 <td colname="col1"> <p> <b>Advertising Analytics</b> </p> </td> 
 <td colname="col2"> <p>Als u controles op de parameters van het vraagkoord hebt, ben zeker om de parameters ` s_kwcid ` en ` te whiteliseren ` s_kwcid` en ` ef_id`. Technisch gezien gebruikt Advertising Analytics alleen 's_kwcid', maar als je Ad Cloud Search of DSP ophaalt, gebruikt het ook 'ef_id'. Deze parameters voor queryreeksen zijn alfanumeriek. De parameter ` s_kwcid ` gebruikt "!" en de parameter ` ef_id' gebruikt het teken ':'. Als u "!" blokkeert in de URL moet u ook een whitelist toevoegen.</p></td> 
 </tr>
 </tbody> 
</table>

>[!MORELIKETHIS]
>
>* [Content Security Policy Reference](https://content-security-policy.com/)
>* [MDN: Beveiligingsbeleid voor inhoud](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP)
>* [Wikipedia: Beveiligingsbeleid voor inhoud](https://en.wikipedia.org/wiki/Content_Security_Policy)

