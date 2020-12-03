---
description: Een overzicht van de processen van de synchronisatie van identiteitskaart en gelijke tarieven in de Dienst van de Identiteit van de Experience Cloud, met inbegrip van Adobe Media Optimizer en de dienst van identiteitskaart
keywords: ID Service
seo-description: Een overzicht van de processen van de synchronisatie van identiteitskaart en gelijke tarieven in de Dienst van de Identiteit van de Experience Cloud, met inbegrip van Adobe Media Optimizer en de dienst van identiteitskaart
seo-title: ID-synchronisatie en overeenkomsten
title: ID-synchronisatie en overeenkomsten
uuid: 31bd655f-2b9e-4f8d-9a1f-e81a6110eda8
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 0%

---


# ID-synchronisatie en overeenkomsten{#understanding-id-synchronization-and-match-rates}

Een overzicht van de processen van de synchronisatie van identiteitskaart en gelijke tarieven in de Dienst van de Identiteit van de Experience Cloud, met inbegrip van Adobe Media Optimizer en de dienst van identiteitskaart

## ID-synchronisatie en overeenkomstige snelheden {#section-f652aae7234945e89d26dd833c5215fb}

Identiteitssynchronisatie komt overeen met IDs die door de dienst van identiteitskaart aan IDs wordt toegewezen aan plaatsbezoekers door onze klanten. Stel dat de id-service een bezoeker-id 1234 heeft toegewezen. Een ander platform kent deze bezoeker op ID 4321. De dienst van identiteitskaart brengt deze IDs samen tijdens het synchronisatieproces in kaart. De resultaten voegen nieuwe gegevenspunten toe aan wat onze klanten over hun plaatsbezoekers weten. En, als de dienst van identiteitskaart geen identiteitskaart kan aanpassen, leidt het tot nieuwe en gebruikt die identiteitskaart voor toekomstige synchronisatie.

Met Identieke snelheden wordt de doeltreffendheid van het synchronisatieproces van de id gemeten en gevalideerd. De hoge gelijke tarieven wijzen erop dat een bepaalde dienst effectiever zal zijn en toegang tot een groter online publiek dan de dienst met lage gelijke tarieven zal verlenen. Het vergelijken van gelijke tarieven is een kwantificeerbare manier om verschillende geïntegreerde ad technologieplatforms te evalueren.

![](assets/idsync2.png)

**Zorgen voor hoge match-rates**

Om hoge gelijke tarieven te produceren, is het belangrijk aan opstelling de dienst van identiteitskaart behoorlijk (zie de [standaard implementatiegids](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445)). Een correcte implementatie helpt hoge gelijke tarieven te verzekeren omdat de dienst van identiteitskaart de koekjes laat plaatsen het vereist om identiteitskaart met toegelaten gegevenspartners te functioneren en te synchroniseren. Nochtans, kunnen de factoren zoals langzame verbindingen van Internet, gegevensinzameling van mobiele apparaten of draadloze netwerken beïnvloeden hoe goed de dienst van identiteitskaart verzamelt, synchroniseert, en past IDs aan. Deze cliënt-zijvariabelen zijn voorbij de controle van de dienst van identiteitskaart of [!DNL Adobe].

## ID-synchronisatieproces is beschreven {#section-a541a85cbbc74f5682824b1a2ee2a657}

De dienst van identiteitskaart synchroniseert identiteitskaarts in real time. Dit proces werkt in browser in plaats van door een server-aan-server gegevensoverdracht. In de volgende tabel worden de stappen in het synchronisatieproces van de id beschreven.

**Stap 1: Pagina laden**

Wanneer een bezoeker naar uw site komt en een pagina laadt, maakt de `Visitor.getInstance` functie een [CORS](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758) - of JSON-P-aanroep naar de id-service. De id-service reageert met een cookie die de [!DNL Experience Cloud] id (MID) van de bezoeker bevat. De id is een unieke id die aan elke sitebezoeker is toegewezen. Zie ook [Cookies en de Experience Cloud Identity Service](../introduction/cookies.md).

**Stap 2: iFrame laden**

Terwijl de hoofdtekst van de pagina wordt geladen, laadt de id-service een iFrame met de naam *`Destination Publishing iFrame`*. De [!UICONTROL Destination Publishing iFrame] code wordt in een domein geladen dat los staat van de bovenliggende pagina. Dit ontwerp zorgt voor betere paginaprestaties omdat de iFrame:

* Hiermee wordt asynchroon geladen ten opzichte van de bovenliggende pagina. Dit betekent dat de bovenliggende pagina onafhankelijk van de [!UICONTROL Destination Publishing iFrame]pagina kan worden geladen. Het laden van de iFrame en het laden van ID synchronisatiepixels vanuit het iFrame heeft geen invloed op de bovenliggende pagina of de gebruikerservaring.
* Laadt zo snel mogelijk. Als dit te snel is, kunt u het iFrame laden na de gebeurtenis load van het venster (niet aanbevolen). Zie [idSyncAttachIframeOnWindowLoad](../library/function-vars/idsyncattachiframeonwindowload.md#reference-b86b7112e0814a4c82c4e24c158508f4) voor meer informatie.
* Voorkomt dat code in het iFrame toegang krijgt tot de bovenliggende pagina of dit beïnvloedt.

Zie ook, [hoe de Dienst van de Identiteit van de Experience Cloud verzoekt en IDs plaatst...](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a).

**Stap 3: Vuurwerk-id-syncs**

De id-synchronisatie is een URL die wordt geactiveerd in het iFrame voor publiceren van doelen. Zoals aangetoond in dit generische voorbeeld, bevat een synchronisatie URL van identiteitskaart een de synchronisatieeindpunt van identiteitskaart van een partner en een omleidings URL, die een omleiding terug naar [!DNL Adobe] die hun identiteitskaart omvat.

`http://abc.com?partner_id=abc&sync_id=123&redir=http://dpm.demdex.net/ibs:dpid=<ADOBE_PARTNER_ID>&dpuuid=<PARTNER_UUID>`

See also, [ID Synchronization for Inbound Data Transfers](https://docs.adobe.com/content/help/en/audience-manager/user-guide/implementation-integration-guides/sending-audience-data/batch-data-transfer-process/id-sync-http.html).

**Stap 4: Winkel-id&#39;s**

Gesynchroniseerde id&#39;s worden opgeslagen op de [Edge- en kerngegevensservers](https://docs.adobe.com/content/help/en/audience-manager/user-guide/reference/system-components/components-edge.html).

## Synchronisatieservices beheren synchronisatie van id&#39;s {#section-cd5784d7ad404a24aa28ad4816a0119a}

De term *`Sync Services`* verwijst naar interne [!DNL Experience Cloud] technologieën verantwoordelijk voor de synchronisatie van identiteitskaart. Deze service is standaard ingeschakeld. Als u deze wilt uitschakelen, voegt u een [optionele variabele](../library/function-vars/disableidsync.md#reference-589d6b489ac64eddb5a7ff758945e414) toe aan de ID-service- `Visitor.getInstance` functie. Synchronisatieservices komen overeen met verschillende id&#39; [!DNL Experience Cloud] s, zoals:

* Cookie-id&#39; [!DNL Experience Cloud] s van andere bedrijven naar id&#39; [!DNL Experience Cloud] s van andere bedrijven.

* Eerste-partij [!DNL Experience Cloud] cookie-id&#39;s naar [!DNL Adobe Media Optimizer] (AMO)-id&#39;s.

* Cookie-id&#39; [!DNL Experience Cloud] s van andere leveranciers naar externe gegevensaanbieder en identificatie van platform-id&#39;s. Dit omvat diensten en platforms zoals gegevensaanbieders, vraag- en/of aanbodplatforms, en netwerken, uitwisselingen, enz.
* Eerste-partij [!DNL Experience Cloud] koekje IDs aan dwars-apparaat partner IDs.

## ID-synchronisatie met Adobe Advertising Cloud {#section-642c885ea65d45ffb761f78838735016}

[!DNL Adobe Advertising Cloud] (eerder geroepen [!DNL Adobe Media Optimizer])is een uitzondering op het op iFrame-Gebaseerde proces van de synchronisatie van identiteitskaart. Omdat [!DNL Advertising Cloud] het een vertrouwd domein is, worden id-synchronisaties uitgevoerd vanaf de bovenliggende pagina in plaats van in de [!UICONTROL Destination Publishing iFrame]bovenliggende pagina. Tijdens synchronisatie, roept de dienst van identiteitskaart [!DNL Advertising Cloud] bij `cm.eversttech.net`, die een naam van het erfenisdomein is die door [!DNL Advertising Cloud] voorafgaand aan zijn verwerving door Adobe wordt gebruikt. Het verzenden van gegevens naar [!DNL Advertising Cloud] verbetert de match-snelheden en is automatisch voor klanten van de identiteitskaart die versie 2.0 (of hoger) gebruiken. Zie ook [Advertising Cloud Cookies](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-advertising-cloud.html).

>[!MORELIKETHIS]
>
>* [Inzicht in calls naar het Demdex-domein](https://docs.adobe.com/content/help/en/audience-manager/user-guide/reference/demdex-calls.html)

