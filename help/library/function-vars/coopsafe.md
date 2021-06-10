---
description: Een optionele, Booleaanse configuratie die bepaalt of de id-service gegevens naar de Adobe Experience Cloud Device Co-op verzendt (of niet verzendt).
keywords: ID-service
title: isCoopSafe
exl-id: 827f7819-9f95-4e8d-90c3-dcf86b67715b
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 2%

---

# isCoopSafe{#iscoopsafe}

Een optionele, Booleaanse configuratie die bepaalt of de id-service gegevens naar de Adobe Experience Cloud Device Co-op verzendt (of niet verzendt).

Inhoud:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-4883eda6beb8437182bcc82bb58fae41" format="dita" scope="local"> Vereisten </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-d18af2b903f248e18ae8108aaf0a8ebb" format="dita" scope="local"> Gevallen gebruiken  </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-952f56724a2b4d349340e26fbaf33ddd" format="dita" scope="local"> Syntaxis en codevoorbeeld  </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-fcd441933506493faefaa6b51f194a17" format="dita" scope="local"> Parameters POST gebeurtenisaanroep  </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-9281c39c8b6249d7864100b5cbca7dc6" format="dita" scope="local"> Post-Instantiatie-API's  </a> </li> 
</ul>

## Vereisten {#section-4883eda6beb8437182bcc82bb58fae41}

Als u `isCoopSafe` wilt gebruiken, moet u:

* Gebruik ID-servicecode versie 2.4 of hoger.
* Neem deel aan [Experience Cloud Device Co-op](https://experienceleague.adobe.com/docs/device-co-op/using/about/overview.html). De perspectiefleden van coop zouden deze documentatie ook moeten herzien om te bepalen als `isCoopSafe` mogelijke zorgen over hoe de gegevens worden gebruikt om de apparatengrafiek tot stand te brengen richt.

* Werk samen met uw [!DNL Adobe]-consultant om een whitelist- of een blacklist-vlag in te stellen op uw Device Co-op-account. Er is geen zelfbedieningspad om deze markeringen in te schakelen.

## Gevallen {#section-d18af2b903f248e18ae8108aaf0a8ebb} gebruiken

`isCoopSafe` helpt twee gebruiksgevallen oplossen die verband houden met gegevensverzameling door huidige of toekomstige leden van de Device Co-op. Deze gebruiksgevallen hebben betrekking op de manier waarop bezoekersgegevens van de site worden doorgegeven aan de copop van het apparaat om de apparaatgrafiek samen te stellen. In de volgende tabel wordt beschreven hoe `isCoopSafe` met deze gebruiksgevallen werkt om gegevens te blokkeren of naar de apparaatgrafiek te verzenden

<table id="table_A24C63D2A21F47EDBAC8FA5E7BE888D8"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Gebruiksscenario </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Geverifieerde bezoekers</b> </p> </td> 
   <td colname="col2"> <p>Voeg <span class="codeph"> isCoopSafe </span> aan uw de dienstcode van identiteitskaart toe om te controleren hoe de gegevens voor voor authentiek verklaarde bezoekers die termijn-van-gebruikovereenkomsten hebben of niet hebben goedgekeurd door de Co-op van het Apparaat wordt gebruikt om de apparatengrafiek te bouwen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>DIL op sites van derden</b> </p> </td> 
   <td colname="col2"> <p>Voeg <span class="codeph"> isCoopSafe </span> aan uw de dienstcode van identiteitskaart voor gebruik op derdeplaatsen toe waar u: </p> <p> 
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

* `isCoopSafe: true`: De door een mobiele SDK of website verzamelde bezoekersgegevens  ** kunnen worden gebruikt om de apparaatgrafiek te maken.

* `isCoopSafe: false`: De door een mobiele SDK of website verzamelde bezoekersgegevens  ** kunnen niet worden gebruikt om de apparaatgrafiek te maken.

**Codevoorbeeld**

Stel dit in wanneer uw ID-servicecode het volgende doet:

```js
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here",{ 
     ... 
     isCoopSafe: true 
});
```

## Parameters {#section-fcd441933506493faefaa6b51f194a17} van de POST van de Gebeurtenis

Afhankelijk van de vlag u ( `true` of `false`) plaatst, vertaalt de dienst van identiteitskaart `isCoopSafe` in deze POST parameters en verzendt hen naar [!DNL Adobe] in een gebeurtenisvraag:

* `d_coop_safe=1`
* `d_coop_unsafe=1`

De parameters van de POST vertellen [!DNL Experience Cloud] Apparaatcoop als het gebruikersgegevens in de apparatengrafiek kan of niet kan omvatten. In de onderstaande tabel wordt de relatie gedefinieerd tussen de Booleaanse markeringen `isCoopSafe` en de parameters van de POST die worden doorgegeven aan een gebeurtenisaanroep. Als u `isCoopSafe` niet gebruikt, worden geen van beide overgegaan in een gebeurtenisvraag.

<table id="table_0A544534CA904F4D9836A34B8C1EACBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Configuratiestatus </th> 
   <th colname="col2" class="entry"> Parameter POST </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe: true  </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> d_coop_safe=1  </span> </p> <p>De interface van het Apparaat kan bezoekersgegevens gebruiken helpen de apparatengrafiek bouwen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe: false  </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> d_coop_unsafe=1  </span> </p> <p>De interface van het Apparaat kan bezoekersgegevens niet gebruiken helpen de apparatengrafiek bouwen. </p> </td> 
  </tr> 
 </tbody> 
</table>

## API&#39;s voor nainstantiëring {#section-9281c39c8b6249d7864100b5cbca7dc6}

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
   <td colname="col1"> <p> <span class="codeph"> bezoeker.setAsCoopSafe();  </span> </p> </td> 
   <td colname="col2"> <p>Stelt de parameter POST <span class="codeph"> d_coop_safe=1 </span> in alle volgende gebeurtenisaanroepen in. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> bezoeker.setAsCoopUnsafe();  </span> </p> </td> 
   <td colname="col2"> <p>Stelt de parameter POST <span class="codeph"> d_coop_unsafe=1 </span> in alle volgende gebeurtenisaanroepen in. </p> </td> 
  </tr> 
 </tbody> 
</table>

<!--
Wiki page https://wiki.corp.adobe.com/x/RCfFTg
-->

>[!MORELIKETHIS]
>
>* [DIL isCoopSafe](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/class-level-dil-methods/dil-coopsafe.html)

