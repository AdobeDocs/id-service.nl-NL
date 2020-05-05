---
description: 'null'
keywords: order of operations;ID Service
seo-description: 'null'
seo-title: CNAME's voor gegevensverzameling en interdomeintracering
title: CNAME's voor gegevensverzameling en interdomeintracering
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# CNAME&#39;s voor gegevensverzameling en interdomeintracering{#data-collection-cnames-and-cross-domain-tracking}

Als u een hoofdinvoersite hebt waarop klanten kunnen worden geïdentificeerd voordat ze andere domeinen bezoeken, kan een CNAME het bijhouden van gegevens naar andere domeinen toestaan in browsers die cookies van derden (zoals Safari) niet accepteren.

In browsers die cookies van derden accepteren, wordt een cookie door de server voor gegevensverzameling ingesteld tijdens de aanvraag voor een bezoeker-id. Met dit cookie kan de bezoekersidentiteitsservice dezelfde Experience Cloud-bezoekersidentiteitskaart retourneren op alle domeinen die zijn geconfigureerd met dezelfde Experience Cloud Org-id.

In browsers die cookies van derden afwijzen, wordt voor elk domein een nieuwe Experience Cloud-bezoeker-id toegewezen.

Met het cookie demdex.net kan de bezoeker-id-service hetzelfde niveau van interdomein bijhouden bieden als het s_vi-cookie in Analytics, waar het cookie in sommige browsers wordt geaccepteerd en in verschillende domeinen wordt gebruikt, maar door andere browsers wordt geweigerd.

## CNAME&#39;s voor gegevensverzameling {#section-48fd186d376a48079769d12c4bd9f317}

Wanneer het koekje van de Analyse door de server van de gegevensinzameling werd geplaatst, hebben vele klanten CNAME van de server van de gegevensinzameling verslagen als deel van een [eerste-partijkoekjesimplementatie](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-first-party.html) gevormd om kwesties met browsers te vermijden die derdekoekjes verwerpen. Tijdens dit proces wordt het serverdomein van de gegevensverzameling zo geconfigureerd dat het overeenkomt met uw websitedomein, zodat het cookie van de bezoeker-id wordt ingesteld als een cookie van de eerste partij.

Aangezien de bezoekersidentiteitsservice het bezoekerscookie met JavaScript rechtstreeks op het domein van de huidige website instelt, is deze configuratie niet langer nodig om cookies van de eerste partij in te stellen.

Klanten die één enkele Webbezit (één enkel domein) hebben kunnen zich bij de gegevensinzameling CNAMEs migreren en hun standaardgegevens gebruiken inzamelen hostname (of `omtrdc.net` of `2o7.net`).

Nochtans, is er een extra voordeel aan het gebruiken van een CNAME voor gegevensinzameling die u toestaat om bezoekers tussen een belangrijkste landend domein en andere domeinen in browsers te volgen die derde koekjes niet goedkeuren. Klanten die meerdere wegeigenschappen (meerdere domeinen) hebben, kunnen baat hebben bij het onderhouden van een CNAME voor gegevensverzameling. In de volgende sectie wordt uitgelegd hoe het bijhouden van interdomeinbezoekers werkt.

## Hoe CNAMEs dwars-domein het volgen toelaat {#section-78925af798e24917b9abed79de290ad9}

Vanwege de manier waarop cookies van de eerste partij in een context van derden in Apple Safari en sommige andere browsers kunnen worden gebruikt, kunt u met een CNAME klanten bijhouden tussen een primair domein en andere domeinen die dezelfde trackingserver gebruiken.

U hebt bijvoorbeeld een primaire site op `mymainsite.com`. U vormde het verslag CNAME om aan uw veilige server van de gegevensinzameling te richten: `smetrics.mymainsite.com`.

Wanneer een gebruiker `mymainsite.com`bezoekt, wordt het de dienstkoekje van identiteitskaart geplaatst door de server van de gegevensinzameling. Dit wordt toegestaan aangezien het domein van de server van de gegevensinzameling het domein van de website aanpast, en is wat als het gebruiken van een koekje in een *eerste partijcontext*, of enkel een *eerste-partijkoekje* wordt bekend.

Als u deze zelfde server van de gegevensinzameling op andere plaatsen (bijvoorbeeld, `myothersiteA.com`, en `myothersiteB.com``mymainsite.com` ) ook gebruikt, en een bezoeker later deze plaatsen bezoekt, wordt het koekje dat tijdens het bezoek aan werd geplaatst verzonden in het HTTPS verzoek naar de server van de gegevensinzameling (herinner dat browsers alle koekjes voor een domein met alle HTTPS verzoeken naar dat domein verzenden, zelfs als het domein niet het domein van de huidige website aanpast). Dit is wat als het gebruiken van een koekje in een *derdecontext*, of enkel een *derdekoekje* wordt bekend, en het laat zelfde bezoekersidentiteitskaart toe om op deze andere domeinen worden gebruikt. cookies in externe contexten worden in browsers anders verwerkt dan cookies van andere leveranciers.

*Opmerking: Safari blokkeert alle cookies in de context van derden, ongeacht hoe deze zijn ingesteld.*

Dientengevolge, zou uw inzamelingsdomein een domein moeten zijn dat de mensen algemeen bezoeken om een bezoeker te identificeren over domeinen. Als er geen *gemeenschappelijk* domein voor het domein van de gegevensinzameling te gebruiken is, is er geen dwars-domeinvoordeel aan het handhaven van een NAAM voor het domein van de gegevensinzameling. Als de hoofdsite niet eerst wordt bezocht, worden bezoekers op de secundaire site en hoofdsite anders geïdentificeerd.

## Ondersteuning voor CNAME inschakelen met de Experience Cloud Identity Service {#section-25d4feb686d944e3a877d7aad8dbdf9a}

De CNAME-ondersteuning van de gegevensverzamelingsserver wordt ingeschakeld door de `visitor.marketingCloudServerSecure` variabelen in te stellen.
