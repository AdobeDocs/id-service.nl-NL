---
description: Als u meerdere JavaScript-bestanden hebt die gegevens naar dezelfde rapportsuite verzenden of als u andere technologieën op uw site gebruikt, zoals Flash-videometing, raden wij u aan een respijtperiode te configureren.
keywords: ID Service
seo-description: Als u meerdere JavaScript-bestanden hebt die gegevens naar dezelfde rapportsuite verzenden of als u andere technologieën op uw site gebruikt, zoals Flash-videometing, raden wij u aan een respijtperiode te configureren.
seo-title: De uitstelperiode voor de id-service
title: De uitstelperiode voor de id-service
uuid: 10a7db7d-de32-4379-914f-edaf929efa32
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---


# De uitstelperiode voor de id-service {#the-id-service-grace-period}

Als u meerdere JavaScript-bestanden hebt die gegevens naar dezelfde rapportsuite verzenden of als u andere technologieën op uw site gebruikt, zoals Flash-videometing, raden wij u aan een respijtperiode te configureren.

Nadat u de [!DNL Experience Cloud] id-service hebt geïmplementeerd, ontvangen nieuwe bezoekers geen Analytics-bezoeker-id meer van uw gegevensverzamelingsserver. Als gedeelten van uw site de [!DNL Experience Cloud] ID-service nog niet hebben geïmplementeerd en bezoekers naar deze secties bladeren, wordt de Experience Cloud-id niet herkend en krijgen bezoekers een oudere Analytics-bezoekersidentiteitskaart toegewezen. Hierdoor kunnen dubbele aantallen bezoekers en een onjuiste toewijzing worden gemaakt.

Als de ondersteuningssectie van uw site bijvoorbeeld in een aparte CMS wordt beheerd, hebt u mogelijk een ander JavaScript-bestand voor Analytics voor deze sectie. Als u de bezoekersidentiteitskaart op uw belangrijkste plaats opstelt alvorens u de dienst van bezoekersidentiteitskaart aan de steunplaats opstelt, zullen de nieuwe bezoekers een erfenisAnalytics ID ontvangen wanneer zij de steunsectie bezoeken, en de bezoeken die beide plaatssecties overspannen zullen als verschillende bezoeken worden gemeld.

Het implementeren van de [!DNL Experience Cloud] id-service op sites die meerdere JavaScript-bestanden of andere technologieën (zoals Flash) gebruiken, kan coördinatieproblemen veroorzaken, omdat u de id-service op alle delen van uw site tegelijk moet inschakelen. Door een respijtperiode in te stellen, kunnen nieuwe bezoekers een Analytics-bezoeker-id blijven ontvangen van de [!DNL Experience Cloud] ID-service, zodat bezoekers consistent kunnen worden geïdentificeerd op gedeelten van uw site die niet zijn bijgewerkt voor gebruik van de ID-service.

>[!NOTE]
>
>Voor ondersteuning voor de respijtperiode is versie 1.3 of hoger van de [!DNL Experience Cloud] id-service vereist.

## Heb ik een respijtperiode nodig? {#section-fd34c7ff697348a39f49258b7d39eb42}

Als u één JavaScript-bestand voor Analytics hebt en geen andere AppMeasurement-bibliotheken gebruikt, hebt u geen respijtperiode nodig. U kunt de update uitvoeren in het enige JavaScript-bestand en nieuwe bezoekers worden tijdens het bezoek op consistente wijze geïdentificeerd met de marketingcloud-id.

Als u meerdere JavaScript-bestanden hebt die gegevens naar *dezelfde rapportsuite* verzenden of als u andere technologieën op uw site gebruikt, zoals Flash-videometing, raden wij u aan een respijtperiode te configureren.

## Hoe kan ik een respijtperiode toestaan? {#section-512d5cd8570e483cbdd8b04457a16ced}

Contact [Customer Care](https://helpx.adobe.com/marketing-cloud/contact-support.html).
