---
title: Inschakelen gebruiken om de activiteiten van het Experience Cloud te beheren op basis van toestemming van de gebruiker
description: Het Adobe Opt-in Voorwerp is een uitbreiding van de Dienst van de Identiteit van Adobe Experience Platform, die wordt ontworpen om u te helpen controleren of en welke oplossingen van het Experience Cloud tot koekjes op Web-pagina's kunnen leiden of bakens in werking stellen, die op eindgebruikertoestemming wordt gebaseerd.
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
source-git-commit: 0dca594c090095a01dfa2d02a98dfeba7ca02dca
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 1%

---

# De Activiteiten van het Experience Cloud van de controle die op de Toestemming van de Gebruiker worden gebaseerd

Het object Adobe [!UICONTROL Opt-in] is een uitbreiding van de Adobe [!UICONTROL Experience Platform Identity Service] , waarmee u kunt bepalen of en welke oplossingen voor Experiencen Cloud cookies op webpagina&#39;s kunnen maken of bakens kunnen initiëren, op basis van toestemming van de eindgebruiker.

## De basisbeginselen van [!UICONTROL Opt-In]

Een belangrijk aspect van privacyregels is het verkrijgen en overbrengen van toestemming van gebruikers over de manier waarop hun persoonsgegevens kunnen worden gebruikt en door wie. De meest recente versie van [!UICONTROL Identity Service] bevat functionaliteit die voorwaardelijke afvuren (zoals pre- en posttoestemmingen) van Experience Cloud oplossingstags biedt, op basis van of de toestemming van de eindgebruiker is gegeven. Dit proces wordt weergegeven in de volgende afbeelding:

![ Diagram van hoe [!UICONTROL Opt-in] werkt ](assets/opt-in.png)

[!UICONTROL Opt-in] werkt als volgt:

**als [!UICONTROL Opt-in] in de Dienst van de Identiteit (via een variabele Van Boole) wordt toegelaten, vertraagt het de bibliotheken van de oplossing van het Experience Cloud van het vuren van markeringen of het plaatsen van koekjes tot de toestemming voor die oplossing is gegeven.**

Met [!UICONTROL Opt-in] kunt u ook bepalen of tags worden geactiveerd voordat de gebruiker hiermee akkoord gaat. Vervolgens wordt deze informatie over toestemming (samen met de toestemming van de eindgebruiker) opgeslagen, zodat deze kan worden gebruikt bij volgende treffers. Opslag van de toestemming is beschikbaar in de [!UICONTROL Opt-in] opties, of u kunt met CMP integreren en het hebben toestemmingsselecties.

## Inschakelen en configureren [!UICONTROL Opt-In]

[!UICONTROL Opt-in] kan het gemakkelijkst worden geconfigureerd met Adobe Experience Platform-tags (voorheen Starten). Bekijk de volgende korte video om te zien hoe.

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Als u geen Experience Platform markeringen gebruikt, kunt u [!UICONTROL Opt-in] configuratie in de initialisering van het globale voorwerp van de Bezoeker plaatsen, zoals aangetoond in de [ documentatie ](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/getting-started.html?lang=en).

## [!UICONTROL Opt-In] op de pagina implementeren

Al deze installatie- en achtergrondinformatie is precies in voorbereiding op het bieden van een interface voor bezoekers van de site die met toestemmingsopties kunnen worden weergegeven. Deze interface kan door u worden gebouwd, of u kunt een partner gebruiken CMP (het Platform van het Beheer van de Toestemming) om UI tot stand te brengen.

Wanneer u een gebruikersinterface instelt om [!UICONTROL Opt-in] te gebruiken voor het verzamelen van toestemming, moet u deze zodanig configureren dat API&#39;s worden aangeroepen die aan [!UICONTROL Opt-in] zijn gekoppeld en moet u de gebruikersinterface informeren om toestemming te geven voor sommige of alle Adobe Experience Cloud-oplossingen. De gedetailleerde informatie betreffende deze APIs kan in de [ Opt-binnen documentatie van de Verwijzing ](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/api.html?lang=en) worden gevonden. Aanvullende informatie over Opt-in vindt u ook op de omliggende documentatiepagina&#39;s.

## [!UICONTROL Opt-In] Demo

In de volgende video ziet u een snelle demo van [!UICONTROL Opt-in] over het werken aan de pagina en hoe deze invloed kan hebben op het feit of de oplossingen van het Experience Cloud cookies kunnen instellen, bakens kunnen initialiseren, enzovoort.

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**NOTA:** Het is belangrijk om op te merken dat op het tijdstip van het schrijven van dit artikel, [!UICONTROL Opt-in] niet in de bibliotheken voor alle toepassingen van het Experience Cloud is gebouwd. De bibliotheken die momenteel worden ondersteund voor [!UICONTROL Opt-in] zijn:

* Identiteitsservice
* Analytics
* Audience Manager
* [!DNL Target]
