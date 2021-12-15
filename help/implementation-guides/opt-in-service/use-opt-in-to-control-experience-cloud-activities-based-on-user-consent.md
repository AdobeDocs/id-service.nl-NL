---
title: Inschakelen gebruiken om Experience Cloud-activiteiten te beheren op basis van toestemming van de gebruiker
description: Het Adobe Opt-in Voorwerp is een uitbreiding van de Dienst van de Identiteit van Adobe Experience Platform, die wordt ontworpen om u te helpen controleren of en welke Experience Cloud oplossingen tot koekjes op Web-pagina's of initiërende bakens kunnen leiden, op eindgebruikerstoestemming wordt gebaseerd.
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
source-git-commit: 0dca594c090095a01dfa2d02a98dfeba7ca02dca
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# Experience Cloud-activiteiten beheren op basis van toestemming van gebruiker

De Adobe [!UICONTROL Opt-in] Object is een uitbreiding van de Adobe [!UICONTROL Experience Platform Identity Service], ontworpen om u te helpen bepalen of en welke Experience Cloud-oplossingen cookies kunnen maken op webpagina&#39;s of bakens kunnen initiëren, op basis van toestemming van de eindgebruiker.

## De basisbeginselen van [!UICONTROL Opt-In]

Een belangrijk aspect van privacyregels is het verkrijgen en overbrengen van toestemming van gebruikers over de manier waarop hun persoonsgegevens kunnen worden gebruikt en door wie. De meest recente versie van de [!UICONTROL Identity Service] omvat functionaliteit die voorziet in voorwaardelijke branding (zoals voorafgaande en achteraf toestemming) van Experience Cloud-oplossingstags, op basis van of de toestemming van de eindgebruiker wordt gegeven. Dit proces wordt weergegeven in de volgende afbeelding:

![Grafiek van hoe [!UICONTROL Opt-in] werken](assets/opt-in.png)

[!UICONTROL Opt-in] werkt als volgt:

**Indien [!UICONTROL Opt-in] wordt toegelaten in de Dienst van de Identiteit (via een variabele Van Boole), vertraagt het de oplossingsbibliotheken van de Experience Cloud van het vuren van markeringen of het plaatsen van koekjes tot de toestemming voor die oplossing is gegeven.**

[!UICONTROL Opt-in] U kunt ook bepalen of tags worden geactiveerd voordat de gebruiker hiermee akkoord gaat en vervolgens deze informatie over toestemming (samen met de toestemming die de eindgebruiker heeft gegeven) wordt opgeslagen zodat deze bij volgende treffers kan worden gebruikt. Opslag van de toestemming is beschikbaar in de [!UICONTROL Opt-in] of u kunt integreren met een CMP en er toestemmingsselecties voor laten opslaan.

## Het toelaten en het Vormen [!UICONTROL Opt-In]

[!UICONTROL Opt-in] is het eenvoudigst te configureren met Adobe Experience Platform-tags (voorheen Launch). Bekijk de volgende korte video om te zien hoe.

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Als u geen Experience Platform-tags gebruikt, kunt u [!UICONTROL Opt-in]De configuratie van de gebruiker in de initialisatie van het algemene bezoekersobject, zoals getoond in het dialoogvenster [documentatie](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/getting-started.html?lang=en).

## Implementatie [!UICONTROL Opt-In] op de pagina

Al deze installatie- en achtergrondinformatie is precies in voorbereiding op het bieden van een interface voor bezoekers van de site die met toestemmingsopties kunnen worden weergegeven. Deze UI kan door u worden gebouwd, of u kunt een partner gebruiken CMP (het Platform van het Beheer van de Toestemming) om UI tot stand te brengen.

Bij het instellen van een gebruikersinterface [!UICONTROL Opt-in] om toestemming te verzamelen, zou het moeten worden gevormd om APIs te roepen die in zullen haak [!UICONTROL Opt-in] en de Commissie ervan in kennis stellen dat zij sommige of alle Adobe Experience Cloud-oplossingen goedkeurt. Gedetailleerde informatie over deze API&#39;s vindt u in de [Referentiedocumentatie voor aanmelding](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/api.html?lang=en). Aanvullende informatie over Opt-in vindt u ook op de omliggende documentatiepagina&#39;s.

## [!UICONTROL Opt-In] Demo

In de volgende video ziet u een snelle demo van [!UICONTROL Opt-in] werken aan de pagina, en hoe het kan beïnvloeden of de oplossingen van de Experience Cloud koekjes kunnen plaatsen, beacons in werking stellen, etc.

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**OPMERKING:** Het is belangrijk op te merken dat op het moment van het schrijven van dit artikel, [!UICONTROL Opt-in] is niet in de bibliotheken voor alle Experience Cloud-toepassingen ingebouwd. De bibliotheken die momenteel worden ondersteund voor [!UICONTROL Opt-in] zijn:

* Identiteitsservice
* Analytics
* Audience Manager
* [!DNL Target]
