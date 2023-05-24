---
description: Oudere implementaties gebruiken Dynamic Tag Management (DTM) om de Experience Cloud Identity Service in te stellen, te implementeren en te integreren met uw andere Experience Cloud-oplossingen.
keywords: ID-service
title: Implementatie met Dynamic Tag Management
exl-id: 37ccc919-3015-42fa-a88f-639cdf726f48
source-git-commit: e171c94ccfa1f4fe9b8d909d0204adb94f20cbb6
workflow-type: tm+mt
source-wordcount: '1974'
ht-degree: 0%

---

# Implementatie met Dynamic Tag Management {#implementation-with-dynamic-tag-management}

Oudere implementaties gebruiken Dynamic Tag Management (DTM) om de Experience Cloud Identity Service in te stellen, te implementeren en te integreren met uw andere Experience Cloud-oplossingen.

## Implementatie met Dynamic Tag Management {#topic-6f4ed5d96977406ca991e50f3fbd5b01}

Oudere implementaties gebruiken Dynamic Tag Management (DTM) om de Experience Cloud Identity Service in te stellen, te implementeren en te integreren met uw andere Experience Cloud-oplossingen.

>[!NOTE]
>
>Momenteel [Adobe Experience Platform Launch](https://experienceleague.adobe.com/docs/launch/using/home.html) is het voorkeursprogramma en het aanbevolen implementatieprogramma omdat dit complexe taken voor tagbeheer vereenvoudigt en code-plaatsing automatiseert die verder gaat dan de mogelijkheden van DTM. Zie [Implementeren met starten](../implementation-guides/ecid-implement-with-launch.md).

## Dynamic Tag Management en de ID-service {#section-4a4c4fac5d0a4cbbaff8e1833f73657c}

[Dynamische Tag Management](https://experienceleague.adobe.com/docs/dtm/using/dtm-home.html) laat u vormen, opstellen en beheren uw de dienstinstantie van identiteitskaart en verwant [!DNL Experience Cloud] integratie van oplossingen. DTM helpt het implementatieproces te vereenvoudigen, omdat het volledig is geïntegreerd met de id-service en andere Experience Cloud-oplossingen. U hoeft alleen het gereedschap Experience Cloud-id toe te voegen en te configureren en informatie op te geven, zoals:

* Organisatie-id Experience Cloud (automatisch ingevuld als deze is gekoppeld aan de Experience Cloud)
* Analytics tracking-server (beveiligd en niet beveiligd)
* Experience Cloud-server (voor &#39;first-party tracking&#39;-servers)

DTM is gratis beschikbaar voor alle [!DNL Experience Cloud] klant.

**Aan de slag met DTM**

DTM is een eenvoudig maar krachtig hulpmiddel. Als u het nog niet gebruikt, raden we u aan dit te doen. Zie de [DTM-documentatie](https://experienceleague.adobe.com/docs/dtm/using/c-overview.html) om aan de slag te gaan met deze service. Zie de informatie en procedures in de volgende secties voor instructies over het instellen van de id-service met DTM.

## Richtlijnen voor implementatie {#concept-54a2ec49af8f4bfca9207b1d404e8e1a}

Controleer deze vereisten en procedures voordat u probeert de Experience Cloud Identity Service met Dynamic Tag Management (DTM) te implementeren.

<!--
mcvid-dtm-deployment.xml
-->

**Je account verstrekken**

Voordat u aan de slag kunt, moet u ervoor zorgen dat uw organisatie en oplossingen zijn ingericht voor de [!DNL Experience Cloud] en je bent vertrouwd met [!DNL Dyanamic Tag Management]. Aan de slag met deze documentatie:

* [Laat uw oplossingen voor de kerndiensten toe](https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html): Voer de Experience Cloud uit en word een beheerder. Dit proces moderniseert uw oplossingen voor de kerndiensten zoals klantenattributen en Experience Cloud publiek.
* [Aan de slag met Dynamic Tag Management](https://experienceleague.adobe.com/docs/dtm/using/getting-started/get-started.html)

**Plaatsing van ID-servicecode en laadvolgorde**

De id-service werkt door een unieke id aan te vragen en te ontvangen van de [!DNL Adobe] servers voor gegevensverzameling. De code van uw id-service werkt alleen correct als:

* Het eerste blok van [!DNL Adobe] code die op de pagina wordt uitgevoerd.
* Zo hoog mogelijk op de pagina geplaatst, gewoonlijk binnen `<head>` codeblok.

Zolang u al uw [!DNL Adobe] oplossingen en codebibliotheken in DTM, zal het ervoor zorgen dat uw de dienstcode van identiteitskaart op de juiste plaats wordt geplaatst en op het juiste ogenblik brandt.

**regionale gegevensverzameling valideren**

Klanten moeten een CNAME of een gebruik opgeven `*.sc.omtrdc` for [regionale gegevensverzameling](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html) (RDC). Verkrijg de specifieke, RDC montages van uw [!DNL Adobe] consultant.

**Analytische rapportsuites configureren**

Nieuw [!DNL Analytics] klanten moeten [een rapportsuite maken](https://experienceleague.adobe.com/docs/analytics/admin/manage-report-suites/new-report-suite/new-report-suite.html) voor gegevensverzameling.

## Implementeer de Experience Cloud Identity Service met DTM {#task-a659cf19dea84ad48edabe0b72ef9f5c}

Voer de volgende stappen uit om de id-service te implementeren met Dynamic Tag Management (DTM).

**Vereisten**

* Laat uw oplossingen voor de [!DNL Experience Cloud] en controleer of u beheerdersmachtigingen hebt. Zie [Laat uw oplossingen voor de kerndiensten toe](https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html).

* Maak een webeigenschap in DTM. Zie de DTM [Een webeigenschap maken](https://experienceleague.adobe.com/docs/dtm/using/admin/web-property.html) documentatie.

<!--
mcvid-dtm-implement.xml
-->

**Uitvoeringsstappen** De id-service implementeren met DTM:

1. In de DTM [!UICONTROL Dashboard], klikt u op de webeigenschap waarmee u wilt werken.
1. In de **[!UICONTROL Overview]** tabblad van de geselecteerde webeigenschap, klikt u op **[!UICONTROL Add a Tool]**.
1. In de **[!UICONTROL Tool Type]** lijst, klikt u op **[!UICONTROL Experience Cloud Identity Service]**.

   >[!NOTE]
   >
   >Deze handeling vult de **[!UICONTROL Experience Cloud Organization ID]** met uw organisatie-id. Als uw DTM-account niet is gekoppeld aan de [!DNL Experience Cloud], moet je deze id opgeven. Als u uw account wilt koppelen, raadpleegt u [Accounts koppelen in de Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html). Zie de [vereisten](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26) voor informatie over hoe u uw organisatie-id kunt vinden.

1. Typ de naam van de volgende server in het dialoogvenster **[!UICONTROL Tracking Server]** doos. Als u niet zeker bent hoe te om uw het volgen server te vinden zie [Veelgestelde vragen](../faq-intro/faq.md) en [De variabelen trackingServer en trackingServerSecure correct vullen](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).
1. Klikken **[!UICONTROL Create Tool]** en **[!UICONTROL Save Changes]**.

   Na het opslaan wordt de id-service ingesteld als een hulpprogramma in DTM. Het is echter nog niet gebruiksklaar. Uw DTM-tool moet nog steeds het publicatie-/goedkeuringsproces van DTM doorlopen en u kunt aanvullende parameters configureren. Voor informatie over de extra parameters kunt u aan DTM toevoegen, zie [Experience Cloud Identity Service Settings voor DTM](../implementation-guides/standard.md#concept-fb6cb6a0e6cc4f10b92371f8671f6b59).

## Experience Cloud Identity Service Settings voor DTM {#concept-fb6cb6a0e6cc4f10b92371f8671f6b59}

Beschrijft de [!UICONTROL Organization ID], [!UICONTROL General] en [!UICONTROL Customer Settings] velden en hoe deze worden gebruikt door de [!DNL Experience Cloud] ID-service.

<!--
mcvid-dtm-settings.xml
-->

## Hoe vind ik deze instellingen? {#section-c5b2d1c928944ae2b8565c1b182fe575}

De instellingen zijn beschikbaar nadat u de id-service hebt toegevoegd en opgeslagen als een programma in Dynamic Tag Management (DTM). U kunt deze instellingen ook openen door op het tandwielpictogram te klikken in het dialoogvenster [!UICONTROL Installed Tools] van uw DTM-webeigenschap.

![](assets/installedTools.png)

## Organisatie-ID {#section-949b5a0d8af940558b04ff675cf53f77}

Dit is de id die vereist is voor en gekoppeld is aan uw provisioning [!DNL Experience Cloud] bedrijf. Een organisatie is de entiteit die een beheerder toelaat om gebruikers, groepen, en controle enige sign-on toegang in te vormen [!DNL Experience Cloud]. De organisatie-id is een alfanumerieke tekenreeks van 24 tekens, gevolgd door (en moet bevatten) @AdobeOrg. [!DNL Experience Cloud] beheerders kunnen deze id vinden in [Experience Cloud > Gereedschappen](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html).

![](assets/orgID.png)

Zie ook [Cookies en de Experience Cloud Identity Service](../introduction/cookies.md).

## Algemene instellingen {#section-071d358e40f84629a8901b893dd61392}

Met deze instellingen kunt u trackingservers, codeversies en andere variabelen opgeven.

![](assets/generalSettings.png)

In de volgende tabel worden de [!UICONTROL General] instellingen.

**Visitor-id automatisch aanvragen**

Als deze optie is ingeschakeld, roept Dynamic Tag Management automatisch het `getMarketingCloudVisitorID()` vóór het laden van de Adobe-oplossingen die gebruikmaken van de Experience Cloud Identity Service.

Zie [getMarketingCloudVisitorID](../library/get-set/getmcvid.md).

**Analytics Tracking Server**

De naam van de volgende server die voor de gegevensinzameling van Analytics wordt gebruikt. Dit is het domein waarop de afbeeldingsaanvraag en het cookie worden geschreven (bijvoorbeeld `http://site.omtrdc.net`).

Als u de URL&#39;s van de trackingserver niet kent, controleert u `s_code.js` of `AppMeasurement.js` bestanden. U wilt de URL instellen door de `s.trackingServer` variabele.

Zie [trackingServer](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/page-variables.html) en [De variabele trackingServer en trackingServerSecure correct vullen](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).

**Beveiliging van trackingserver**

De naam van de veilige die volgserver voor de gegevensinzameling van Analytics wordt gebruikt. Dit is het domein waarop de afbeeldingsaanvraag en het cookie worden geschreven (bijvoorbeeld `https://site.omtrdc.net`).

Als u de URL&#39;s van de trackingserver niet kent, controleert u `s_code.js` of `AppMeasurement.js` bestanden. U wilt de URL instellen door de `s.trackingServerSecure` variabele.

Zie [trackingServer](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/page-variables.html) en [De variabele trackingServer en trackingServerSecure correct vullen](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).

**Experience Cloud-server**

Als uw bedrijf de inzameling van gegevens van de eerste partij (CNAME) gebruikt om eerderekookies in een derdecontext te gebruiken, ga hier de volgende server (b.v. in, `http://metrics.company.com`.)

**Experience Cloud Server beveiligd**

Als uw bedrijf de inzameling van gegevens van de eerste partij (CNAME) gebruikt om eerderekookies in een derdecontext te gebruiken, ga hier de volgende server (b.v. in, `https://metrics.company.com`.)

**Bibliotheekversie**

Hiermee wordt de versie van de ID-servicecode-bibliotheek ingesteld ( `VisitorAPI.js`) die u wilt gebruiken. U kunt deze menuopties niet bewerken.

**Instellingen**

In deze velden kunt u [functievariabelen](../library/function-vars/function-vars.md) als sleutel-waardeparen. Klikken **[!UICONTROL Add]** om een of meer variabelen toe te voegen aan de implementatie van de id-service.

![](assets/dtmVars.png)

>[!IMPORTANT]
>
>Stel de `cookieDomain` hier variabel. Dit is vereist voor domeinen van het bovenste niveau met meerdere delen, waarbij een van de laatste twee delen van de URL uit meer dan twee tekens bestaat. Zie de hierboven verbonden documentatie van de Variabelen van de Configuratie.

## Klantinstellingen {#section-238d1272c1504d148fe38fb0ae5d71c2}

Extra velden waarmee u een integratiecode of een geverifieerde statusstatus kunt toevoegen.

![](assets/customerSettings.png)

**Integratiecode**

Een integratiecode is een unieke, door de klant opgegeven id. De integratiecode moet de waarde bevatten die u hebt gebruikt [een gegevensbron maken](https://experienceleague.adobe.com/docs/audience-manager/user-guide/features/data-sources/manage-datasources.html#create-data-source) in [!DNL Audience Manager].

**Value**

De waarde moet een gegevenselement zijn dat de gebruikers-id bevat. Gegevenselementen zijn geschikte containers voor dynamische waarden, zoals id&#39;s van een client-specifiek intern systeem.

**Deelstaat Auth**

Opties die bezoekers definiëren of identificeren op basis van hun verificatiestatus (bijvoorbeeld aangemeld, afgemeld). Zie [Klant-id&#39;s en verificatiestatus](../reference/authenticated-state.md).

## De Experience Cloud Identity Service testen en verifiëren {#concept-644fdbef433b46ba9c0634ac95eaa680}

Deze instructies, hulpmiddelen, en procedures helpen u bepalen als de dienst van identiteitskaart behoorlijk werkt. Deze tests zijn van toepassing op de dienst van identiteitskaart in het algemeen en voor de verschillende dienst van identiteitskaart en [!DNL Experience Cloud] combinaties van oplossingen.

<!--
mcvid-test-verify.xml
-->

## Voordat u begint {#section-b1e76ad552ed4eb793b6e521a55127d4}

Belangrijke informatie die u moet weten voordat u de id-service gaat testen en controleren.

**Browseromgevingen**

Wanneer het testen in een normale browser zitting, ontruim uw browser geheim voorgeheugen vóór elke test.

U kunt de id-service ook testen in een anonieme of incognito-browsersessie. In een anonieme zitting, te hoeven u niet om uw browser koekjes of geheime voorgeheugen vóór elke test te ontruimen.

**Tools**

De [Adobe debugger](https://experienceleague.adobe.com/docs/analytics/implementation/validate/debugger.html) en de [Charles HTTP-proxy](https://www.charlesproxy.com/) kan u helpen bepalen als de dienst van identiteitskaart is gevormd om behoorlijk met Analytics te werken. De informatie in deze sectie die op de resultaten wordt gebaseerd die door debugger van de Adobe en Charles zijn teruggekeerd. Nochtans, zou u zich vrij moeten voelen om welk hulpmiddel of debugger het beste voor u te gebruiken.

## Testen met Adobe Debugger {#section-861365abc24b498e925b3837ea81d469}

Uw de dienstintegratie wordt gevormd behoorlijk wanneer u ziet [!DNL Experience Cloud ID] (MID) in de [!DNL Adobe] foutopsporingsreactie. Zie [Cookies en de Experience Cloud Identity Service](../introduction/cookies.md) voor meer informatie over de MID.

Om de status van de id-service te verifiëren met de [!DNL Adobe] [foutopsporing](https://experienceleague.adobe.com/docs/analytics/implementation/validate/debugger.html):

1. Wis uw browsercookies of open een anonieme bladersessie.
1. Laad de testpagina die de de dienstcode van identiteitskaart bevat.
1. Open de [!DNL Adobe] foutopsporing.
1. Controleer de resultaten voor een MID.

## Resultaten van Adobe-foutopsporing {#section-bd2caa6643d54d41a476d747b41e7e25}

MID wordt opgeslagen in een zeer belangrijk-waardepaar dat deze syntaxis gebruikt: `MID= *`Experience Cloud-id`*`. De debugger toont deze informatie zoals hieronder getoond.

**Succes**

De id-service is correct geïmplementeerd als u een reactie ziet die er als volgt uitziet:

```
mid=20265673158980419722735089753036633573
```

Als je een [!DNL Analytics] klant, u kunt een [!DNL Analytics] ID (STEUN) naast de MID. Dit gebeurt:

* Met sommige van uw vroege/lange-tijdbezoekers van de plaats.
* Als u een respijtperiode hebt ingeschakeld.

**Mislukt**

Contact [klantenservice](https://helpx.adobe.com/marketing-cloud/contact-support.html) als de foutopsporing:

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

De code van uw id-service werkt correct wanneer de `Visitor.getInstance` functie roept een JavaScript aan `dpm.demdex.net`. Een succesvol verzoek omvat uw [Organisatie-id](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26). De organisatie-id wordt doorgegeven als sleutelwaardepaar dat deze syntaxis gebruikt: `d_orgid= *`organisatie-id`*`. Zoek naar `dpm.demdex.net` en de JavaScript-aanroepen onder de [!UICONTROL Structure] tab. Zoek uw organisatie-id onder de [!UICONTROL Request] tab.

![](assets/charles_request.png)

### Reacties met geslaagde id-service in Charles

Uw account is correct ingericht voor de id-service wanneer de reactie van de [Gegevensverzamelingsservers](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/system-components/components-data-collection.html) (DCS) retourneert een MID. MID is geretourneerd als sleutelwaardepaar dat deze syntaxis gebruikt: `d_mid: visitor Experience Cloud ID`. Zoek naar MID in [!UICONTROL Response] zoals hieronder weergegeven.

![](assets/charles_response_success.png)

### Reacties van id-service in Charles zijn mislukt

Uw account is niet correct ingericht als de id ontbreekt in het DCS-antwoord. Een niet-succesvolle reactie retourneert een foutcode en een foutbericht in het dialoogvenster [!UICONTROL Response] zoals hieronder weergegeven. Neem contact op met de klantenservice als dit foutbericht wordt weergegeven in het DCS-antwoord.

![](assets/charles_response_unsuccessful.png)

Zie voor meer informatie over foutcodes [DCS-foutcodes, berichten en voorbeelden](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-error-codes.html).

>[!MORELIKETHIS]
>
>* [Web-eigenschappen](https://experienceleague.adobe.com/docs/dtm/using/admin/web-property.html)

