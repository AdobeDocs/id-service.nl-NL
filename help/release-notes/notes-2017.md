---
description: Functies worden vrijgegeven, bijgewerkt of gewijzigd in de Experience Cloud Identity Service voor 2017.
keywords: ID Service
seo-description: Functies worden vrijgegeven, bijgewerkt of gewijzigd in de Experience Cloud Identity Service voor 2017.
seo-title: Opmerkingen bij de release 2017
title: Opmerkingen bij de release 2017
uuid: 79452df0-49db-42b8-96fe-01aa7629fbb5
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Opmerkingen bij de release 2017 {#release-notes}

Functies worden vrijgegeven, bijgewerkt of gewijzigd in de Experience Cloud Identity Service voor 2017.

Deze wijzigingen worden ook vastgelegd in de opmerkingen bij de release [Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/). Zie de opmerkingen bij de [vorige release](https://marketing.adobe.com/resources/help/en_US/whatsnew/?f=c_legacy_releases.html) of de koppelingen onder aan deze pagina voor opmerkingen bij de oudere ID-service.

>[!NOTE]
>
>Er zijn geen klant-onder ogen ziet versienota&#39;s of codeveranderingen voor Maart, April, Mei, en Oktober 2017. Voor die maanden bleef de ID-servicecode ongewijzigd op v2.1.

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
   <td colname="col1"> <p> <span class="codeph"> getVisitorValues</span> </p> </td> 
   <td colname="col2"> <p>Dit is een asynchrone API die herkenningstekens voor Analytics, de dienst van identiteitskaart, de optieoptie van de gegevensinzameling, geografische plaats, en meta-gegevens "blob"inhoud door gebrek terugkeert. U kunt ook bepalen welke id's u wilt retourneren met de optionele <span class="codeph"> name bezoeker.FIELDS</span> . Zie <a href="../library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Opgeloste problemen en andere wijzigingen**

* Oplossing voor een Chrome-gerelateerde fout die ervoor zorgde dat de id-service een fout genereerde wanneer op de knop Vorige in die browser werd geklikt.
* De dienst van identiteitskaart hervat nu de syncs van identiteitskaart wanneer gebied identiteitskaart in de reactie van de gebeurtenisvraag verandert.
* Er is nieuwe documentatie toegevoegd, het beveiligingsbeleid voor [inhoud en de Experience Cloud Identity Service](/help/reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3), waarin wordt uitgelegd hoe u aanroepen naar Adobe-domeinen die door de id-service worden gebruikt, kunt whitelist.

## Versie 2.4 {#section-f4d1608dd8894f558a92b82e83321200}

augustus 2017

<table id="table_D9623D34F4444B038F7835750932C8AA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Functie </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe</span> </p> </td> 
   <td colname="col2"> <p>Een optionele, Booleaanse configuratie die bepaalt of de id-service gegevens verzendt (of niet verzendt) naar de Adobe Experience Cloud Device Co-op. Zie <a href="../library/function-vars/coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local"> CoopSafe</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Herziene documentatie**

Bijgewerkt en herzien de [Veelgestelde vragen](/help/faq-intro/faq-intro.md) om afzonderlijke veelgestelde vragen voor verschillende [!DNL Experience Cloud] oplossingen op te nemen.

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
   <td colname="col1"> <p> <span class="codeph"> sdidParamExpiry</span> </p> </td> 
   <td colname="col2"> <p>Wanneer toegevoegd aan de functie <span class="codeph"> Visitor.getInstance</span> , laat deze configuratie u het standaard Supplemental interval van de Vervaltijd van Gegevens - identiteitskaart (SDID) met voeten treden wanneer het overgaan van die identiteitskaart van één pagina aan een andere. U zou <span class="codeph"> sdidParamExpiry</span> met de <span class="codeph"> appendSupplimentalDataTo</span> hulpfunctie gebruiken. Zie <a href="../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458" format="dita" scope="local"> doParamExiry</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> resetState</span> </p> </td> 
   <td colname="col2"> <p>Deze functie is vooral ontworpen voor klanten van A4T om problemen op te lossen die verband houden met het werken met id's op sites/schermen of apps van één pagina. Zie <a href="../library/get-set/resetstate.md#reference-47fc00ae139042d795d78244d9970139" format="dita" scope="local"> resetState</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Opgeloste problemen en andere wijzigingen**

* Oplossing voor een bug in VisitorAPI.js v2.2 die ervoor zorgde dat de id-service en het doel niet in Internet Explorer konden samenwerken.
* De herziene code helpt verbeteren hoe de dienst van identiteitskaart gegevens naar het Publiceren van de Bestemming iFrame verzendt. Dit helpt het CPU-gebruik te verminderen.

## Versie 2.2 {#section-b7dee2495c29470e9b3a3132ec1fd951}

Releasedatum: Juni 2017

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
   <td colname="col2"> <p>De sectie <span class="keyword"> Analytics</span> is bijgewerkt met informatie over het zoeken naar informatie over de trackingserver. </p> </td> 
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
   <td colname="col2"> <p>Toegevoegde verbindingen aan de documentatie van de Manager <span class="keyword"> van de Audience die vraag aan het</span> demdex.net <span class="codeph"></span> domein beschrijft. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/subdomain-config.md" format="dita" scope="local"> Identiteitssynchronisatie en gelijke Tarieven begrijpen </a> </p> </td> 
   <td colname="col2"> <p>De herziene sectie van <span class="keyword"> Media Optimizer</span> om de vraag aan <span class="codeph"> cm.eversttech.net</span>te beschrijven. Dit is de automatische synchronisatie van id's die de id-service uitvoert met <span class="keyword"> Media Optimizer</span>. Deze functie is gepubliceerd in januari 2017. Zie <a href="../release-notes/notes-2017.md#section-0ceac6007c1241b58ad607e2b76b2b7e" format="dita" scope="local"> versie 2.0</a> hieronder. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Versie 2.1 {#section-5e666dc47c2f4f92999e92697d75799e}

Releasedatum: februari 2017

**Functies**

<table id="table_1F7E1CF091604D22B1D9F3F1AE4DB2D7"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Functie </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> ID service-API-eigenschap, <span class="codeph"> idSyncContainerID</span></p> </td> 
   <td colname="col2"> <p>Deze eigenschap stelt de container-id in die door Audience Manager <span class="keyword"></span> wordt gebruikt voor id-syncs. Zie <a href="/help/library/function-vars/idsyncontainerid.md" format="https" scope="external"> idSyncContainerID</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>ID-service-API-methode, <span class="codeph">appendSupplementalDataIDTo(<span class="varname"> URL</span>,<span class="varname"> SDID</span>)</span></p> </td> 
   <td colname="col2"> <p>Deze openbare methode voegt de <span class="wintitle"> Extra identiteitskaart</span> van Gegevens (SDID) als parameter van het vraagkoord aan een omleidingsURL toe. Zie <a href="../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d" format="dita" scope="local"> appendSupplementalDataIDTo</a>. (MCID-285) </p> </td> 
  </tr> 
 </tbody> 
</table>

**Oplossingen**

Oplossing voor een probleem dat ertoe leidde dat de id-service redundante serveraanroepen voor een id maakte in plaats van de id te gebruiken die in het AMCV-cookie was opgeslagen. (MCID-296)

**Nieuwe documentatie**

[DNS Prefetch gebruiken met de Verschillende Oplossingen en de Diensten van de Wolk van de Ervaring `Learn how to use DNS prefetch to help reduce page load times.`](https://marketing.adobe.com/resources/help/en_US/mcloud/dns-prefetch.html)

## Versie 2.0 {#section-0ceac6007c1241b58ad607e2b76b2b7e}

januari 2017

>[!IMPORTANT]
>
>Met de ID-servicecode v2.0 worden id&#39;s standaard automatisch gesynchroniseerd met Adobe Media Optimizer. Dit betekent u een vraag van de pagina aan zult zien `cm.eversttech.net`, die een erfenisdomein is dat door wordt gecontroleerd [!DNL Media Optimizer] [!DNL Adobe]. Zie ook, [Begrijpend de Synchronisatie van identiteitskaart en Gelijke Tarieven](../introduction/match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab).

**Oplossingen en verbeteringen**

* Oplossing voor een probleem dat ervoor zorgde dat AppMeasurement geen volgende aanroepen naar Analytics kon maken. (MCID-254, MCID-256, MCID-286)
* Oplossing voor een probleem dat ervoor zorgde dat de id-service niet meteen kon mislukken als een bezoeker een advertentieblokker had ingeschakeld en die blokker was geconfigureerd om het domein demdex.net uit te sluiten. Dit is een zeldzame en ongebruikelijke bug omdat de meeste hulpmiddelen voor het blokkeren van advertenties het domein demdex.net niet blokkeren. (MCID-233)
* Oplossing voor een bug die werd veroorzaakt door interacties tussen ID-servicecode en een aangepast script op de website van een klant. Hierdoor kon Internet Explorer 9 geen webpagina&#39;s laden. (MCID-206)

## Vorige jaren {#section-aaabe2b7b0f04641b24acffc11cd7d2e}

Opmerkingen bij de release van oudere id-services.