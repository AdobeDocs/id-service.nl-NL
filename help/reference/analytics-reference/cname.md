---
description: Als u een hoofdinvoersite hebt waarop klanten kunnen worden geïdentificeerd voordat ze andere domeinen bezoeken, kan een CNAME het bijhouden van gegevens naar andere domeinen toestaan in browsers die cookies van derden (zoals Safari) niet accepteren.
keywords: volgorde van activiteiten;ID-service
seo-description: Als u een hoofdinvoersite hebt waarop klanten kunnen worden geïdentificeerd voordat ze andere domeinen bezoeken, kan een CNAME het bijhouden van gegevens naar andere domeinen toestaan in browsers die cookies van derden (zoals Safari) niet accepteren.
seo-title: CNAME's voor gegevensverzameling en interdomeintracering
title: CNAME's voor gegevensverzameling en interdomeintracering
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: 053d45656e941adc1950d49099c30da1d9a72aa0
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 0%

---


# CNAME&#39;s voor gegevensverzameling en domeinoverschrijdende tracering{#data-collection-cnames-and-cross-domain-tracking}

Als u een hoofdinvoersite hebt waarop klanten kunnen worden geïdentificeerd voordat ze andere domeinen bezoeken, kan een CNAME het bijhouden van gegevens naar andere domeinen toestaan in browsers die cookies van derden (zoals Safari) niet accepteren.

In browsers die cookies van derden accepteren, wordt een cookie door de server voor gegevensverzameling ingesteld tijdens de aanvraag voor een bezoeker-id. Met dit cookie kan de bezoekersidentiteitsservice dezelfde Experience Cloud bezoekersidentiteitskaart retourneren op alle domeinen die zijn geconfigureerd met dezelfde Experience Cloud Org-id.

In browsers die cookies van derden afwijzen, wordt voor elk domein een nieuwe Experience Cloud-bezoeker-id toegewezen.

Met het cookie demdex.net kan de bezoeker-id-service hetzelfde niveau van interdomein bijhouden bieden als het s_vi-cookie in Analytics, waar het cookie in sommige browsers wordt geaccepteerd en in verschillende domeinen wordt gebruikt, maar door andere browsers wordt geweigerd.

## CNAME&#39;s voor gegevensverzameling {#section-48fd186d376a48079769d12c4bd9f317}

Wanneer het Analytics-cookie door de gegevensverzamelingsserver is ingesteld, hebben veel klanten CNAME-records voor gegevensverzamelingsservers geconfigureerd als onderdeel van een [first-party cookie-implementatie](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-first-party.html) om problemen te voorkomen met browsers die cookies van derden afwijzen. Tijdens dit proces wordt het serverdomein van de gegevensverzameling zo geconfigureerd dat het overeenkomt met uw websitedomein, zodat het cookie van de bezoeker-id wordt ingesteld als een cookie van de eerste partij.

Aangezien de bezoekersidentiteitsservice het bezoekerscookie met JavaScript rechtstreeks op het domein van de huidige website instelt, is deze configuratie niet langer nodig om cookies van de eerste partij in te stellen.

Klanten met één webeigenschap (één domein) kunnen migreren van CNAME&#39;s voor gegevensverzameling en in plaats daarvan hun standaardhostnaam voor gegevensverzameling gebruiken (ofwel `omtrdc.net` of `2o7.net`).

Nochtans, is er een extra voordeel aan het gebruiken van een CNAME voor gegevensinzameling die u toestaat om bezoekers tussen een belangrijkste landend domein en andere domeinen in browsers te volgen die derde koekjes niet goedkeuren. Klanten die meerdere wegeigenschappen (meerdere domeinen) hebben, kunnen baat hebben bij het onderhouden van een CNAME voor gegevensverzameling. In de volgende sectie wordt uitgelegd hoe het bijhouden van interdomeinbezoekers werkt.

## Domeinovertrekken {#section-78925af798e24917b9abed79de290ad9}

De dienst van bezoekersidentiteitskaart gebruikt demdex.net als zijn domein voor het volgen van bezoekers over domeinen (maar binnen het zelfde het bezitten bedrijf) als de privacy en browser van de gebruiker montages toestaan.

Een CNAME biedt geen extra voordelen voor andere domeinen. U hebt bijvoorbeeld een primaire site op `mymainsite.com`. U vormde het verslag CNAME om aan uw veilige server van de gegevensinzameling te richten: `smetrics.mymainsite.com`.

Wanneer een gebruiker `mymainsite.com` bezoekt, wordt het de dienstkoekje van identiteitskaart geplaatst door de server van de gegevensinzameling. Dit is toegestaan omdat het domein van de gegevensverzamelingsserver overeenkomt met het domein van de website. Dit is wat bekend staat als het gebruik van een cookie in een *first-party context*, of alleen een *first-party cookie*.

Als u deze zelfde server van de gegevensinzameling op andere plaatsen (bijvoorbeeld, `myothersiteA.com`, en `myothersiteB.com`) ook gebruikt, en een bezoeker later deze plaatsen bezoekt, wordt het koekje dat tijdens het bezoek aan `mymainsite.com` werd geplaatst verzonden in het HTTPS verzoek naar de server van de gegevensinzameling (herinner dat browsers alle koekjes voor een domein met alle verzoeken HTTPS naar dat domein verzenden, zelfs als het domein niet het domein aanpast huidige website). Dit is wat als het gebruiken van een koekje in een *derde context*, of enkel een *derdekoekje* wordt bekend, alhoewel u een CNAME gebruikt. Adobe raadt een CNAME aan voor elk uniek domein.

*Opmerking: Safari blokkeert alle cookies in de context van derden, ongeacht hoe deze zijn ingesteld.*

## CNAME-ondersteuning inschakelen met de Experience Cloud Identity-service {#section-25d4feb686d944e3a877d7aad8dbdf9a}

De CNAME-ondersteuning van de gegevensverzamelingsserver wordt ingeschakeld door het instellen van de variabelen `visitor.marketingCloudServerSecure`.
