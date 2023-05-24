---
description: Als u meerdere JavaScript-bestanden hebt die gegevens naar dezelfde rapportsuite verzenden of als u andere technologieën op uw site gebruikt, zoals Flash-videometing, raden wij u aan een respijtperiode te configureren.
keywords: ID-service
title: De uitstelperiode voor de id-service
exl-id: 83b4898c-8358-458b-a798-1e3c9633afe9
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# De uitstelperiode voor de id-service {#the-id-service-grace-period}

Als u meerdere JavaScript-bestanden hebt die gegevens naar dezelfde rapportsuite verzenden of als u andere technologieën op uw site gebruikt, zoals Flash-videometing, raden wij u aan een respijtperiode te configureren.

Nadat u de [!DNL Experience Cloud] De dienst van identiteitskaart, de nieuwe bezoekers ontvangen niet meer een bezoekersidentiteitskaart van de Analyse van uw server van de gegevensinzameling. Als gedeelten van uw site nog niet zijn geïmplementeerd, [!DNL Experience Cloud] De dienst van identiteitskaart, wanneer de bezoekers aan deze secties doorbladeren, wordt identiteitskaart van de Experience Cloud niet erkend en de bezoekers krijgen een erfenisBezoeker-identiteitskaart van de Analyse toegewezen. Hierdoor kunnen dubbele aantallen bezoekers en een onjuiste toewijzing worden gemaakt.

Als de ondersteuningssectie van uw site bijvoorbeeld in een aparte CMS wordt beheerd, hebt u mogelijk een ander JavaScript-bestand voor Analytics voor deze sectie. Als u de bezoekersidentiteitskaart op uw belangrijkste plaats opstelt alvorens u de dienst van bezoekersidentiteitskaart aan de steunplaats opstelt, zullen de nieuwe bezoekers een erfenisAnalytics ID ontvangen wanneer zij de steunsectie bezoeken, en de bezoeken die beide plaatssecties overspannen zullen als verschillende bezoeken worden gemeld.

De [!DNL Experience Cloud] De dienst van identiteitskaart op plaatsen die veelvoudige dossiers JavaScript of andere technologieën (zoals Flash) gebruiken kan coördinatiekwesties veroorzaken aangezien u de dienst van identiteitskaart op alle gedeelten van uw plaats tezelfdertijd moet toelaten. Door een respijtperiode in te stellen, kunnen nieuwe bezoekers een Analytics-bezoeker-id blijven ontvangen van de [!DNL Experience Cloud] De dienst van identiteitskaart, zodat kunnen de bezoekers constant op secties van uw plaats worden geïdentificeerd die niet zijn bevorderd om de dienst van identiteitskaart te gebruiken.

>[!NOTE]
>
>Voor ondersteuning voor de respijtperiode is versie 1.3 of hoger van de [!DNL Experience Cloud] ID-service.

## Heb ik een respijtperiode nodig? {#section-fd34c7ff697348a39f49258b7d39eb42}

Als u één JavaScript-bestand voor Analytics hebt en geen andere AppMeasurement-bibliotheken gebruikt, hebt u geen respijtperiode nodig. U kunt de update uitvoeren in het enige JavaScript-bestand en nieuwe bezoekers worden tijdens het bezoek op consistente wijze geïdentificeerd met de marketingcloud-id.

Als u meerdere JavaScript-bestanden hebt die gegevens verzenden naar de *zelfde rapportsuite* of als u andere technologieën op uw site gebruikt, zoals Flash-videometing, raden wij u aan een respijtperiode te configureren.

## Hoe kan ik een respijtperiode toestaan? {#section-512d5cd8570e483cbdd8b04457a16ced}

Contact [Klantenservice](https://helpx.adobe.com/marketing-cloud/contact-support.html).
