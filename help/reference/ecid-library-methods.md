---
title: ECID-bibliotheekmethoden in een Safari ITP-wereld
description: Documentatie voor Adobe ECID-bibliotheek (ID Service).
exl-id: ac1d1ee1-2b5f-457a-a694-60bb4c960ae7
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 0%

---

# ECID-bibliotheekmethoden in een Safari ITP-wereld

>[!NOTE]
>
>Er zijn updates aangebracht die de meest recente wijzigingen in ITP weerspiegelen die op 12 november 2020 zijn gepubliceerd als onderdeel van de Big Sur OS-release.

Aangezien Safari het grensoverschrijdende volgen via ITP aanscherpt, moet Adobe beste praktijken voor bibliotheken handhaven die klanten evenals de privacy en de keus van de consument steunen.

Vanaf 10 november 2020 geldt voor alle ononderbroken cookies van de eerste partij die via de document.cookie-API zijn ingesteld, vaak ook wel &#39;client-side&#39; cookies genoemd, en voor cookies die via CNAME-implementaties van de eerste partij in Safari en mobiele iOS-browsers zijn ingesteld, een vervaldatum van maximaal zeven dagen. Cookies van andere bedrijven blijven geblokkeerd, zoals in eerdere versies van ITP is aangegeven. Lees voor meer informatie over ITP 2.1 en de impact van Adobe oplossingen [Safari ITP 2.1 Impact op klanten van Adobe Experience Cloud en Experience Platform](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac).

## Aan ITP gerelateerde wijzigingen, methoden en configuraties

Aangezien er extra methoden voor tekstspatiëring in Safari zijn gemaakt, worden deze toegevoegd als verwijzing naar deze pagina.

>[!NOTE]
>
>*ECID* = *MID* = *MCID* in alle onderstaande documentatie.

Zie hieronder voor inspanningen met betrekking tot ITP- en ECID-bibliotheekgebruik.

## Huidig gedrag van ECID-bibliotheek met ITP en Apple WebKit

ITP 2.1 belemmert de mogelijkheid om cookies aan de clientzijde te schrijven, wat de mogelijkheid om klanten nauwkeurige informatie over het bijhouden van bezoekers te verstrekken, beperkt. Als dusdanig, wordt de verandering geïntroduceerd in Adobe NAAM die servers controleert om Experience Cloud identiteitskaart (ECID) van de bezoeker op te slaan van een eerstepartijkoekje.

Deze wijziging is alleen nuttig voor ECID-klanten die een Analytics CNAME gebruiken in de context van de eerste partij. Als u een klant van de Analyse bent die momenteel geen CNAME, of zelfs een klant niet-Analytics gebruikt, bent u nog verkiesbaar voor een verslag CNAME. Neem contact op met de klantenservice of uw accountvertegenwoordiger om het registratieproces voor een [CNAME](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-first-party.html).

Voer een upgrade uit naar de ECID-bibliotheek v.4.3.0 + om deze wijziging te benutten.

Hieronder wordt beschreven hoe de ECID-bibliotheek zich gedraagt met ITP 2.1 en de laatste wijzigingen die Apple heeft aangebracht als onderdeel van de Big Sur-release

**Ontwerp**

Zodra een identiteitskaart- verzoek wordt ingediend aan demdex.net en een ECID wordt teruggewonnen, als een het volgen server in uw ECID bibliotheek wordt geplaatst, wordt een identiteitskaart- verzoek gemaakt aan het domein van de klant. Dit eindpunt leest ecid param van het vraagkoord, en plaatst een nieuw [koekje](/help/introduction/cookies.md) die uitsluitend de ECID omvat en een vervaldatum die twee jaar in de toekomst geldt. Telkens als dit eindpunt op deze manier wordt geroepen, `s_ecid` cookie wordt herschreven met een vervaldatum van twee jaar vanaf het tijdstip van die oproep. De ECID-bibliotheek moet worden bijgewerkt naar versie 4.3.0, zodat de waarde van dit cookie kan worden opgehaald.

>[!IMPORTANT]
>
>Als onderdeel van de Big Sur-updates kan een `s_ecid` cookies die via CNAME worden ingesteld, worden ook zeven dagen bewaard.

Deze nieuwe `s_ecid` cookie heeft dezelfde status als de AMCV-cookie. Als het ecid uit de `s_ecid` cookie, wordt demdex altijd direct aangeroepen om de laatste status van de optie om te weigeren voor die id op te halen en in het AMCV-cookie opgeslagen.

Als uw consument via deze optie heeft afgezien van Analytics tracking [methode](https://experienceleague.adobe.com/docs/analytics/implementation/js/opt-out.html), `s_ecid` cookie wordt verwijderd.

De naam van de trackingserver moet worden opgegeven bij het initialiseren van de bibliotheek met `trackingServer` of `trackingServerSecure`. Dit moet overeenkomen met de `trackingServer` config in de Analytics vormt.

Als u ervoor kiest om deze methode niet te gebruiken, voegt u de volgende config toe aan uw ECID-bibliotheekimplementatie: `discardtrackingServerECID`. Wanneer deze config aan waar wordt geplaatst, leest de bibliotheek van de Bezoeker MID niet die door de eerste partij volgende server wordt geplaatst.

![](assets/itp-proposal-v1.png)

## Gebruik de methode appendVisitorIDsTo voor interdomeintracering (binnen de meerdere domeinen van uw eigen bedrijf)

Met deze functie kunt u de ECID van een bezoeker in verschillende domeinen delen wanneer browsers cookies van derden blokkeren. Om deze functie te gebruiken, moet u de dienst van identiteitskaart hebben uitgevoerd en de bron en bestemmingsdomeinen bezitten. Beschikbaar in VisitorAPI.js versie 1.7.0 of hoger (maar niet in versie 1.10.0).

**Ontwerp**

* Wanneer een bezoeker naar andere domeinen bladert, retourneert de bezoeker.appendVisitorIDsTo(url) een URL met de ECID die als queryparameter is toegevoegd.

   Gebruik deze URL om van het oorspronkelijke domein naar het doeldomein om te leiden.

* De de dienstcode van identiteitskaart op het bestemmingsdomein haalt ECID uit URL in plaats van het verzenden van een verzoek naar Adobe voor identiteitskaart van die bezoeker.

   Deze aanvraag bevat de cookie-id van een andere fabrikant, die in dit geval niet beschikbaar is.

* De de dienstcode van identiteitskaart op de bestemmingspagina gebruikt overgegaan ECID om de bezoeker te volgen.

   >[!NOTE]
   >Als de bestemmingspagina reeds ECID van vorige bezoeken heeft, dan wordt het besluit om het bestaande koekje te overschrijven-schrijven gecontroleerd door dit config overwriteCrossDomainMCIDAndAID. Voor details over dit config, zie [overwriteCrossDomainMCIDAndAID](/help/library/function-vars/overwrite-visitor-id.md).
   >
   >Voor meer informatie over deze methode raadpleegt u de [appendVisitorIDsTo (Cross Domain Tracking)](/help/library/get-set/appendvisitorid.md) referentiepagina.
