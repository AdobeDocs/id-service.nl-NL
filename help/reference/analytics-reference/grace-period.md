---
description: Als u meerdere JavaScript-bestanden hebt die gegevens naar dezelfde rapportsuite verzenden, of als u andere technologieën op uw site gebruikt, zoals videometingen voor Flash, raden we u aan een respijtperiode te configureren.
keywords: ID-service
title: De uitstelperiode voor de id-service
exl-id: 83b4898c-8358-458b-a798-1e3c9633afe9
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# De uitstelperiode voor de id-service {#the-id-service-grace-period}

Als u meerdere JavaScript-bestanden hebt die gegevens naar dezelfde rapportsuite verzenden, of als u andere technologieën op uw site gebruikt, zoals videometingen voor Flash, raden we u aan een respijtperiode te configureren.

Nadat u de [!DNL Experience Cloud] ID-service hebt geïmplementeerd, ontvangen nieuwe bezoekers geen Analytics-bezoeker-id meer van uw gegevensverzamelingsserver. Als gedeelten van uw site de [!DNL Experience Cloud] ID-service nog niet hebben geïmplementeerd en bezoekers naar deze secties bladeren, wordt de Experience Cloud-id niet herkend en krijgen bezoekers een verouderde Analytics-bezoekersidentiteitskaart toegewezen. Hierdoor kunnen dubbele aantallen bezoekers en een onjuiste toewijzing worden gemaakt.

Als de ondersteuningssectie van uw site bijvoorbeeld in een aparte CMS wordt beheerd, hebt u mogelijk een ander JavaScript-bestand voor Analytics voor deze sectie. Als u de bezoekersidentiteitskaart op uw belangrijkste plaats opstelt alvorens u de dienst van bezoekersidentiteitskaart aan de steunplaats opstelt, zullen de nieuwe bezoekers een erfenisAnalytics ID ontvangen wanneer zij de steunsectie bezoeken, en de bezoeken die beide plaatssecties overspannen zullen als verschillende bezoeken worden gemeld.

Het implementeren van de id-service [!DNL Experience Cloud] op sites die meerdere JavaScript-bestanden of andere technologieën (zoals Flash) gebruiken, kan coördinatieproblemen veroorzaken, omdat u de id-service op alle delen van uw site tegelijk moet inschakelen. Door een respijtperiode in te stellen, kunnen nieuwe bezoekers een Analytics-bezoeker-id blijven ontvangen van de [!DNL Experience Cloud] ID-service, zodat bezoekers consistent kunnen worden geïdentificeerd op gedeelten van uw site die niet zijn bijgewerkt voor gebruik van de ID-service.

>[!NOTE]
>
>Voor ondersteuning van de respijtperiode is versie 1.3 of hoger van de [!DNL Experience Cloud] ID-service vereist.

## Heb ik een respijtperiode nodig? {#section-fd34c7ff697348a39f49258b7d39eb42}

Als u één JavaScript-bestand voor Analytics hebt en geen andere bibliotheken voor AppMeasurementen gebruikt, hebt u geen respijtperiode nodig. U kunt de update uitvoeren in het enkele JavaScript-bestand en nieuwe bezoekers worden tijdens het bezoek op consistente wijze geïdentificeerd met de marketingcloud-id.

Als u veelvoudige JavaScript dossiers hebt die gegevens naar *zelfde rapportreeks* verzenden, of als u andere technologieën op uw plaats zoals de videometing van de Flash gebruikt, adviseren wij het vormen van een respijtperiode.

## Hoe kan ik een respijtperiode toestaan? {#section-512d5cd8570e483cbdd8b04457a16ced}

De Zorg van de Klant van het contact [ ](https://helpx.adobe.com/marketing-cloud/contact-support.html).
