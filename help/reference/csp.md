---
description: Een beleid van de Veiligheid van de Inhoud (CSP) is een kopbal en veiligheidseigenschap van HTTP die browsers controle over geeft welk type van middelen op een Web-pagina worden geladen. Herzie deze sectie als u de dienst van identiteitskaart gebruikt en strikte CSPs hebt die lijsten van gewenste personen gebruiken om middelen van vertrouwde op domeinen goed te keuren. U moet de Adobe-domeinen die hier worden vermeld, toevoegen aan uw CSP-lijsten van gewenste personen.
keywords: ID-service
title: Beleid voor inhoudsbeveiliging en de Experience Cloud Identity Service
exl-id: e35c6809-764e-4c3e-9139-88bb92e82338
source-git-commit: c56bbaa6a3639e421c11a8231e14afb58a4fa305
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# Beleid voor inhoudsbeveiliging en de Experience Cloud Identity Service {#content-security-policies-and-the-experience-cloud-id-service}

Een beleid van de Veiligheid van de Inhoud (CSP) is een kopbal en veiligheidseigenschap van HTTP die browsers controle over geeft welk type van middelen op een Web-pagina worden geladen. Herzie deze sectie als u de dienst van identiteitskaart gebruikt en strikte CSPs hebt die lijsten van gewenste personen gebruiken om middelen van vertrouwde op domeinen goed te keuren. U moet de Adobe-domeinen die hier worden vermeld, toevoegen aan uw CSP-lijsten van gewenste personen.

## CSP-revisie {#section-5fde5c00a678455c914b8307a8caab82}

CSPs gebruikt de kopbal van HTTP `Content-Security-Policy` om het type van middelen te controleren een browsers goedkeuren of laden op een pagina. Het toepassen van een CDV kan u helpen voorkomen:

* JavaScript-bestanden van het laden als de bron onbekend is of niet is opgenomen in een lijst van gewenste personen.
* XS-aanvallen (cross-site scripting).
* Aanvallen op gegevensinjectie.
* Aanvallen op de defactie van de site.
* Distributie van malware.

Het gebruik van CDV’s is gebruikelijk en goed begrepen. Het is niet de bedoeling van deze documentatie om CDV&#39;s in detail uit te leggen (zie de gerelateerde informatiekoppelingen hieronder voor meer informatie). Belangrijk is dat u begrijpt welke Adobe-domeinnamen u aan een CSP moet toevoegen als u deze gebruikt en een strak beveiligingsbeleid hebt. Als u deze domeinen toevoegt, kunnen bezoekerbrowsers die toegang krijgen tot uw site, die belangrijke aanroepen uitvoeren naar Experience Cloud-bronnen die u gebruikt.

## Experience Cloud Domains voor Voegende op lijst van gewenste personen doeleinden {#section-30693e9a96834edfbf04de9e698cf2aa}

Voeg deze domeinnamen of URL&#39;s toe aan uw CSP voor elke Experience Cloud-oplossing of -service die u gebruikt.

<table id="table_EC9FC999A62D4B7A830CE73B0AB9EF3C">
 <thead>
  <tr>
   <th colname="col1" class="entry">Experience Cloud Solution of Service</th>
   <th colname="col2" class="entry">Beschrijving</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1">
    <p><b>AppMeasurement</b></p>
   </td>
   <td colname="col2">
    <p>Wijzig uw CSP om het volgende op te nemen:</p>
    <ul id="ul_7522AE83A03A4115A84DF5B32D6DD79B">
     <li id="li_AB1EC161FB154BEDA1BEFE76C8A38A90"><span class="codeph">*.2o7.net</span></li>
     <li id="li_4B12A283716746949201528CD6AF529E"><span class="codeph">*.omtrdc.net</span></li>
    </ul>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Target</b></p>
   </td>
   <td colname="col2">
    <p>Wijzig CSP om <span class="codeph">*.tt.omtr dc.net </span> op te nemen.</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Experience Cloud ID Service en Audience Manager</b></p>
   </td>
   <td colname="col2">
    <p>Wijzig uw CSP om de hieronder domeinen te omvatten.</p>
    <ul>
     <li>connect-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>img-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>script-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>frame-src 'self' <code>https://*.demdex.net;</code></li>
     <li>Als u Adobe Launch gebruikt om tags te implementeren, moet u ook <code>https://assets.adobedtm.com</code> toevoegen aan de lijst met domeinen.</li>
    </ul>
    <p>De vraag aan het {<span class="codeph"> domein 0} demdex.net wordt gebruikt om de </span> Cookies en de Dienst van de Identiteit van Experience Cloud <a href="../introduction/cookies.md" format="dita" scope="local"> en voor de syncs van identiteitskaart te produceren. </a> Zie ook, <a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=nl-NL" format="https" scope="external"> Begrijpend Vraag aan het Domein van de Index </a>.</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Activity Map-insteekmodule</b></p>
   </td>
   <td colname="col2">
    <p>Wijzig uw CSP om *.adobe.com te omvatten. **Opmerking**: als Activity Map al vóór januari 2020 was geïnstalleerd, wordt een eerste aanvraag voor de browser weergegeven op *.omniture.com, maar wordt deze doorgestuurd naar *.adobe.com.</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Advertising Analytics</b></p>
   </td>
   <td colname="col2">
    <p>Als u de parameters van het vraagkoord beperkt, dan lijst van gewenste personen de volgende parameters:</p>
    <ul>
     <li><code>s_kwcid</code> (gebruikt <code>!</code>)</li>
     <li><code>ef_id</code> (gebruikt <code>:</code>)</li>
    </ul>
    <p>Als u het teken <code>!</code> in URLs blokkeert, dan lijst van gewenste personen het ook.</p>
    <p>Advertising Analytics gebruikt alleen <code>s_kwcid</code> , maar Advertising Search, Social &amp; Commerce en Advertising DSP gebruiken ook <code>ef_id</code> .</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Adobe Advertising</b></p>
   </td>
   <td colname="col2">
    <p>Wijzig uw CSP om de volgende domeinen te omvatten:</p>
    <ul>
     <li><code>.everestjs.net</code></li>
     <li><code>.everesttech.net</code></li>
    </ul>
   </td>
  </tr>
 </tbody>
</table>

>[!MORELIKETHIS]
>
>* [ Verwijzing van het Beleid van de Veiligheid van de Inhoud ](https://content-security-policy.com/)
>* [ MDN: Het Beleid van de Veiligheid van de inhoud ](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP)
>* [ Wikipedia: Het Beleid van de Veiligheid van de inhoud ](https://en.wikipedia.org/wiki/Content_Security_Policy)
