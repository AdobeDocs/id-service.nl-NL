---
description: Deze instructies, hulpmiddelen, en procedures helpen u bepalen als de dienst van identiteitskaart behoorlijk werkt. Deze tests zijn van toepassing op de dienst van identiteitskaart in het algemeen en voor verschillende de dienst en van de Ervaring Cloud oplossingscombinaties van identiteitskaart
keywords: ID Service
seo-description: Deze instructies, hulpmiddelen, en procedures helpen u bepalen als de dienst van identiteitskaart behoorlijk werkt. Deze tests zijn van toepassing op de dienst van identiteitskaart in het algemeen en voor verschillende de dienst en van de Ervaring Cloud oplossingscombinaties van identiteitskaart
seo-title: De Experience Cloud Identity Service testen en verifiëren
title: De Experience Cloud Identity Service testen en verifiëren
uuid: 442de9c3-c265-4412-89bd-aeaa286ddad6
translation-type: tm+mt
source-git-commit: ef3169f8928f337d4f2d17922b44a7421d225e51

---


# De Experience Cloud Identity Service testen en verifiëren{#test-and-verify-the-experience-cloud-id-service}

Deze instructies, hulpmiddelen, en procedures helpen u bepalen als de dienst van identiteitskaart behoorlijk werkt. Deze tests zijn van toepassing op de dienst van identiteitskaart in het algemeen en voor verschillende de dienst en van de Ervaring Cloud oplossingscombinaties van identiteitskaart

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

**Aanvragen voor ID-service met succes in Charles**

De code van uw id-service werkt goed wanneer de `Visitor.getInstance` functie een JavaScript-aanroep uitvoert naar `dpm.demdex.net`. Een succesvol verzoek bevat uw [organisatie-id](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26). De organisatie-id wordt doorgegeven als sleutelwaardepaar dat deze syntaxis gebruikt: `d_orgid= *`organisatie-id`*`. Zoek de JavaScript- `dpm.demdex.net` en JavaScript-aanroepen onder het [!UICONTROL Structure] tabblad. Zoek uw organisatie-id onder het [!UICONTROL Request] tabblad.

![](assets/charles_request.png)

**Reacties met geslaagde id-service in Charles**

Uw account is correct ingericht voor de id-service wanneer de reactie van de [gegevensverzamelingsservers](https://marketing.adobe.com/resources/help/en_US/aam/c_compcollect.html) (DCS) een MID retourneert. MID is geretourneerd als sleutelwaardepaar dat deze syntaxis gebruikt: De `d_mid: *`bezoeker erservaring Cloud ID`*`. Zoek naar MID in het [!UICONTROL Response] lusje zoals hieronder getoond.

![](assets/charles_response_success.png)

**Reacties van id-service in Charles zijn mislukt**

Uw account is niet correct ingericht als de id ontbreekt in het DCS-antwoord. Een mislukte reactie retourneert een foutcode en een foutbericht op het [!UICONTROL Response] tabblad, zoals hieronder wordt weergegeven. Neem contact op met de klantenservice als dit foutbericht wordt weergegeven in het DCS-antwoord.

![](assets/charles_response_unsuccessful.png)

Zie [DCS-foutcodes, berichten en voorbeelden](https://marketing.adobe.com/resources/help/en_US/aam/dcs_error_codes.html)voor meer informatie over foutcodes.
