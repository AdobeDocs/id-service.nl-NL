---
title: Inschakelen gebruiken om Experience Cloud-activiteiten te beheren op basis van toestemming van de gebruiker
description: Het Adobe Opt-in Voorwerp is een uitbreiding van de Dienst van de Identiteit van Adobe Experience Platform, die wordt ontworpen om u te helpen controleren of en welke Experience Cloud oplossingen tot koekjes op Web-pagina's of initiërende bakens kunnen leiden, op eindgebruikerstoestemming wordt gebaseerd.
translation-type: tm+mt
source-git-commit: 3aba8820ef40d068c732a637be5ab67652a8d35d
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 0%

---


# Experience Cloud-activiteiten beheren op basis van toestemming van gebruiker

Het Adobe- [!UICONTROL Opt-in] object is een extensie van de Adobe [!UICONTROL Experience Platform Identity Service]die u helpt te bepalen of en welke Experience Cloud-oplossingen cookies op webpagina&#39;s kunnen maken of bakens kunnen initiëren, op basis van toestemming van de eindgebruiker.

## De basisbeginselen van [!UICONTROL Opt-In]

Een belangrijk aspect van privacyregels is het verkrijgen en overbrengen van toestemming van gebruikers over de manier waarop hun persoonsgegevens kunnen worden gebruikt en door wie. De meest recente versie van de [!UICONTROL Identity Service] code bevat functionaliteit, die zich tussen de gebruiker (de gebruikersinterface) en de Adobe-oplossingen bevindt en die voorziet in voorwaardelijk vuren (bv. voorafgaande en achteraf toestemming) van Adobe Experience Cloud-oplossingstags, op basis van of de eindgebruiker toestemming heeft gegeven. Dit wordt getoond in het volgende beeld:

![Schema van de werking van [!UICONTROL Opt-in] het programma](assets/opt-in.png)

[!UICONTROL Opt-in] is eigenlijk de poortwachter... of is het de keymaster? U beslist.

Het komt hierop neer:

**Als deze optie [!UICONTROL Opt-in] is ingeschakeld in de identiteitsservice (via een Booleaanse variabele), wordt de Experience Cloud-oplossingenbibliotheken vertraagd door tags te typen of cookies in te stellen totdat er toestemming is gegeven voor die oplossing.**

[!UICONTROL Opt-in] U kunt ook bepalen of er tags worden geactiveerd *voordat* de gebruiker hiermee akkoord gaat. Vervolgens wordt deze informatie over toestemming (samen met de toestemming van de eindgebruiker) opgeslagen, zodat deze kan worden gebruikt bij volgende treffers. Opslag van de toestemming is beschikbaar in de [!UICONTROL Opt-in] opties, of u kunt met CMP integreren en het hebben toestemmingsselecties.

## Het toelaten en het Vormen [!UICONTROL Opt-In]

[!UICONTROL Opt-in] is ook het gemakkelijkst configureerbaar met Adobe Experience Platform Launch. Bekijk de volgende korte video om te zien hoe.

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Als u geen Experience Platform Launch gebruikt, kunt u de configuratie [!UICONTROL Opt-in]van de opstelling in de initialisatie van het globale voorwerp van de Bezoeker, zoals aangetoond in de [documentatie](https://marketing.adobe.com/resources/help/en_US/mcvid/getting-started.html)plaatsen.

## Implementeren [!UICONTROL Opt-In] op de pagina

Al deze installatie- en achtergrondinformatie is precies in voorbereiding op het bieden van een interface voor bezoekers van de site die met toestemmingsopties kunnen worden weergegeven. Deze UI kan door u worden gebouwd, of u kunt een partner gebruiken CMP (het Platform van het Beheer van de Toestemming) om UI tot stand te brengen.

Wanneer vestiging een UI om toestemming te gebruiken [!UICONTROL Opt-in] te verzamelen, zou het moeten worden gevormd om APIs te roepen die in zullen aansluiten [!UICONTROL Opt-in] en het zal informeren om toestemming aan sommige of alle oplossingen van Adobe Experience Cloud te geven. Gedetailleerde informatie over deze API&#39;s vindt u in de documentatie [van de](https://marketing.adobe.com/resources/help/en_US/mcvid/api.html)aanmeldingsreferenties. Aanvullende informatie over Opt-in vindt u ook op de omliggende documentatiepagina&#39;s.

## [!UICONTROL Opt-In] Demo

In de volgende video ziet u een snelle demo van het [!UICONTROL Opt-in] werken aan de pagina en hoe deze invloed kan hebben op het feit of de Experience Cloud-oplossingen cookies kunnen instellen, bakens kunnen starten, enzovoort.

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**OPMERKING:** Het is belangrijk om op te merken dat op het moment van het schrijven van dit artikel, niet in de bibliotheken voor alle Experience Cloud-oplossingen [!UICONTROL Opt-in] is ingebouwd. De bibliotheken die momenteel worden ondersteund voor [!UICONTROL Opt-in] zijn:

* Identiteitsservice
* Analytics
* Audience Manager
* [!DNL Target]
