---
description: Deze instructies, hulpmiddelen, en procedures helpen u bepalen als de dienst van identiteitskaart behoorlijk werkt. Deze tests zijn van toepassing op de dienst van identiteitskaart in het algemeen en voor verschillende de dienst en van het Experience Cloud oplossingscombinaties van identiteitskaart
keywords: ID-service
title: De identiteitsdienst van het Experience Cloud testen en verifiëren
exl-id: afdf9778-e73d-46ca-9d2f-a65abaae2fe6
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# De identiteitsdienst van het Experience Cloud testen en verifiëren{#test-and-verify-the-experience-cloud-id-service}

Deze instructies, hulpmiddelen, en procedures helpen u bepalen als de dienst van identiteitskaart behoorlijk werkt. Deze tests zijn van toepassing op de dienst van identiteitskaart in het algemeen en voor verschillende de dienst en van het Experience Cloud oplossingscombinaties van identiteitskaart

## Voordat u begint {#section-b1e76ad552ed4eb793b6e521a55127d4}

Belangrijke informatie die u moet weten voordat u de id-service gaat testen en controleren.

**Browser milieu&#39;s**

Wanneer het testen in een normale browser zitting, ontruim uw browser geheim voorgeheugen vóór elke test.

U kunt de id-service ook testen in een anonieme of incognito-browsersessie. In een anonieme zitting, te hoeven u niet om uw browser koekjes of geheime voorgeheugen vóór elke test te ontruimen.

**Hulpmiddelen**

De [ debugger van de Adobe ](https://experienceleague.adobe.com/docs/analytics/implementation/validate/debugger.html) en de [ volmacht van HTTP van Charles ](https://www.charlesproxy.com/) kunnen u helpen bepalen als de dienst van identiteitskaart is gevormd om behoorlijk met Analytics te werken. De informatie in deze sectie die op de resultaten wordt gebaseerd die door debugger van de Adobe en Charles zijn teruggekeerd. Nochtans, zou u zich vrij moeten voelen om welk hulpmiddel of debugger het beste voor u te gebruiken.

## Testen met de Adobe Debugger {#section-861365abc24b498e925b3837ea81d469}

Uw service-integratie is op de juiste wijze geconfigureerd wanneer u een [!DNL Experience Cloud ID] (MID) ziet in de foutopsporingsreactie van [!DNL Adobe] . Zie [ Cookies en de Dienst van de Identiteit van het Experience Cloud ](../introduction/cookies.md) voor meer informatie over MID.

Om het statuut van de dienst van identiteitskaart met [!DNL Adobe] [ debugger ](https://experienceleague.adobe.com/docs/analytics/implementation/validate/debugger.html) te verifiëren:

1. Wis uw browsercookies of open een anonieme bladersessie.
1. Laad de testpagina die de de dienstcode van identiteitskaart bevat.
1. Open het foutopsporingsprogramma van [!DNL Adobe] .
1. Controleer de resultaten voor een MID.

## De resultaten van Adoben Debugger begrijpen {#section-bd2caa6643d54d41a476d747b41e7e25}

MID wordt opgeslagen in een zeer belangrijk-waardepaar dat deze syntaxis gebruikt: `MID= *` identiteitskaart van het Experience Cloud `*`. De debugger toont deze informatie zoals hieronder getoond.

**Succes**

De id-service is correct geïmplementeerd als u een reactie ziet die er als volgt uitziet:

```
mid=20265673158980419722735089753036633573
```

Als u een [!DNL Analytics] -klant bent, ziet u mogelijk een [!DNL Analytics] ID (AID) naast de MID. Dit gebeurt:

* Met sommige van uw vroege/lange-tijdbezoekers van de plaats.
* Als u een respijtperiode hebt ingeschakeld.

**Mislukking**

De klantenzorg van het contact [&#128279;](https://helpx.adobe.com/marketing-cloud/contact-support.html) als debugger:

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

**de Succesvolle verzoeken van de Dienst van identiteitskaart in Karel**

De servicecode van uw id werkt correct wanneer de functie `Visitor.getInstance` een JavaScript-aanroep naar `dpm.demdex.net` uitvoert. Een succesvol verzoek omvat uw [ identiteitskaart van de Organisatie ](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26). Identiteitskaart van de Organisatie wordt overgegaan als zeer belangrijk-waardepaar dat deze syntaxis gebruikt: `d_orgid= *` organisatie identiteitskaart `*`. Zoek naar de aanroepen `dpm.demdex.net` en JavaScript onder het tabblad [!UICONTROL Structure] . Zoek de organisatie-id op het tabblad [!UICONTROL Request] .

![](assets/charles_request.png)

**Succesvolle reacties van de Dienst van identiteitskaart in Karel**

Uw rekening is verstrekt correct voor de dienst van identiteitskaart wanneer de reactie van de [ Servers van de Inzameling van Gegevens ](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/system-components/components-data-collection.html) (DCS) een MID terugkeert. MID is teruggekeerd als zeer belangrijk-waardepaar dat deze syntaxis gebruikt: {identiteitskaart van het Experience Cloud van 0} bezoeker `*`. `d_mid: *` Zoek de id op het tabblad [!UICONTROL Response] (zie hieronder).

![](assets/charles_response_success.png)

**Ontbroken Reacties van de Dienst van identiteitskaart in Karel**

Uw account is niet correct ingericht als de id ontbreekt in het DCS-antwoord. Een mislukte reactie retourneert een foutcode en een foutbericht op het tabblad [!UICONTROL Response] , zoals hieronder wordt weergegeven. Neem contact op met de klantenservice als dit foutbericht wordt weergegeven in het DCS-antwoord.

![](assets/charles_response_unsuccessful.png)

Voor meer informatie over foutencodes, zie [ Codes van de Fout DCS, Berichten, en Voorbeelden ](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-error-codes.html).
