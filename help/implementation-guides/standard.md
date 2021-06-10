---
description: Oudere implementaties gebruiken Dynamic Tag Management (DTM) om de Experience Cloud Identity Service in te stellen, te implementeren en te integreren met uw andere Experience Cloud-oplossingen.
keywords: ID-service
title: Implementatie met dynamisch tagbeheer
exl-id: 37ccc919-3015-42fa-a88f-639cdf726f48
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '1999'
ht-degree: 1%

---

# Implementatie met dynamisch tagbeheer {#implementation-with-dynamic-tag-management}

Oudere implementaties gebruiken Dynamic Tag Management (DTM) om de Experience Cloud Identity Service in te stellen, te implementeren en te integreren met uw andere Experience Cloud-oplossingen.

## Implementatie met dynamisch tagbeheer {#topic-6f4ed5d96977406ca991e50f3fbd5b01}

Oudere implementaties gebruiken Dynamic Tag Management (DTM) om de Experience Cloud Identity Service in te stellen, te implementeren en te integreren met uw andere Experience Cloud-oplossingen.

>[!NOTE]
>
>Op dit moment is [Adobe Experience Platform Launch](https://experienceleague.adobe.com/docs/launch/using/home.html) het voorkeursprogramma voor implementatie, omdat het complexe taken voor tagbeheer vereenvoudigt en codeplaatsing automatiseert die verder gaat dan de mogelijkheden van DTM. Zie [Implementeren met starten](../implementation-guides/ecid-implement-with-launch.md).

## Dynamisch tagbeheer en de id-service {#section-4a4c4fac5d0a4cbbaff8e1833f73657c}

[Met Dynamic Tag ](https://docs.adobe.com/content/help/nl-NL/dtm/using/dtm-home.html) Management kunt u uw ID-serviceexemplaar en verwante  [!DNL Experience Cloud] oplossingsintegraties configureren, implementeren en beheren. DTM helpt het implementatieproces te vereenvoudigen, omdat het volledig is geïntegreerd met de id-service en andere Experience Cloud-oplossingen. U hoeft alleen het gereedschap Experience Cloud-id toe te voegen en te configureren en informatie op te geven, zoals:

* Organisatie-id Experience Cloud (automatisch ingevuld als deze is gekoppeld aan de Experience Cloud)
* Analytics tracking-server (beveiligd en niet beveiligd)
* Experience Cloud-server (voor &#39;first-party tracking&#39;-servers)

DTM is gratis beschikbaar voor elke [!DNL Experience Cloud]-klant.

**Aan de slag met DTM**

DTM is een eenvoudig maar krachtig hulpmiddel. Als u het nog niet gebruikt, raden we u aan dit te doen. Raadpleeg de [DTM-documentatie](https://docs.adobe.com/content/help/en/dtm/using/c-overview.html) om aan de slag te gaan met deze service. Zie de informatie en procedures in de volgende secties voor instructies over het instellen van de id-service met DTM.

## Richtlijnen voor implementatie {#concept-54a2ec49af8f4bfca9207b1d404e8e1a}

Controleer deze vereisten en procedures voordat u probeert de Experience Cloud Identity Service met Dynamic Tag Management (DTM) te implementeren.

<!--
mcvid-dtm-deployment.xml
-->

**Je account verstrekken**

Voordat u aan de slag kunt, moet u ervoor zorgen dat uw organisatie en oplossingen zijn ingericht voor de [!DNL Experience Cloud] en dat u bekend bent met [!DNL Dyanamic Tag Management]. Aan de slag met deze documentatie:

* [Laat uw oplossingen voor de kerndiensten](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html) toe: Voer de Experience Cloud uit en word een beheerder. Dit proces moderniseert uw oplossingen voor de kerndiensten zoals klantenattributen en Experience Cloud publiek.
* [Aan de slag met dynamisch tagbeheer](https://docs.adobe.com/content/help/en/dtm/using/getting-started/get-started.html)

**Plaatsing van ID-servicecode en laadvolgorde**

De id-service werkt door een unieke id op te vragen en te ontvangen van de gegevensverzamelingsservers van [!DNL Adobe]. De code van uw id-service werkt alleen correct als:

* Het eerste blok van [!DNL Adobe] code die op de pagina uitvoert.
* Geplaatst zo hoog mogelijk op de pagina, gewoonlijk binnen het `<head>` codeblok.

Zolang u al uw [!DNL Adobe] oplossingen en codebibliotheken in DTM handhaaft, zal het ervoor zorgen dat uw de dienstcode van identiteitskaart in de juiste plaats wordt geplaatst en op het juiste tijdstip in brand steekt.

**regionale gegevensverzameling valideren**

Klanten moeten een CNAME opgeven of `*.sc.omtrdc` gebruiken voor [regionale gegevensverzameling](https://docs.adobe.com/content/help/en/analytics/technotes/rdc/regional-data-collection.html) (RDC). Verkrijg de specifieke, RDC montages van uw [!DNL Adobe] consultant.

**Analytische rapportsuites configureren**

Nieuwe [!DNL Analytics] klanten moeten [een rapportsuite](https://docs.adobe.com/content/help/en/analytics/admin/manage-report-suites/new-report-suite/new-report-suite.html) voor gegevensverzameling maken.

## Implementeer de Experience Cloud Identity Service met DTM {#task-a659cf19dea84ad48edabe0b72ef9f5c}

Voer de volgende stappen uit om de id-service te implementeren met Dynamic Tag Management (DTM).

**Vereisten**

* Laat uw oplossingen voor [!DNL Experience Cloud] toe en verifieer dat u beheerdertoestemmingen hebt. Zie [Uw oplossingen inschakelen voor kernservices](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html).

* Maak een webeigenschap in DTM. Zie de DTM [Create a Web Property](https://docs.adobe.com/content/help/en/dtm/using/admin/web-property.html) documentatie.

<!--
mcvid-dtm-implement.xml
-->

**ImplementatiestappenDe id-service implementeren** met DTM:

1. Klik in de DTM [!UICONTROL Dashboard] op de webeigenschap waarmee u wilt werken.
1. Klik op het tabblad **[!UICONTROL Overview]** van de geselecteerde webeigenschap op **[!UICONTROL Add a Tool]**.
1. Klik in de lijst **[!UICONTROL Tool Type]** op **[!UICONTROL Experience Cloud Identity Service]**.

   >[!NOTE]
   >
   >Met deze handeling wordt het vak **[!UICONTROL Experience Cloud Organization ID]** gevuld met uw organisatie-id. Als uw DTM-account niet is gekoppeld aan [!DNL Experience Cloud], moet u deze id opgeven. Zie [Accounts koppelen in de Experience Cloud](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/organizations.html) om uw account te koppelen. Zie [requirements](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26) voor informatie over hoe te om uw identiteitskaart van de Organisatie te vinden.

1. Typ de naam van de volgende server in het tekstvak **[!UICONTROL Tracking Server]**. Als u niet zeker bent hoe te om uw het volgen server te vinden [FAQ](../faq-intro/faq.md) en [bevolkt correct trackingServer en trackingServerSecure variabelen](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).
1. Klik op **[!UICONTROL Create Tool]** en **[!UICONTROL Save Changes]**.

   Na het opslaan wordt de id-service ingesteld als een hulpprogramma in DTM. Het is echter nog niet gebruiksklaar. Uw DTM-tool moet nog steeds het publicatie-/goedkeuringsproces van DTM doorlopen en u kunt aanvullende parameters configureren. Voor informatie over de extra parameters u aan DTM kunt toevoegen, zie [Experience Cloud Montages van de Dienst van de Identiteit voor DTM](../implementation-guides/standard.md#concept-fb6cb6a0e6cc4f10b92371f8671f6b59).

## Experience Cloud Identiteitsservice-instellingen voor DTM {#concept-fb6cb6a0e6cc4f10b92371f8671f6b59}

Beschrijft de [!UICONTROL Organization ID], [!UICONTROL General] en [!UICONTROL Customer Settings] gebieden en hoe zij door de [!DNL Experience Cloud] dienst van identiteitskaart worden gebruikt.

<!--
mcvid-dtm-settings.xml
-->

## Hoe vind ik deze instellingen? {#section-c5b2d1c928944ae2b8565c1b182fe575}

De instellingen zijn beschikbaar nadat u de id-service hebt toegevoegd en opgeslagen als een programma in Dynamic Tag Management (DTM). U kunt tot deze montages ook toegang hebben door het tandwielpictogram van [!UICONTROL Installed Tools] sectie van uw DTM Webbezit te klikken.

![](assets/installedTools.png)

## Organisatie-id {#section-949b5a0d8af940558b04ff675cf53f77}

Dit is identiteitskaart die door wordt vereist en met uw provisioned [!DNL Experience Cloud] bedrijf wordt geassocieerd. Een organisatie is de entiteit die een beheerder toelaat om gebruikers, groepen te vormen, en enige sign-on toegang in [!DNL Experience Cloud] te controleren. De organisatie-id is een alfanumerieke tekenreeks van 24 tekens, gevolgd door (en moet bevatten) @AdobeOrg. [!DNL Experience Cloud] beheerders kunnen deze id vinden in  [Experience Cloud > Gereedschappen](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html).

![](assets/orgID.png)

Zie ook [Cookies en de Dienst van de Identiteit van de Experience Cloud](../introduction/cookies.md).

## Algemene instellingen {#section-071d358e40f84629a8901b893dd61392}

Met deze instellingen kunt u trackingservers, codeversies en andere variabelen opgeven.

![](assets/generalSettings.png)

In de volgende tabel worden de instellingen [!UICONTROL General] weergegeven en gedefinieerd.

**Visitor-id automatisch aanvragen**

Wanneer gecontroleerd, roept het Dynamische Beheer van de Markering automatisch de `getMarketingCloudVisitorID()` methode alvorens om het even welke oplossingen van de Adobe te laden die de Dienst van de Identiteit van de Experience Cloud gebruiken.

Zie [getMarketingCloudVisitorID](../library/get-set/getmcvid.md).

**Analytics Tracking Server**

De naam van de volgende server die voor de gegevensinzameling van Analytics wordt gebruikt. Dit is het domein waarop de afbeeldingsaanvraag en het cookie worden geschreven (bijvoorbeeld `http://site.omtrdc.net`).

Als u de URL&#39;s van de volgende server niet kent, controleert u de `s_code.js`- of `AppMeasurement.js`-bestanden. U zult URL die door de `s.trackingServer` variabele wordt geplaatst willen.

Zie [trackingServer](https://docs.adobe.com/content/help/en/analytics/implementation/vars/page-vars/page-variables.html) en [De variabele trackingServer en trackingServerSecure](https://helpx.adobe.com/analytics/kb/determining-data-center.html#) correct vullen.

**Beveiliging van trackingserver**

De naam van de veilige die volgserver voor de gegevensinzameling van Analytics wordt gebruikt. Dit is het domein waarop de afbeeldingsaanvraag en het cookie worden geschreven (bijvoorbeeld `https://site.omtrdc.net`).

Als u de URL&#39;s van de volgende server niet kent, controleert u de `s_code.js`- of `AppMeasurement.js`-bestanden. U zult URL die door de `s.trackingServerSecure` variabele wordt geplaatst willen.

Zie [trackingServer](https://docs.adobe.com/content/help/en/analytics/implementation/vars/page-vars/page-variables.html) en [De variabele trackingServer en trackingServerSecure](https://helpx.adobe.com/analytics/kb/determining-data-center.html#) correct vullen.

**Experience Cloud-server**

Als uw bedrijf gegevensverzameling van de eerste partij (CNAME) gebruikt om cookies van de eerste partij in een context van een derde te gebruiken, ga hier de volgende server in (b.v., `http://metrics.company.com`.)

**Experience Cloud Server beveiligd**

Als uw bedrijf gegevensverzameling van de eerste partij (CNAME) gebruikt om cookies van de eerste partij in een context van een derde te gebruiken, ga hier de volgende server in (b.v., `https://metrics.company.com`.)

**Bibliotheekversie**

Hiermee stelt u de versie in van de codebibliotheek met id-services ( `VisitorAPI.js`) die u wilt gebruiken. U kunt deze menuopties niet bewerken.

**Instellingen**

Met deze velden kunt u [functievariabelen](../library/function-vars/function-vars.md) toevoegen als sleutel-waardeparen. Klik **[!UICONTROL Add]** om één of meerdere variabelen aan uw de dienstimplementatie van identiteitskaart toe te voegen

![](assets/dtmVars.png)

>[!IMPORTANT]
>
>Stel hier de variabele `cookieDomain` in. Dit is vereist voor domeinen van het bovenste niveau met meerdere delen, waarbij een van de laatste twee delen van de URL uit meer dan twee tekens bestaat. Zie de hierboven verbonden documentatie van de Variabelen van de Configuratie.

## Klanteninstellingen {#section-238d1272c1504d148fe38fb0ae5d71c2}

Extra velden waarmee u een integratiecode of een geverifieerde statusstatus kunt toevoegen.

![](assets/customerSettings.png)

**Integratiecode**

Een integratiecode is een unieke, door de klant opgegeven id. De integratiecode zou de waarde moeten bevatten u aan [creeerde een gegevensbron](hhttps://docs.adobe.com/content/help/en/audience-manager/user-guide/features/data-sources/manage-datasources.html#create-data-source) in [!DNL Audience Manager] gebruikte.

**Value**

De waarde moet een gegevenselement zijn dat de gebruikers-id bevat. Gegevenselementen zijn geschikte containers voor dynamische waarden, zoals id&#39;s van een client-specifiek intern systeem.

**Deelstaat Auth**

Opties die bezoekers definiëren of identificeren op basis van hun verificatiestatus (bijvoorbeeld aangemeld, afgemeld). Zie [Klantnamen en verificatiestatus](../reference/authenticated-state.md).

## Test en verifieer de Experience Cloud Identiteitsdienst {#concept-644fdbef433b46ba9c0634ac95eaa680}

Deze instructies, hulpmiddelen, en procedures helpen u bepalen als de dienst van identiteitskaart behoorlijk werkt. Deze tests zijn van toepassing op de dienst van identiteitskaart in het algemeen en voor verschillende de dienstcombinaties van identiteitskaart en [!DNL Experience Cloud] oplossingscombinaties.

<!--
mcvid-test-verify.xml
-->

## Voordat u {#section-b1e76ad552ed4eb793b6e521a55127d4} begint

Belangrijke informatie die u moet weten voordat u de id-service gaat testen en controleren.

**Browseromgevingen**

Wanneer het testen in een normale browser zitting, ontruim uw browser geheim voorgeheugen vóór elke test.

U kunt de id-service ook testen in een anonieme of incognito-browsersessie. In een anonieme zitting, te hoeven u niet om uw browser koekjes of geheime voorgeheugen vóór elke test te ontruimen.

**Tools**

Met [Adobe debugger](https://docs.adobe.com/content/help/en/analytics/implementation/validate/debugger.html) en [Charles HTTP proxy](https://www.charlesproxy.com/) kunt u bepalen of de id-service is geconfigureerd om correct te werken met Analytics. De informatie in deze sectie die op de resultaten wordt gebaseerd die door debugger van de Adobe en Charles zijn teruggekeerd. Nochtans, zou u zich vrij moeten voelen om welk hulpmiddel of debugger het beste voor u te gebruiken.

## Testen met Adobe-foutopsporing {#section-861365abc24b498e925b3837ea81d469}

Uw de dienstintegratie wordt gevormd behoorlijk wanneer u [!DNL Experience Cloud ID] (MID) in [!DNL Adobe] debugger reactie ziet. Zie [Cookies en de Dienst van de Identiteit van de Experience Cloud](../introduction/cookies.md) voor meer informatie over MID.

De status van de id-service controleren met [!DNL Adobe] [foutopsporing](https://docs.adobe.com/content/help/en/analytics/implementation/validate/debugger.html):

1. Wis uw browsercookies of open een anonieme bladersessie.
1. Laad de testpagina die de de dienstcode van identiteitskaart bevat.
1. Open [!DNL Adobe] debugger.
1. Controleer de resultaten voor een MID.

## Resultaten van Adobe-foutopsporing {#section-bd2caa6643d54d41a476d747b41e7e25}

MID wordt opgeslagen in een zeer belangrijk-waardepaar dat deze syntaxis gebruikt: `MID= *`Experience Cloud-id`*`. De debugger toont deze informatie zoals hieronder getoond.

**Succes**

De id-service is correct geïmplementeerd als u een reactie ziet die er als volgt uitziet:

```
mid=20265673158980419722735089753036633573
```

Als u een [!DNL Analytics] klant bent, kunt u een [!DNL Analytics] identiteitskaart (HULP) naast MID zien. Dit gebeurt:

* Met sommige van uw vroege/lange-tijdbezoekers van de plaats.
* Als u een respijtperiode hebt ingeschakeld.

**Mislukt**

Neem contact op met de [klantenservice](https://helpx.adobe.com/marketing-cloud/contact-support.html) als de foutopsporing:

* Retourneert geen MID.
* Keert een foutenmelding terug die erop wijst dat uw partneridentiteitskaart niet provisioned is.

## Testen met de proxy {#section-d9e91f24984146b2b527fe059d7c9355} van Charles HTTP

Om de status van de dienst van identiteitskaart met Charles te verifiëren:

1. Wis uw browsercookies of open een anonieme bladersessie.
1. Start Charles.
1. Laad de testpagina die de de dienstcode van identiteitskaart bevat.
1. Controleer de hieronder beschreven verzoek- en antwoordaanroepen en gegevens.

## De resultaten van Charles begrijpen {#section-c10c3dc0bb9945cbaffcf6fec7082fab}

Verwijs naar deze sectie voor informatie over waar te kijken, en wat te zoeken, wanneer u Charles gebruikt om de vraag van HTTP te controleren.

### Aanvragen voor ID-service met succes in Charles

De code van uw id-service werkt correct wanneer de functie `Visitor.getInstance` een JavaScript-aanroep uitvoert naar `dpm.demdex.net`. Een succesvol verzoek omvat uw [Organisatie-id](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26). De organisatie-id wordt doorgegeven als sleutelwaardepaar dat deze syntaxis gebruikt: `d_orgid= *`organisatie-id`*`. Zoek naar `dpm.demdex.net` en de vraag JavaScript onder [!UICONTROL Structure] tabel. Zoek uw organisatie-id op het tabblad [!UICONTROL Request].

![](assets/charles_request.png)

### Reacties met geslaagde id-service in Charles

Uw account is correct ingericht voor de id-service wanneer de reactie van de [Gegevensverzamelingsservers](https://docs.adobe.com/content/help/en/audience-manager/user-guide/reference/system-components/components-data-collection.html) (DCS) een MID retourneert. MID is geretourneerd als sleutelwaardepaar dat deze syntaxis gebruikt: `d_mid: visitor Experience Cloud ID`. Zoek naar MID op het [!UICONTROL Response] lusje zoals hieronder getoond.

![](assets/charles_response_success.png)

### Reacties van id-service in Charles zijn mislukt

Uw account is niet correct ingericht als de id ontbreekt in het DCS-antwoord. Een mislukte reactie retourneert een foutcode en een foutbericht op het tabblad [!UICONTROL Response], zoals hieronder wordt weergegeven. Neem contact op met de klantenservice als dit foutbericht wordt weergegeven in het DCS-antwoord.

![](assets/charles_response_unsuccessful.png)

Zie [DCS-foutcodes, -berichten en -voorbeelden](https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-error-codes.html) voor meer informatie over foutcodes.

>[!MORELIKETHIS]
>
>* [Web-eigenschappen](https://docs.adobe.com/content/help/en/dtm/using/admin/web-property.html)

