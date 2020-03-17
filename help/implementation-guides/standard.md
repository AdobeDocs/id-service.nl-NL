---
description: Oudere implementaties gebruiken Dynamic Tag Management (DTM) om de Experience Cloud Identity Service in te stellen, te implementeren en te integreren met uw andere Experience Cloud-oplossingen.
keywords: ID Service
seo-description: Oudere implementaties gebruiken Dynamic Tag Management (DTM) om de Experience Cloud Identity Service in te stellen, te implementeren en te integreren met uw andere Experience Cloud-oplossingen.
seo-title: Implementatie met dynamisch tagbeheer
title: Implementatie met dynamisch tagbeheer
uuid: c4f752c4-392e-4909-b178-911706857064
translation-type: tm+mt
source-git-commit: c4c0b791230422f17292b72fd45ba5689a60adae

---


# Implementatie met dynamisch tagbeheer {#implementation-with-dynamic-tag-management}

Oudere implementaties gebruiken Dynamic Tag Management (DTM) om de Experience Cloud Identity Service in te stellen, te implementeren en te integreren met uw andere Experience Cloud-oplossingen.

## Implementatie met dynamisch tagbeheer {#topic-6f4ed5d96977406ca991e50f3fbd5b01}

Oudere implementaties gebruiken Dynamic Tag Management (DTM) om de Experience Cloud Identity Service in te stellen, te implementeren en te integreren met uw andere Experience Cloud-oplossingen.

>[!NOTE]
>
>Momenteel is [Adobe Experience Platform Launch](https://docs.adobelaunch.com/) het aanbevolen implementatieprogramma, omdat het complexe taken voor tagbeheer vereenvoudigt en codeplaatsing automatiseert die verder gaat dan de mogelijkheden van DTM. Zie [Implementeren met starten](../implementation-guides/ecid-implement-with-launch.md).

## Dynamisch tagbeheer en de id-service {#section-4a4c4fac5d0a4cbbaff8e1833f73657c}

[Met Dynamic Tag Management](https://marketing.adobe.com/resources/help/en_US/dtm/) kunt u uw ID-serviceversie en de bijbehorende integratie van [!DNL Experience Cloud] oplossingen configureren, implementeren en beheren. DTM helpt het implementatieproces te vereenvoudigen, omdat het nauw is geïntegreerd met de id-service en andere Experience Cloud-oplossingen. U hoeft alleen het gereedschap Experience Cloud ID toe te voegen en te configureren en informatie op te geven, zoals:

* Experience Cloud Organization ID (automatisch ingevuld als deze gekoppeld is aan de Experience Cloud)
* Analytics tracking-server (beveiligd en niet beveiligd)
* Experience Cloud-server (voor &#39;first-party tracking&#39;-servers)

DTM is gratis beschikbaar voor elke [!DNL Experience Cloud] klant.

**Aan de slag met DTM**

DTM is een eenvoudig maar krachtig hulpmiddel. Als u het nog niet gebruikt, raden we u aan dit te doen. Raadpleeg de DTM- [documentatie](https://marketing.adobe.com/resources/help/en_US/dtm/c_overview.html) en video&#39;s [over het starten van de](https://marketing.adobe.com/resources/help/en_US/dtm/jump-start-videos.html) DTM-sneltoets om aan de slag te gaan met deze service. Zie de informatie en procedures in de volgende secties voor instructies over het instellen van de id-service met DTM.

## Richtlijnen voor implementatie {#concept-54a2ec49af8f4bfca9207b1d404e8e1a}

Controleer deze vereisten en procedures voordat u probeert de Experience Cloud Identity Service met Dynamic Tag Management (DTM) te implementeren.

<!--
mcvid-dtm-deployment.xml
-->

**Je account verstrekken**

Voordat u aan de slag kunt, moet u ervoor zorgen dat uw organisatie en oplossingen zijn ingericht voor de toepassing [!DNL Experience Cloud] en dat u bekend bent met [!DNL Dyanamic Tag Management]. Aan de slag met deze documentatie:

* [Laat uw oplossingen voor de kerndiensten](https://marketing.adobe.com/resources/help/en_US/mcloud/core_services.html)toe: Implementeer de Experience Cloud en word beheerder. Dit proces moderniseert uw oplossingen voor de kerndiensten zoals klantenattributen en Ervaar Cloud publiek.
* [Aan de slag met dynamisch tagbeheer](https://marketing.adobe.com/resources/help/en_US/dtm/get_started.html)
* [Video&#39;s](https://marketing.adobe.com/resources/help/en_US/dtm/jump-start-videos.html)met snelstartpagina&#39;s: Een reeks korte video&#39;s die aantonen hoe u elementaire DTM-taken kunt uitvoeren.

**Plaatsing van ID-servicecode en laadvolgorde**

De dienst van identiteitskaart werkt door om een unieke identiteitskaart van de servers van de [!DNL Adobe] gegevensinzameling te verzoeken en te ontvangen. De code van uw id-service werkt alleen correct als:

* Het eerste codeblok dat op de pagina wordt uitgevoerd. [!DNL Adobe]
* Geplaatst zo hoog mogelijk op de pagina, gewoonlijk binnen het `<head>` codeblok.

Zolang u al uw [!DNL Adobe] oplossingen en codebibliotheken in DTM handhaaft, zal het ervoor zorgen dat uw de dienstcode van identiteitskaart in de juiste plaats wordt geplaatst en op het juiste tijdstip in brand steekt.

**regionale gegevensverzameling valideren**

Klanten moeten een CNAME of een gebruik `*.sc.omtrdc` voor [regionale gegevensverzameling](https://marketing.adobe.com/resources/help/en_US/whitepapers/rdc/) (RDC) verstrekken. Verkrijg de specifieke, RDC montages van uw [!DNL Adobe] consultant.

**Analytische rapportsuites configureren**

Nieuwe [!DNL Analytics] klanten moeten een rapportsuite [voor gegevensverzameling](https://marketing.adobe.com/resources/help/en_US/reference/new_report_suite.html) maken.

## Implementeer de Experience Cloud Identity Service met DTM {#task-a659cf19dea84ad48edabe0b72ef9f5c}

Voer de volgende stappen uit om de id-service te implementeren met Dynamic Tag Management (DTM).

**Vereisten**

* Laat uw oplossingen voor het toe [!DNL Experience Cloud] en verifieer dat u beheerdertoestemmingen hebt. Zie [Uw oplossingen voor de kernservices](https://marketing.adobe.com/resources/help/en_US/mcloud/core_services.html)inschakelen.

* Maak een webeigenschap in DTM. Zie de DTM [Create a Web Property](https://marketing.adobe.com/resources/help/en_US/dtm/web_property.html) documentatie of de [Admin Jump Start video](https://marketing.adobe.com/resources/help/en_US/dtm/admin-jump-start.html).

<!--
mcvid-dtm-implement.xml
-->

**Implementatiestappen** Om de id-service met DTM te implementeren:

1. Klik in de DTM [!UICONTROL Dashboard]op de webeigenschap waarmee u wilt werken.
1. Klik op het **[!UICONTROL Overview]** tabblad van de geselecteerde webeigenschap **[!UICONTROL Add a Tool]**.
1. Klik in de **[!UICONTROL Tool Type]** lijst op **[!UICONTROL Experience Cloud Identity Service]**.

   >[!NOTE]
   >
   >Deze actie vult het **[!UICONTROL Experience Cloud Organization ID]** vakje met uw identiteitskaart van de Organisatie. Als uw DTM-account niet aan de account is gekoppeld, moet u deze id opgeven. [!DNL Experience Cloud] Als u uw account wilt koppelen, raadpleegt u [Accounts koppelen in de Experience Cloud](https://marketing.adobe.com/resources/help/en_US/mcloud/organizations.html). Zie de [vereisten](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26) voor informatie over hoe te om uw identiteitskaart van de Organisatie te vinden.

1. Typ in het **[!UICONTROL Tracking Server]** vak de naam van de trackingserver. Als u niet zeker bent hoe te om uw het volgen server te vinden [FAQ](../faq-intro/faq.md) zien en [Correct bevolken trackingServer en trackingServerSecure variabelen](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).
1. Klik **[!UICONTROL Create Tool]** en **[!UICONTROL Save Changes]**.

   Na het opslaan wordt de id-service ingesteld als een hulpprogramma in DTM. Het is echter nog niet gebruiksklaar. Uw DTM-tool moet nog steeds het publicatie-/goedkeuringsproces van DTM doorlopen en u kunt aanvullende parameters configureren. Voor informatie over het DTM goedkeuringsproces, zie de video van het Begin [van de Grondbeginselen van de](https://marketing.adobe.com/resources/help/en_US/dtm/user-basics-jump-start.html) Gebruiker. Zie [Experience Cloud Identity Service Settings voor DTM voor meer informatie over de extra parameters die u kunt toevoegen aan DTM](../implementation-guides/standard.md#concept-fb6cb6a0e6cc4f10b92371f8671f6b59).

## Ervaar de instellingen van de cloudidentiteitsservice voor DTM {#concept-fb6cb6a0e6cc4f10b92371f8671f6b59}

Beschrijft de [!UICONTROL Organization ID], [!UICONTROL General] en de [!UICONTROL Customer Settings] gebieden en hoe zij door de dienst van [!DNL Experience Cloud] identiteitskaart worden gebruikt.

<!--
mcvid-dtm-settings.xml
-->

## Hoe vind ik deze instellingen? {#section-c5b2d1c928944ae2b8565c1b182fe575}

De instellingen zijn beschikbaar nadat u de id-service hebt toegevoegd en opgeslagen als een programma in Dynamic Tag Management (DTM). U kunt deze montages ook toegang hebben door het tandwielpictogram van de [!UICONTROL Installed Tools] sectie van uw DTM Webbezit te klikken.

![](assets/installedTools.png)

## Organisatie-id {#section-949b5a0d8af940558b04ff675cf53f77}

Dit is de id die wordt vereist door en is gekoppeld aan uw [!DNL Experience Cloud] bedrijf waarvoor u een provisioning uitvoert. Een organisatie is de entiteit die een beheerder toelaat om gebruikers, groepen, en controle enige sign-on toegang in [!DNL Experience Cloud]te vormen. De organisatie-id is een alfanumerieke tekenreeks van 24 tekens, gevolgd door (en moet bevatten) @AdobeOrg. [!DNL Experience Cloud] beheerders kunnen deze id vinden in [Experience Cloud > Tools](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html).

![](assets/orgID.png)

Zie ook [Cookies en de Experience Cloud Identity Service](../introduction/cookies.md).

## Algemene instellingen {#section-071d358e40f84629a8901b893dd61392}

Met deze instellingen kunt u trackingservers, codeversies en andere variabelen opgeven.

![](assets/generalSettings.png)

In de volgende tabel worden de [!UICONTROL General] instellingen weergegeven en gedefinieerd.

**Visitor-id automatisch aanvragen**

Als u Dynamisch tagbeheer inschakelt, wordt de `getMarketingCloudVisitorID()` methode automatisch aangeroepen voordat een van de Adobe-oplossingen wordt geladen die gebruikmaken van de Experience Cloud Identity Service.

Zie [getMarketingCloudVisitorID](../library/get-set/getmcvid.md).

**Analytics Tracking Server**

De naam van de volgende server die voor de gegevensinzameling van Analytics wordt gebruikt. Dit is het domein waarop de afbeeldingsaanvraag en het cookie worden geschreven (bijvoorbeeld `http://site.omtrdc.net`).

Als u de URL&#39;s van de trackingserver niet kent, controleert u uw `s_code.js` of `AppMeasurement.js` bestanden. U zult URL die door de `s.trackingServer` variabele wordt geplaatst willen.

Zie [trackingServer](https://marketing.adobe.com/resources/help/en_US/sc/implement/trackingServer.html) en bevolk [correct trackingServer en trackingServerSecure variabele](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).

**Beveiliging van trackingserver**

De naam van de veilige die volgserver voor de gegevensinzameling van Analytics wordt gebruikt. Dit is het domein waarop de afbeeldingsaanvraag en het cookie worden geschreven (bijvoorbeeld `https://site.omtrdc.net`).

Als u de URL&#39;s van de trackingserver niet kent, controleert u uw `s_code.js` of `AppMeasurement.js` bestanden. U zult URL die door de `s.trackingServerSecure` variabele wordt geplaatst willen.

Zie [trackingServer](https://marketing.adobe.com/resources/help/en_US/sc/implement/trackingServer.html) en bevolk [correct trackingServer en trackingServerSecure variabele](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).

**Experience Cloud Server**

Als uw bedrijf de inzameling van gegevens van de eerste partij (CNAME) gebruikt om eerderekookies in een derdecontext te gebruiken, ga hier de volgende server (b.v., `http://metrics.company.com`.) in

**Experience Cloud Server Secure**

Als uw bedrijf de inzameling van gegevens van de eerste partij (CNAME) gebruikt om eerderekookies in een derdecontext te gebruiken, ga hier de volgende server (b.v., `https://metrics.company.com`.) in

**Bibliotheekversie**

Hiermee stelt u de versie in van de ID-servicecode-bibliotheek ( `VisitorAPI.js`) die u wilt gebruiken. U kunt deze menuopties niet bewerken.

**Instellingen**

Met deze velden kunt u [functievariabelen](../library/function-vars/function-vars.md) toevoegen als sleutel-waardeparen. Klik **[!UICONTROL Add]** om een of meer variabelen toe te voegen aan de implementatie van de id-service.

![](assets/dtmVars.png)

>[!IMPORTANT]
>
>Stel hier de `cookieDomain` variabele in. Dit is vereist voor domeinen van het bovenste niveau met meerdere delen, waarbij een van de laatste twee delen van de URL uit meer dan twee tekens bestaat. Zie de hierboven verbonden documentatie van de Variabelen van de Configuratie.

## Klantinstellingen {#section-238d1272c1504d148fe38fb0ae5d71c2}

Extra velden waarmee u een integratiecode of een geverifieerde statusstatus kunt toevoegen.

![](assets/customerSettings.png)

**Integratiecode**

Een integratiecode is een unieke, door de klant opgegeven id. De integratiecode moet de waarde bevatten waarin u een gegevensbron [hebt](https://marketing.adobe.com/resources/help/en_US/aam/create-datasource.html) gemaakt [!DNL Audience Manager].

**Waarde**

De waarde moet een gegevenselement zijn dat de gebruikers-id bevat. Gegevenselementen zijn geschikte containers voor dynamische waarden, zoals id&#39;s van een client-specifiek intern systeem.

**Deelstaat Auth**

Opties die bezoekers definiëren of identificeren op basis van hun verificatiestatus (bijvoorbeeld aangemeld, afgemeld). See [Customer IDs and Authentication States](../reference/authenticated-state.md).

## De Experience Cloud Identity Service testen en verifiëren {#concept-644fdbef433b46ba9c0634ac95eaa680}

Deze instructies, hulpmiddelen, en procedures helpen u bepalen als de dienst van identiteitskaart behoorlijk werkt. Deze tests zijn van toepassing op de dienst van identiteitskaart in het algemeen en voor verschillende de dienst en [!DNL Experience Cloud] oplossingscombinaties van identiteitskaart

<!--
mcvid-test-verify.xml
-->

## Voordat u begint {#section-b1e76ad552ed4eb793b6e521a55127d4}

Belangrijke informatie die u moet weten voordat u de id-service gaat testen en controleren.

**Browseromgevingen**

Wanneer het testen in een normale browser zitting, ontruim uw browser geheim voorgeheugen vóór elke test.

U kunt de id-service ook testen in een anonieme of incognito-browsersessie. In een anonieme zitting, te hoeven u niet om uw browser koekjes of geheime voorgeheugen vóór elke test te ontruimen.

**Gereedschappen**

De foutopsporing [van](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html) Adobe en de proxy [van](https://www.charlesproxy.com/) Charles HTTP kunnen u helpen bepalen als de dienst van identiteitskaart is gevormd om behoorlijk met Analytics te werken. De informatie in deze sectie is gebaseerd op de resultaten die zijn geretourneerd door Adobe Debugger en Charles. Nochtans, zou u zich vrij moeten voelen om welk hulpmiddel of debugger het beste voor u te gebruiken.

## Testen met Adobe Debugger {#section-861365abc24b498e925b3837ea81d469}

Uw de dienstintegratie wordt gevormd behoorlijk wanneer u een [!DNL Experience Cloud ID] (MID) in de [!DNL Adobe] debugger reactie ziet. Raadpleeg [Cookies en de Experience Cloud Identity Service](../introduction/cookies.md) voor meer informatie over de MID.

Om de status van de dienst van identiteitskaart met [!DNL Adobe] debugger [](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html)te verifiëren:

1. Wis uw browsercookies of open een anonieme bladersessie.
1. Laad de testpagina die de de dienstcode van identiteitskaart bevat.
1. Open het [!DNL Adobe] foutopsporingsprogramma.
1. Controleer de resultaten voor een MID.

## De resultaten van Adobe Debugger {#section-bd2caa6643d54d41a476d747b41e7e25}

MID wordt opgeslagen in een zeer belangrijk-waardepaar dat deze syntaxis gebruikt: Cloud-id `MID= *``*`beleven. De debugger toont deze informatie zoals hieronder getoond.

**Succes**

De id-service is correct geïmplementeerd als u een reactie ziet die er als volgt uitziet:

```
mid=20265673158980419722735089753036633573
```

Als je een [!DNL Analytics] klant bent, zie je mogelijk een [!DNL Analytics] ID (AID) naast de MID. Dit gebeurt:

* Met sommige van uw vroege/lange-tijdbezoekers van de plaats.
* Als u een respijtperiode hebt ingeschakeld.

**Mislukt**

Neem contact op met de [klantenservice](https://helpx.adobe.com/marketing-cloud/contact-support.html) als de foutopsporing:

* Retourneert geen MID.
* Keert een foutenmelding terug die erop wijst dat uw partneridentiteitskaart niet provisioned is.

## Testen met de proxy Charles HTTP {#section-d9e91f24984146b2b527fe059d7c9355}

Om de status van de dienst van identiteitskaart met Charles te verifiëren:

1. Wis uw browsercookies of open een anonieme bladersessie.
1. Start Charles.
1. Laad de testpagina die de de dienstcode van identiteitskaart bevat.
1. Controleer de hieronder beschreven verzoek- en antwoordaanroepen en gegevens.

## De resultaten van Charles begrijpen {#section-c10c3dc0bb9945cbaffcf6fec7082fab}

Verwijs naar deze sectie voor informatie over waar te kijken, en wat te zoeken, wanneer u Charles gebruikt om de vraag van HTTP te controleren.

### Aanvragen voor ID-service met succes in Charles

De code van uw id-service werkt goed wanneer de `Visitor.getInstance` functie een JavaScript-aanroep uitvoert naar `dpm.demdex.net`. Een succesvol verzoek bevat uw [organisatie-id](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26). De organisatie-id wordt doorgegeven als sleutelwaardepaar dat deze syntaxis gebruikt: `d_orgid= *`organisatie-id`*`. Zoek de JavaScript- `dpm.demdex.net` en JavaScript-aanroepen onder het [!UICONTROL Structure] tabblad. Zoek uw organisatie-id onder het [!UICONTROL Request] tabblad.

![](assets/charles_request.png)

### Reacties met geslaagde id-service in Charles

Uw account is correct ingericht voor de id-service wanneer de reactie van de [gegevensverzamelingsservers](https://marketing.adobe.com/resources/help/en_US/aam/c_compcollect.html) (DCS) een MID retourneert. MID is geretourneerd als sleutelwaardepaar dat deze syntaxis gebruikt: `d_mid: visitor Experience Cloud ID`. Zoek naar MID in het [!UICONTROL Response] lusje zoals hieronder getoond.

![](assets/charles_response_success.png)

### Reacties van id-service in Charles zijn mislukt

Uw account is niet correct ingericht als de id ontbreekt in het DCS-antwoord. Een mislukte reactie retourneert een foutcode en een foutbericht op het [!UICONTROL Response] tabblad, zoals hieronder wordt weergegeven. Neem contact op met de klantenservice als dit foutbericht wordt weergegeven in het DCS-antwoord.

![](assets/charles_response_unsuccessful.png)

Zie [DCS-foutcodes, berichten en voorbeelden](https://marketing.adobe.com/resources/help/en_US/aam/dcs_error_codes.html)voor meer informatie over foutcodes.

>[!MORELIKETHIS]
>
>* [Web-eigenschappen](https://marketing.adobe.com/resources/help/en_US/dtm/web_property.html)

