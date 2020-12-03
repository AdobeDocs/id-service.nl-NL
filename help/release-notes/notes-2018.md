---
description: De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van de Experience Cloud voor 2018.
keywords: ID Service
seo-description: De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van de Experience Cloud voor 2018.
seo-title: Opmerkingen bij de release 2018
title: Opmerkingen bij de release 2018
uuid: 771b5b11-a8e3-464c-b65e-b15135584ace
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---


# 2018 Release Notes {#release-notes}

De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van de Experience Cloud voor 2018.

## Versie 3.3 {#section-3202c8d5457a45a5b5f4b4c838d44de3}

<table id="table_201417BD540E4EE69911AABE9BF77509"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Objectbeschrijving </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Meer beveiliging voor AMCV-cookies </p> </td> 
   <td colname="col2"> <p>Tijdens een interne beveiligingsscan werd ontdekt dat bij gebruik van de DTM-bibliotheek cookies die voor sessiebeheer worden gebruikt, geen juiste kenmerken kunnen opgeven. Dit kan ertoe leiden dat cookie-informatie onbedoeld wordt gedeeld. Om dit op te lossen, hebben wij een configuratie geïntroduceerd die de Klant toestaat om het koekje van AMCV als veilig te plaatsen. Zie <a href="/help/library/function-vars/securecookie.md" format="https" scope="external"> SecureCookie</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Versie 3.2 {#section-ae2fee1c152e405faa4eb395f960e2f6}

<table id="table_6546F5C74E4742E4B5E9793BCEAB66FA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Objectbeschrijving </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Meer beveiliging voor AMCV-cookies </p> </td> 
   <td colname="col2"> <p>Tijdens een interne beveiligingsscan werd ontdekt dat bij gebruik van de DTM-bibliotheek cookies die voor sessiebeheer worden gebruikt, geen juiste kenmerken kunnen opgeven. Dit kan ertoe leiden dat cookie-informatie onbedoeld wordt gedeeld. Om dit op te lossen, hebben wij een configuratie geïntroduceerd die de Klant toestaat om het koekje van AMCV als veilig te plaatsen. Zie secureCookie. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Integratiecode en id moeten getallen of niet-lege tekenreeksen zijn </p> </td> 
   <td colname="col2"> <p>Probleem verholpen met valideren van "setCustomerIDs" wanneer gegevens een integratie "code" of "id" bevatten die noch een getal, noch een niet-lege tekenreeks is. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> ECID JS is beschikbaar in Public Git repo </td> 
   <td colname="col2"> ECID JS is nu beschikbaar in Public Git repo voor alle klanten van Experience Cloud op https://github.com/Adobe-Marketing-Cloud/id-service/releases. </td> 
  </tr> 
 </tbody> 
</table>

## Versie 3.1.2 {#section-3cba186f74fe4f2186a9ca2e5e0a2514}

<table id="table_9FA4E20C996746A2A4219C9A0F759AD1"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Objectbeschrijving </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Onrealistische spiraal in het unieke aantal bezoekers </p> </td> 
   <td colname="col2"> <p>Met de release van Experience Cloud Identity Service 3.1.0 hebben we een probleem gevonden dat een onrealistisch beeld creëerde van het aantal unieke bezoekers toen deze versie werd geïmplementeerd. Dit gedrag wordt alleen getoond met de nieuwste versie van ECID, v3.1.0, en als een gebruiker de optie "Alleen huidige website toestaan" heeft geselecteerd in de privacy-instellingen van een Safari-browser. Versie 3.1.2 verhelpt dit probleem. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Versie 3.1.0 {#section-a20c8278bf9643018965330415091e53}

>[!NOTE]
>
>Het wordt aanbevolen om zo snel mogelijk een upgrade uit te voeren van versie 3.1.0 naar de nieuwste versie. Zie de beschrijving van versie 3.1.2. De nieuwste bundel is beschikbaar in Adobe Experience Platform Launch, DTM en AppMeasurement.

<table id="table_512039AFC4D34038B8F116B71EEEE7F6"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Objectbeschrijving </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Cookie ingesteld op onjuist domein </p> </td> 
   <td colname="col2"> <p>We hebben een fout verholpen waarbij temp Visitor-cookie een cookie instelde in het ‘standaard’ cookie domein in plaats van deze in te stellen in het domein dat wordt verschaft in de config (initConfig). </p> </td> 
  </tr> 
 </tbody> 
</table>

## Versie 3.0 {#section-5fcaef66e8b343238abeb10048dc5747}

<table id="table_7E9224D6CC924A2DB5119171C9DC5443"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Objectbeschrijving </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Thread levert meerdere id-synchronisatieaanvragen op </p> </td> 
   <td colname="col2"> <p><b>Iframe</b> </p> <p>Voor klanten die meerdere id-synchronisaties uitvoeren, wordt de interface in sommige gevallen geblokkeerd vanwege continue CPU-berekeningen. We introduceren thread die ervoor zorgt dat de verzoeken voor id-synchronisatie met telkens 100 msec worden gescheiden. </p> <p>Deze wijziging verbetert de prestaties voor klanten die Visitor 2.3.0+ en DIL 6.10+ gebruiken. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Toegevoegde de capaciteit om derdevraag onbruikbaar te maken </td> 
   <td colname="col2"> <p><b>JavaScript - 3.0.0</b> </p> <p>Adobe noemde de volgende configuraties anders om voor het onbruikbaar maken van vraag van de derdesynchronisatie toe te staan. </p> <p>idSyncDisableSyncs to disableIdSyncs </p> <p>idSyncDisable3rdPartySyncing omThirdPartyCookies uit te schakelen </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Ondersteuning voor Internet Explorer </p> </td> 
   <td colname="col2"> <p>De dienst van identiteitskaart steunt Internet Explorer 6, 7, 8, en 9 niet meer. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Bijwerken naar getInstance-documentatie </p> </td> 
   <td colname="col2"> <p>Er is een waarschuwing toegevoegd aan de functie Visitor over het niet instantiëren van deze functie met var bezoeker = new Visitor. </p> </td> 
  </tr> 
 </tbody> 
</table>

