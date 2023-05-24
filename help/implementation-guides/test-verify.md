---
description: Deze instructies, hulpmiddelen, en procedures helpen u bepalen als de dienst van identiteitskaart behoorlijk werkt. Deze tests zijn op de dienst van identiteitskaart in het algemeen en voor verschillende de dienst en oplossingscombinaties van identiteitskaart van toepassing Experience Cloud.
keywords: ID-service
title: De Experience Cloud Identity Service testen en verifiëren
exl-id: afdf9778-e73d-46ca-9d2f-a65abaae2fe6
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---

# De Experience Cloud Identity Service testen en verifiëren{#test-and-verify-the-experience-cloud-id-service}

Deze instructies, hulpmiddelen, en procedures helpen u bepalen als de dienst van identiteitskaart behoorlijk werkt. Deze tests zijn op de dienst van identiteitskaart in het algemeen en voor verschillende de dienst en oplossingscombinaties van identiteitskaart van toepassing Experience Cloud.

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

**Aanvragen voor ID-service met succes in Charles**

De code van uw id-service werkt correct wanneer de `Visitor.getInstance` functie roept een JavaScript aan `dpm.demdex.net`. Een succesvol verzoek omvat uw [Organisatie-id](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26). De organisatie-id wordt doorgegeven als sleutelwaardepaar dat deze syntaxis gebruikt: `d_orgid= *`organisatie-id`*`. Zoek naar `dpm.demdex.net` en de JavaScript-aanroepen onder de [!UICONTROL Structure] tab. Zoek uw organisatie-id onder de [!UICONTROL Request] tab.

![](assets/charles_request.png)

**Reacties met geslaagde id-service in Charles**

Uw account is correct ingericht voor de id-service wanneer de reactie van de [Gegevensverzamelingsservers](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/system-components/components-data-collection.html) (DCS) retourneert een MID. MID is geretourneerd als sleutelwaardepaar dat deze syntaxis gebruikt: `d_mid: *`Experience Cloud-id van bezoeker`*`. Zoek naar MID in [!UICONTROL Response] zoals hieronder weergegeven.

![](assets/charles_response_success.png)

**Reacties van id-service in Charles zijn mislukt**

Uw account is niet correct ingericht als de id ontbreekt in het DCS-antwoord. Een niet-succesvolle reactie retourneert een foutcode en een foutbericht in het dialoogvenster [!UICONTROL Response] zoals hieronder weergegeven. Neem contact op met de klantenservice als dit foutbericht wordt weergegeven in het DCS-antwoord.

![](assets/charles_response_unsuccessful.png)

Zie voor meer informatie over foutcodes [DCS-foutcodes, berichten en voorbeelden](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-error-codes.html).
