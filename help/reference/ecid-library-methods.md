---
title: ECID-bibliotheekmethoden in een Safari ITP-wereld
seo-title: ECID-bibliotheekmethoden in een Safari ITP-wereld
description: Documentatie voor Adobe ECID-bibliotheek (ID Service).
seo-description: Documentatie voor Adobe ECID-bibliotheek (ID Service).
translation-type: tm+mt
source-git-commit: ddff95876722b981f22c7e3196ff2ce9b696010e
workflow-type: tm+mt
source-wordcount: '1090'
ht-degree: 0%

---


# ECID-bibliotheekmethoden in een Safari ITP-wereld

Aangezien Safari het bijhouden van meerdere domeinen via ITP aanscherpt, moet Adobe best practices bijhouden voor bibliotheken die klanten ondersteunen, maar ook de privacy en keuze van de consument.

Op 21 februari 2019 heeft Apple zijn laatste update voor ITP (Intelligent Tracking Prevention) bekendgemaakt. In tegenstelling tot eerdere versies die vooral op cookies van derden waren gericht, bevat deze versie nieuwe voorzorgsmaatregelen ter voorkoming van het bijhouden van cookies van andere bedrijven. Voor alle permanente cookies van de eerste partij die via de document.cookie-API zijn ingesteld, vaak ook wel &#39;client-side&#39; cookies genoemd, geldt een limiet van 7 dagen. Cookies van derden blijven geblokkeerd, zoals in eerdere versies van ITP is aangegeven. Lees voor meer informatie over ITP 2.1 en de impact van Adobe-oplossingen [Safari ITP 2.1 Impact op Adobe Experience Cloud en Experience Platform Customers](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac).

## Veelgestelde vragen over Adobe ECID voor Safari ITP

**Waarom wordt het cookie AMCV, ingesteld door de Experience Cloud ID-bibliotheek (ECID) in het domein van een eerste partij van een klant, beïnvloed door ITP 2.1?**

Het AMCV-cookie is momenteel gebaseerd op de document.cookie-API en wordt ingesteld via &quot;client-side&quot;. Safari geeft de voorkeur aan cookies die op de server van de klant zijn ingesteld.

**Waarom is een cookie ingesteld via een CNAME-trackingserver een betere optie voor tracering in Safari?**

De regels van ITP richten zich op het geven van controle terug aan de ontwikkelaars. Implementaties via CNAME-certificaten kunnen niet alleen via JavaScript worden uitgevoerd. Het CNAME-certificeringsprogramma van Adobe (servercontrole) is in overeenstemming met ITP en maakt al jaren deel uit van de Adobe-strategie. De ECID-bibliotheek geeft methoden vrij die gericht zijn op het verplaatsen van de functionaliteit van de ECID-bibliotheek naar een CNAME-implementatie.

**Waarom richt Adobe zich op de ECID-bibliotheek wanneer andere methoden voor het bijhouden van bezoekers van Analytics vandaag worden gebruikt met CNAME&#39;s?**

De ECID-bibliotheek, AMCV-cookie en ECID (ook bekend als MID) zijn de methode voor de integratie van alle Adobe-oplossingen onder één id. Deze id blijft de prioritaire id op cookieniveau in de routekaart van het Adobe-product en is de standaard cookie-id voor het Adobe Experience Platform.

**Helpen CNAMEs klanten multi-domein het volgen toelaten?**

De zelfde regels en de bedenkingen die eerder met CNAMEs bestonden bestaan nog. In sommige gevallen, kan CNAMEs in een multi-domeinscenario helpen. Als u een hoofdinvoersite hebt waarop gebruikers kunnen worden geïdentificeerd voordat ze andere domeinen bezoeken, kan een CNAME het bijhouden van meerdere domeinen inschakelen in browsers die cookies van derden niet accepteren. Nochtans, terwijl CNAMEs met multi-domein in sommige scenario&#39;s kan helpen, is de reden voor de verschuiving van implementatie ECID naar implementatie CNAME voor blijvende bezoekersidentificatie, niet multi-domein het volgen. Voor meer op CNAME en multi-domain, zie CNAMEs van de Inzameling van [Gegevens en het Volgen](/help/reference/analytics-reference/cname.md)van dwars-Domein.

Hier worden meer veelgestelde vragen toegevoegd als er aanvullende ITP-wijzigingen worden vrijgegeven. Ga voor meer informatie naar [Adobe Experience League](https://experienceleague.adobe.com/#recommended/solutions/analytics).

## Aan ITP gerelateerde wijzigingen, methoden en configuraties

Aangezien er extra methoden voor tekstspatiëring in Safari zijn gemaakt, worden deze toegevoegd als verwijzing naar deze pagina.

>[!NOTE]
>
>*ECID* = *MID* = *MCID* in alle onderstaande documentatie.

Zie hieronder voor inspanningen met betrekking tot ITP- en ECID-bibliotheekgebruik.

## Gebruik de ECID-bibliotheek en CNAME-tracking om de vervaldatum van de bezoekersidentiteitskaart te verlengen

ITP 2.1 belemmert de mogelijkheid om cookies aan de clientzijde te schrijven, wat de mogelijkheid om klanten nauwkeurige informatie over het bijhouden van bezoekers te verstrekken, beperkt. Als zodanig wordt er een wijziging aangebracht in de CNAME-trackingservers van Adobe om de Experience Cloud-id (ECID) van de bezoeker op te slaan in een cookie van de eerste partij.

Deze wijziging is alleen nuttig voor ECID-klanten die een Analytics CNAME gebruiken in de context van de eerste partij. Als u een Analytics-klant bent die momenteel geen CNAME of zelfs een niet-Analytics-klant gebruikt, komt u nog steeds in aanmerking voor een CNAME-record. Neem contact op met de klantenservice of uw accountvertegenwoordiger om het registratieproces voor een [CNAME](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-first-party.html)te starten.

Voer een upgrade uit naar de ECID-bibliotheek v.4.3.0 + om deze wijziging te benutten.

**Ontwerp**

Zodra een identiteitskaart- verzoek wordt ingediend aan demdex.net en een ECID wordt teruggewonnen, als een het volgen server in uw ECID bibliotheek wordt geplaatst, wordt een identiteitskaart- verzoek gemaakt aan het domein van de klant. Dit eindpunt leest de ecid param van het vraagkoord, en plaatst een nieuw [koekje](/help/introduction/cookies.md) dat slechts ECID en een vervaldatum twee jaar in de toekomst omvat. Telkens als dit eindpunt op deze manier wordt geroepen, wordt het `s_ecid` koekje herschreven met een vervaldatum twee jaar van de tijd van die vraag. De ECID-bibliotheek moet worden bijgewerkt naar versie 4.3.0, zodat de waarde van dit cookie kan worden opgehaald.

Dit nieuwe `s_ecid` cookie heeft dezelfde status als de AMCV-cookie. Als de ecid uit het `s_ecid` cookie wordt gelezen, wordt demdex altijd direct aangeroepen om de meest recente status van de opt-out voor die id op te halen en in het AMCV-cookie opgeslagen.

Als de consument via deze [methode](https://docs.adobe.com/content/help/en/analytics/implementation/js/opt-out.html)ervoor heeft gekozen om Analytics niet te volgen, wordt deze `s_ecid` cookie verwijderd.

De naam van de trackingserver moet aan de VisitorJS-bibliotheek worden opgegeven wanneer de bibliotheek wordt geïnitialiseerd met behulp van trackingServer of trackingServerSecure. Dit zou het trackingServer config in Analytics moeten aanpassen vormt.

Als u ervoor kiest om deze methode niet te gebruiken, voegt u de volgende config toe aan uw ECID-bibliotheekimplementatie: discardtrackingServerECID. Wanneer deze config aan waar wordt geplaatst, leest de bibliotheek van de Bezoeker MID niet die door de eerste partij volgende server wordt geplaatst.

![](assets/itp-proposal-v1.png)

## Gebruik de methode appendVisitorIDsTo voor interdomeintracering (binnen de meerdere domeinen van uw eigen bedrijf)

Met deze functie kunt u de ECID van een bezoeker in verschillende domeinen delen wanneer browsers cookies van derden blokkeren. Om deze functie te gebruiken, moet u de dienst van identiteitskaart hebben uitgevoerd en de bron en bestemmingsdomeinen bezitten. Beschikbaar in VisitorAPI.js versie 1.7.0 of hoger (maar niet in versie 1.10.0).

**Ontwerp**

* Wanneer een bezoeker naar andere domeinen bladert, retourneert de bezoeker.appendVisitorIDsTo(url) een URL met de ECID die als queryparameter is toegevoegd.

   Gebruik deze URL om van het oorspronkelijke domein naar het doeldomein om te leiden.

* De code voor de id-service op het doeldomein extraheert de ECID van de URL in plaats van een aanvraag naar Adobe voor de id van die bezoeker te verzenden.

   Deze aanvraag bevat de cookie-id van een andere fabrikant, die in dit geval niet beschikbaar is.

* De de dienstcode van identiteitskaart op de bestemmingspagina gebruikt overgegaan ECID om de bezoeker te volgen.

   >[!NOTE]
   >Als de bestemmingspagina reeds ECID van vorige bezoeken heeft, dan wordt het besluit om het bestaande koekje te overschrijven-schrijven gecontroleerd door dit config overwriteCrossDomainMCIDAndAID. Zie [overwriteCrossDomainMCIDAndAID voor meer informatie over deze configuratie](/help/library/function-vars/overwrite-visitor-id.md).
   >
   >Zie de referentiepagina [appendVisitorIDsTo (Cross Domain Tracking)](/help/library/get-set/appendvisitorid.md) voor meer informatie over deze methode.
