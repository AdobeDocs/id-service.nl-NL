---
description: Een optionele, Booleaanse configuratie die bepaalt of de id-service gegevens naar de Adobe Experience Cloud Device Co-op verzendt (of niet verzendt).
keywords: ID-service
title: isCoopSafe
exl-id: 827f7819-9f95-4e8d-90c3-dcf86b67715b
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# isCoopSafe{#iscoopsafe}

Een optionele, Booleaanse configuratie die bepaalt of de id-service gegevens naar de Adobe Experience Cloud Device Co-op verzendt (of niet verzendt).

Inhoud:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-4883eda6beb8437182bcc82bb58fae41" format="dita" scope="local"> Vereisten </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-d18af2b903f248e18ae8108aaf0a8ebb" format="dita" scope="local"> Gevallen gebruiken </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-952f56724a2b4d349340e26fbaf33ddd" format="dita" scope="local"> Syntaxis en codevoorbeeld </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-fcd441933506493faefaa6b51f194a17" format="dita" scope="local"> Parameters van de POST Gebeurtenisaanroep </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-9281c39c8b6249d7864100b5cbca7dc6" format="dita" scope="local"> Post-Instantiation API's </a> </li> 
</ul>

## Vereisten {#section-4883eda6beb8437182bcc82bb58fae41}

Als u `isCoopSafe` wilt gebruiken, moet u:

* Gebruik ID-servicecode versie 2.4 of hoger.
* Neem deel aan [ Co-op van het Apparaat van het Experience Cloud ](https://experienceleague.adobe.com/docs/device-co-op/using/about/overview.html?lang=nl-NL). Prospectieve copop leden zouden deze documentatie ook moeten herzien om te bepalen als `isCoopSafe` mogelijke zorgen over hoe de gegevens worden gebruikt om de apparatengrafiek tot stand te brengen richt.

* Werk samen met uw [!DNL Adobe] -consultant om een whitelist- of een blacklist-vlag in te stellen op uw Device Co-op-account. Er is geen zelfbedieningspad om deze markeringen in te schakelen.

## Gebruiksscenario’s {#section-d18af2b903f248e18ae8108aaf0a8ebb}

Met `isCoopSafe` kunt u twee gebruiksgevallen oplossen die te maken hebben met gegevensverzameling door huidige of toekomstige leden van de Device Co-op. Deze gebruiksgevallen hebben betrekking op de manier waarop bezoekersgegevens van de site worden doorgegeven aan de copop van het apparaat om de apparaatgrafiek samen te stellen. In de volgende tabel wordt beschreven hoe `isCoopSafe` met deze gebruiksgevallen werkt om gegevens te blokkeren of naar de apparaatgrafiek te verzenden

<table id="table_A24C63D2A21F47EDBAC8FA5E7BE888D8"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Hoofdletters gebruiken </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b> Voor authentiek verklaarde Bezoekers </b> </p> </td> 
   <td colname="col2"> <p>Voeg <span class="codeph"> isCoopSafe </span> toe aan de id-servicecode om te bepalen hoe gegevens voor geverifieerde bezoekers die gebruiksovereenkomsten hebben of niet hebben geaccepteerd, door de apparaatcoop worden gebruikt om de apparaatgrafiek te maken. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> DIL op de Plaatsen van de Derde </b> </p> </td> 
   <td colname="col2"> <p>Voeg <span class="codeph"> isCoopSafe </span> toe aan uw id-servicecode voor gebruik op sites van derden waar u: </p> <p> 
     <ul id="ul_C27BB26510314834A2A7CD99D46DA4AC"> 
      <li id="li_4E6AE574F18646F09C0CF4553EEA1A9E">Kan niet garanderen dat geregistreerde bezoekers gebruiksovereenkomsten hebben of niet hebben geaccepteerd. </li> 
      <li id="li_26D0561BF32B4278B0A6B5082C17FED8">Behoefte om te controleren hoe dat gegeven door Co-op van het Apparaat wordt gebruikt om de apparatengrafiek te bouwen. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Syntaxis en codevoorbeeld {#section-952f56724a2b4d349340e26fbaf33ddd}

**Syntaxis:** `isCoopSafe: true | false`

De opties Van Boole bepalen hoe de klantengegevens door Co-op van het Apparaat worden gebruikt of niet.

* `isCoopSafe: true`: De gegevens van de bezoeker die door een mobiele SDK of website *worden verzameld kunnen* worden gebruikt helpen de apparatengrafiek bouwen.

* `isCoopSafe: false`: De gegevens van de bezoeker die door een mobiele SDK of website *worden verzameld kunnen* niet worden gebruikt helpen de apparatengrafiek bouwen.

**Steekproef van de Code**

Stel dit in wanneer uw ID-servicecode het volgende doet:

```js
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here",{ 
     ... 
     isCoopSafe: true 
});
```

## Parameters POST gebeurtenisaanroep {#section-fcd441933506493faefaa6b51f194a17}

Afhankelijk van de markering die u instelt ( `true` of `false` ), zet de id-service `isCoopSafe` om in deze POST-parameters en verzendt deze naar [!DNL Adobe] in een gebeurtenisaanroep:

* `d_coop_safe=1`
* `d_coop_unsafe=1`

De parameters van de POST vertellen de [!DNL Experience Cloud] Apparaatcoop als het gebruikersgegevens in de apparatengrafiek kan of niet kan omvatten. In de onderstaande tabel wordt de relatie gedefinieerd tussen de vlaggen van `isCoopSafe` Boolean en de parameters van de POST die bij een gebeurtenisaanroep worden doorgegeven. Als u `isCoopSafe` niet gebruikt, worden geen van beide doorgegeven in een gebeurtenisaanroep.

<table id="table_0A544534CA904F4D9836A34B8C1EACBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Configuratiestatus </th> 
   <th colname="col2" class="entry"> Parameter POST </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe: true </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> d_coop_safe=1 </span> </p> <p>De interface van het Apparaat kan bezoekersgegevens gebruiken helpen de apparatengrafiek bouwen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe: false </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> d_coop_unsafe=1 </span> </p> <p>De interface van het Apparaat kan bezoekersgegevens niet gebruiken helpen de apparatengrafiek bouwen. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Post-Instantiatie-API&#39;s {#section-9281c39c8b6249d7864100b5cbca7dc6}

Met deze API&#39;s kunt u de status `isCoopSafe` overschrijven. Deze zijn nodig omdat u hiermee de postinstantiërings- of postaanmeldingsstatus van een bezoeker kunt wijzigen op een site of in een app van één pagina waar de pagina niet wordt vernieuwd. U moet deze API&#39;s bijvoorbeeld aanroepen als een gebruiker zich op uw site of app aanmeldt en later een gebruiksbeleid accepteert waarmee de Device Co-op hun gegevens kan gebruiken.

<table id="table_BAA96B1F82BE48C3A61A1AF1367BA45C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> API </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> bezoeker.setAsCoopSafe(); </span> </p> </td> 
   <td colname="col2"> <p>Stelt de parameter POST <span class="codeph"> d_coop_safe=1 </span> in voor alle volgende gebeurtenisaanroepen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> bezoeker.setAsCoopUnsafe(); </span> </p> </td> 
   <td colname="col2"> <p>Stelt de parameter POST <span class="codeph"> d_coop_unsafe=1 </span> in voor alle volgende gebeurtenisaanroepen. </p> </td> 
  </tr> 
 </tbody> 
</table>

<!--
Wiki page https://wiki.corp.adobe.com/x/RCfFTg
-->

>[!MORELIKETHIS]
>
>* [ DIL isCoopSafe ](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/class-level-dil-methods/dil-coopsafe.html)
