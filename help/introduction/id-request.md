---
description: Een overzicht van het proces voor het aanvragen en beantwoorden van id's. Deze voorbeelden behandelen identiteitskaart taak op individuele plaatsen, over verschillende plaatsen, en voor plaatsen die door verschillende klanten van Experience Cloud met hun eigen organisatie IDs worden beheerd.
keywords: ID-service
title: Hoe de Dienst van de Identiteit van de Experience Cloud verzoekt en identiteitskaart plaatst
exl-id: 1bbee560-d72a-47cf-b3fe-d6bbcacb9eff
source-git-commit: fa2549090e6790763a7ac6b87348789678d18ab6
workflow-type: tm+mt
source-wordcount: '746'
ht-degree: 0%

---

# Hoe de Dienst van de Identiteit van de Experience Cloud verzoekt en identiteitskaart plaatst{#how-the-experience-cloud-id-service-requests-and-sets-ids}

Een overzicht van het proces voor het aanvragen en beantwoorden van id&#39;s. Deze voorbeelden behandelen identiteitskaart taak op individuele plaatsen, over verschillende plaatsen, en voor plaatsen die door verschillende klanten van Experience Cloud met hun eigen organisatie IDs worden beheerd.

>[!NOTE]
>
>Als u niet bekend bent met de manier waarop de Experience Cloud Identity Service de bezoeker-id maakt, kunt u het beste even controleren [Experience Cloud](../introduction/cookies.md).

## Een Experience Cloud-id aanvragen {#section-0b5e261fbd0547d9b9a1680e5ce536cc}

In de volgende voorbeelden wordt getoond hoe de id-service de Experience Cloud-bezoeker-id aanvraagt en ontvangt. In deze voorbeelden worden twee fictieve bedrijven, de Food Company en de Sports Company, gebruikt om gegevensstromen voor identiteitsverzoeken en reacties aan te tonen. Elk bedrijf heeft een unieke Experience Cloud organisatie-id en heeft de ID-servicecode op al hun sites geïmplementeerd. Deze gebruiksgevallen vertegenwoordigen gegevensstromen voor een generische de dienstimplementatie van identiteitskaart zonder Analytics, erfenis IDs, of browsers die derdekoekjes blokkeren.

![](assets/sample_sites.png)

**Eerste aanvraag**

In dit voorbeeld komt een nieuwe bezoeker naar de pizza-site die wordt beheerd door de Food Company. De Food Company heeft ID-servicecode op de pizza-website. Wanneer de pizza-site wordt geladen, controleert de ID-servicecode of het AMCV-cookie zich in het pizza-domein bevindt.

* Als het AMCV-cookie is ingesteld, heeft de sitebezoeker een Experience Cloud-id. In dit geval houdt het cookie de bezoeker bij en deelt het gegevens met andere Experience Cloud-oplossingen.
* Als het AMCV-cookie niet is ingesteld, wordt met de ID-servicecode een regionale [gegevensverzamelingsserver](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html?lang=en) (DCS) bij `dpm.demdex.net/id` (zie ook: [Inzicht krijgen in oproepen van het demdex-domein](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=en). De oproep omvat de organisatie-id voor de Food Company. De organisatie-id wordt ingesteld in het dialoogvenster `Visitor.getInstance` functie van de ID-servicecode.

![](assets/request1.png)

**Eerste reactie**

In de reactie retourneert de DCS de [!DNL Experience Cloud] ID (MID) en het demdex-cookie. De ID-servicecode schrijft de MID-waarde naar het AMCV-cookie. Bijvoorbeeld, zeg DCS een MID waarde van 1234 terugkeert. Het zou de AMCV-cookie opslaan als `mid|1234` en wordt ingesteld in het pizzadomein van de eerste partij. Het demdex-cookie bevat ook een unieke id (noem het maar 5678). Deze cookie wordt ingesteld in het domein demdex.net van een derde, dat los staat van het pizza-domein.

![](assets/response1.png)

Zoals u in het volgende voorbeeld zult zien, staat demdex ID en organisatie identiteitskaart de dienst van identiteitskaart toe om correcte MID tot stand te brengen en terug te keren wanneer onze bezoeker naar een andere plaats die tot het Bedrijf van de Levensmiddelen behoort.

## Verzoek en antwoord naar andere sites {#section-15ea880453af467abd2874b8b4ed6ee9}

In dit voorbeeld navigeert onze bezoeker van de Food Company naar de tacos-site vanuit de pizza-site. De Food Company heeft de dienstcode van identiteitskaart op de website van tacos. De bezoeker is nooit geweest bij de tacos-website.

Gezien deze omstandigheden is er geen AMCV-cookie op de tacos-site. De id-service kan de AMCV-cookie die op de pizza-site is ingesteld, niet gebruiken omdat deze specifiek is voor het pizza-domein. Dientengevolge, moet de dienst van identiteitskaart DCS roepen om een bezoekersidentiteitskaart te controleren en te verzoeken. In dit geval bevat de DCS-oproep de organisatie-id van de Food Company *en* de demdex-id. De demdex-id wordt opgepakt van de pizza-site en opgeslagen als een cookie van een derde onder het domein demdex.net.

![](assets/request2.png)

Nadat het DCS de organisatie-id en de demdex-id ontvangt, wordt de juiste MID voor de bezoeker van de site gemaakt en geretourneerd. Omdat de MID wiskundig wordt afgeleid van de organisatie-id en de demdex-id, bevat het cookie van AMCV de MID-waarde. `mid = 1234`.

![](assets/response2.png)

## ID-aanvragen van andere sites {#section-ba9a929e50d64b0aba080630fd83b6f1}

In dit voorbeeld verlaat onze bezoeker de sites van de Food Company en navigeert hij naar de voetbalsite van de Sports Company. Wanneer de bezoeker naar de voetbalsite komt, werkt het proces voor het controleren en aanvragen van id&#39;s op dezelfde manier als in de vorige voorbeelden wordt beschreven. Nochtans, omdat het Bedrijf van Sport zijn eigen organisatie identiteitskaart heeft, keert de dienst van identiteitskaart een verschillende MID terug. De nieuwe MID is uniek aan de domeinen die door het Bedrijf van Sport worden gecontroleerd en laat die onderneming bezoekersgegevens over oplossingen in volgen en delen [!DNL Experience Cloud]. De demdex-id blijft hetzelfde voor deze bezoeker, omdat deze in een cookie van een derde wordt opgenomen en in verschillende domeinen blijft bestaan.

![](assets/req_resp.png)
