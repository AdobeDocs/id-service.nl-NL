---
description: De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van het Experience Cloud voor 2017.
keywords: ID-service
title: Opmerkingen bij de release 2017
exl-id: 0b51d3b1-e405-4473-9e1a-f89a55250e5e
source-git-commit: 384b292413bbc7e43ade97e442ab7195f3b26c7a
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 1%

---

# Opmerkingen bij de release 2017 {#release-notes}

De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van het Experience Cloud voor 2017.

Deze veranderingen worden ook gevangen in de [ nota&#39;s van de Versie van het Experience Cloud ](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=nl).

>[!NOTE]
>
>Er zijn geen klantgerichte versienota&#39;s of codeveranderingen voor Maart, April, Mei, en Oktober 2017. Voor die maanden bleef de ID-servicecode ongewijzigd op v2.1.

## Versie 2.5 {#section-27b441509124493f80984ed09bd9e88b}

september 2017

<!--
<p>
<note type="important">
ID service support for Internet Explorer 6, 7, and 8 is deprecated and will be discontinued in a future release.
</note> </p>
-->

<table id="table_FD24C06C7B3547C3A7673C46B1852A35"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Functie </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> getVisitorValues </span> </p> </td> 
   <td colname="col2"> <p>Dit is een asynchrone API die herkenningstekens voor Analytics, de dienst van identiteitskaart, de optieoptie van de gegevensinzameling, geografische plaats, en meta-gegevens "blob"inhoud door gebrek terugkeert. U kunt ook bepalen welke id's u wilt retourneren met de optionele <span class="codeph"> bezoeker.FIELDS </span> -opsomming. Zie <a href="../library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues </a> . </p> </td> 
  </tr> 
 </tbody> 
</table>

**Bugfixes en Andere Veranderingen**

* Probleem verholpen met betrekking tot Chrome die ertoe leidde dat de id-service een fout genereerde wanneer op de knop Vorige in die browser werd geklikt.
* De dienst van identiteitskaart hervat nu de syncs van identiteitskaart wanneer gebied identiteitskaart in de reactie van de gebeurtenisvraag verandert.
* Toegevoegde nieuwe documentatie, [ Beleid van de Veiligheid van de Inhoud en de Dienst van de Identiteit van het Experience Cloud ](/help/reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3), die verklaart hoe te whitelist vraag aan Adobe domeinen die door de dienst van identiteitskaart worden gebruikt.

<!-- ## Version 2.4 {#section-f4d1608dd8894f558a92b82e83321200}

August, 2017

<table id="table_D9623D34F4444B038F7835750932C8AA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Feature </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe</span> </p> </td> 
   <td colname="col2"> <p>An optional, Boolean configuration that determines if the ID service sends (or does not send) data to the Adobe Experience Cloud Device Co-op. See <a href="../library/function-vars/coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local"> isCoopSafe</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Revised Documentation**

Updated and revised the [FAQs](/help/faq-intro/faq-intro.md) to include separate FAQs for different [!DNL Experience Cloud] solutions. -->

## Versie 2.3 {#section-ae7b1cb1e52e4ca5a46b453a3ba1f571}

juli 2017

<table id="table_1448040D09B94A74883A694FCF91EB33"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Functie </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> soundParamExpiry </span> </p> </td> 
   <td colname="col2"> <p>Wanneer toegevoegd aan de <span class="codeph"> Visitor.getInstance </span> functie, laat deze configuratie u het standaard Supplemental het vervalinterval van Gegevens van identiteitskaart (SDID) met voeten treden wanneer het overgaan van die identiteitskaart van één pagina aan een andere. U zou <span class="codeph"> soundParamExpiry </span> met <span class="codeph"> appendSupplimentalDataTo </span> helperfunctie gebruiken. Zie <a href="../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458" format="dita" scope="local"> soundParamExpiry </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> resetState </span> </p> </td> 
   <td colname="col2"> <p>Deze functie is vooral ontworpen voor klanten van A4T om problemen op te lossen die verband houden met het werken met id's op sites/schermen of apps van één pagina. Zie <a href="../library/get-set/resetstate.md#reference-47fc00ae139042d795d78244d9970139" format="dita" scope="local"> resetState </a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Bugfixes en Andere Veranderingen**

* Oplossing voor een bug in VisitorAPI.js v2.2 die ervoor zorgde dat de id-service en het doel niet in Internet Explorer konden samenwerken.
* De herziene code helpt verbeteren hoe de dienst van identiteitskaart gegevens naar het Publiceren van de Bestemming iFrame verzendt. Dit helpt het CPU-gebruik te verminderen.

## Versie 2.2 {#section-b7dee2495c29470e9b3a3132ec1fd951}

Releasedatum: juni 2017

<table id="table_7E412383E89D46759B00FE7328C9946F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Functie </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/whitelistdomain.md#reference-999899ff7b5b429a8824c9db7a379808" format="dita" scope="local"> whitelistParentDomain en whitelistIframeDomains </a> </p> </td> 
   <td colname="col2"> <p>Deze configuraties laten verschillende instanties van de de dienstcode van identiteitskaart die in een iFrame en op de ouderpagina wordt uitgevoerd met elkaar communiceren. Zij worden ontworpen helpen problemen met 2 specifieke gebruiksgevallen oplossen waar u of niet de ouderpagina/het domein kunt controleren en u hebt de dienstcode van identiteitskaart die in iFrame van een domein laadt dat u controle hebt. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Documentatieupdates voor mei {#section-1d36b91bb7a140ce8a145251ffac9f2f}

<table id="table_CD031A716A694E8FA89695C9B614BC91"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Onderwerp </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../faq-intro/faq.md" format="dita" scope="local"> Veelgestelde vragen </a> </p> </td> 
   <td colname="col2"> <p>De sectie <span class="keyword"> Analytics </span> is bijgewerkt met informatie over het zoeken naar informatie over de trackingserver. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Documentatieupdates voor april {#section-df3e5a85448c4001a6791517520ae06e}

<table id="table_ADC2636240654C69B8B6A45849024540"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Onderwerp </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/subdomain-config.md#reference-8ad017b3e5d24d34b3da25e8f8a56196" format="dita" scope="local"> publiekManagerServer en publiekManagerServerSecure </a> </p> </td> 
   <td colname="col2"> <p>Toegevoegde verbindingen aan <span class="keyword"> Audience Manager </span> documentatie die vraag aan het <span class="codeph"> demdex.net </span> domein beschrijft. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/subdomain-config.md" format="dita" scope="local"> ID-synchronisatie en overeenkomstige snelheden </a> </p> </td> 
   <td colname="col2"> <p>Herziene <span class="keyword"> Media Optimizer </span> sectie om de vraag aan <span class="codeph"> cm.eversttech.net </span> te beschrijven. Dit is de automatische synchronisatie van identiteitskaart die de dienst van identiteitskaart met <span class="keyword"> Media Optimizer </span> uitvoert. Deze functie is gepubliceerd in januari 2017. Zie <a href="../release-notes/notes-2017.md#section-0ceac6007c1241b58ad607e2b76b2b7e" format="dita" scope="local"> Versie 2.0 </a> hieronder. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Versie 2.1 {#section-5e666dc47c2f4f92999e92697d75799e}

Releasedatum: februari 2017

**Eigenschappen**

<table id="table_1F7E1CF091604D22B1D9F3F1AE4DB2D7"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Functie </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> ID service API-eigenschap, <span class="codeph"> idSyncContainerID </span></p> </td> 
   <td colname="col2"> <p>Deze eigenschap stelt de container-id in die door <span class="keyword"> Audience Manager </span> wordt gebruikt voor id-syncs. Zie <a href="/help/library/function-vars/idsyncontainerid.md" format="https" scope="external"> idSyncContainerID </a> . </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>De dienstAPI van identiteitskaart methode, <span class="codeph"> appendSupplementalDataIDTo (<span class="varname"> URL </span>, <span class="varname"> SDID </span>) </span></p> </td> 
   <td colname="col2"> <p>Deze openbare methode voegt <span class="wintitle"> Supplemental identiteitskaart van Gegevens </span> (SDID) als parameter van het vraagkoord aan opnieuw richt URL toe. Zie <a href="../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d" format="dita" scope="local"> appendSupplementalDataIDTo </a> . (MCID-285) </p> </td> 
  </tr> 
 </tbody> 
</table>

**Oplossingen**

Oplossing voor een probleem dat ertoe leidde dat de id-service redundante serveraanroepen voor een id maakte in plaats van de id te gebruiken die in het AMCV-cookie was opgeslagen. (MCID-296)

**Nieuwe Documentatie**

[ Gebruikend DNS Prefetch met Verschillende Oplossingen en de Diensten van het Experience Cloud ](https://experienceleague.adobe.com/docs/core-services/interface/more-resources/dns-prefetch.html?lang=nl-NL)

## Versie 2.0 {#section-0ceac6007c1241b58ad607e2b76b2b7e}

januari 2017

>[!IMPORTANT]
>
>Met de ID-servicecode v2.0 worden id&#39;s standaard automatisch gesynchroniseerd met Adobe Media Optimizer. Dit betekent dat er een aanroep van de pagina naar `cm.eversttech.net` wordt weergegeven. Dit is een verouderd [!DNL Media Optimizer] domein dat door [!DNL Adobe] wordt beheerd. Zie ook, [ Begrijpend de Synchronisatie van identiteitskaart en Gelijke Tarieven ](../introduction/match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab).

**Bevestigingen en Verbeteringen**

* Oplossing voor een bug waardoor AppMeasurement geen traceeraanroepen naar Analytics kon uitvoeren. (MCID-254, MCID-256, MCID-286)
* Oplossing voor een probleem dat ervoor zorgde dat de id-service niet meteen kon mislukken als een bezoeker een advertentieblokker had ingeschakeld en die blokkering was geconfigureerd om het domein demdex.net uit te sluiten. Dit is een zeldzame en ongebruikelijke bug omdat de meeste hulpprogramma&#39;s voor het blokkeren van advertenties het domein demdex.net niet blokkeren. (MCID-233)
* Oplossing voor een bug die werd veroorzaakt door interacties tussen ID-servicecode en een aangepast script op de website van een klant. Hierdoor kon Internet Explorer 9 geen webpagina&#39;s laden. (MCID-206)

## Vorige jaren {#section-aaabe2b7b0f04641b24acffc11cd7d2e}

Opmerkingen bij de release van oudere id-services.
