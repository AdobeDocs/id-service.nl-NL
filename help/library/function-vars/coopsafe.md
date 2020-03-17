---
description: Een optionele, Booleaanse configuratie die bepaalt of de id-service gegevens verzendt (of niet verzendt) naar de Adobe Experience Cloud Device Co-op.
keywords: ID Service
seo-description: Een optionele, Booleaanse configuratie die bepaalt of de id-service gegevens verzendt (of niet verzendt) naar de Adobe Experience Cloud Device Co-op.
seo-title: isCoopSafe
title: isCoopSafe
uuid: 4dfa1f35-0a88-48d1-9484-d88cb53ad461
translation-type: tm+mt
source-git-commit: c4c0b791230422f17292b72fd45ba5689a60adae

---


# isCoopSafe{#iscoopsafe}

Een optionele, Booleaanse configuratie die bepaalt of de id-service gegevens verzendt (of niet verzendt) naar de Adobe Experience Cloud Device Co-op.

Inhoud:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-4883eda6beb8437182bcc82bb58fae41" format="dita" scope="local"> Vereisten </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-d18af2b903f248e18ae8108aaf0a8ebb" format="dita" scope="local"> Gevallen gebruiken </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-952f56724a2b4d349340e26fbaf33ddd" format="dita" scope="local"> Syntaxis en codevoorbeeld </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-fcd441933506493faefaa6b51f194a17" format="dita" scope="local"> POST-parameters voor gebeurtenisaanroep </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-9281c39c8b6249d7864100b5cbca7dc6" format="dita" scope="local"> Post-Instantiatie-API's </a> </li> 
</ul>

## Vereisten {#section-4883eda6beb8437182bcc82bb58fae41}

Als u `isCoopSafe` het volgende wilt gebruiken:

* Gebruik ID-servicecode versie 2.4 of hoger.
* Neem deel aan de [Experience Cloud Device Co-op](https://marketing.adobe.com/resources/help/en_US/mcdc/). De perspectiefleden van coop zouden deze documentatie ook moeten herzien om te bepalen als `isCoopSafe` mogelijke bezorgdheid over hoe de gegevens worden gebruikt om de apparatengrafiek tot stand te brengen.

* Werk samen met uw [!DNL Adobe] consultant om een whitelist- of een blacklist-vlag in te stellen op uw Co-op-account voor apparaten. Er is geen zelfbedieningspad om deze markeringen in te schakelen.

## Gevallen gebruiken {#section-d18af2b903f248e18ae8108aaf0a8ebb}

`isCoopSafe` helpt twee gebruiksgevallen oplossen die verband houden met gegevensverzameling door huidige of toekomstige leden van de Device Co-op. Deze gebruiksgevallen hebben betrekking op de manier waarop bezoekersgegevens van de site worden doorgegeven aan de copop van het apparaat om de apparaatgrafiek samen te stellen. In de volgende tabel wordt beschreven hoe u met deze gebruiksgevallen gegevens kunt blokkeren of verzenden naar de apparaatgrafiek `isCoopSafe`

<table id="table_A24C63D2A21F47EDBAC8FA5E7BE888D8"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Hoofdletters gebruiken </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Geverifieerde bezoekers</b> </p> </td> 
   <td colname="col2"> <p>Voeg <span class="codeph"> isCoopSafe </span> aan uw de dienstcode van identiteitskaart toe om te controleren hoe de gegevens voor voor authentiek verklaarde bezoekers die termijn-van-gebruikovereenkomsten hebben of niet hebben goedgekeurd door Co-op van het Apparaat wordt gebruikt om de apparatengrafiek te bouwen. </p> </td> 
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

* `isCoopSafe: true`: De door een mobiele SDK of website verzamelde bezoekersgegevens *kunnen* worden gebruikt om de apparaatgrafiek te maken.

* `isCoopSafe: false`: Bezoekersgegevens die zijn verzameld door een mobiele SDK of website *kunnen niet* worden gebruikt om de apparaatgrafiek samen te stellen.

**Codevoorbeeld**

Stel dit in wanneer uw ID-servicecode het volgende doet:

```js
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here",{ 
     ... 
     isCoopSafe: true 
});
```

## POST-parameters voor gebeurtenisaanroep {#section-fcd441933506493faefaa6b51f194a17}

Afhankelijk van de vlag u ( `true` of `false`) plaatst, vertaalt de dienst van identiteitskaart `isCoopSafe` in deze POST parameters en verzendt hen naar [!DNL Adobe] in een gebeurtenisvraag:

* `d_coop_safe=1`
* `d_coop_unsafe=1`

De POST-parameters vertellen de [!DNL Experience Cloud] apparaatcoop of er gebruikersgegevens kunnen of kunnen worden opgenomen in de apparaatgrafiek. In de onderstaande tabel wordt de relatie gedefinieerd tussen de `isCoopSafe` Booleaanse markeringen en de POST-parameters die bij een gebeurtenisaanroep worden doorgegeven. Als u niet gebruikt `isCoopSafe`, worden geen van beide overgegaan in een gebeurtenisvraag.

<table id="table_0A544534CA904F4D9836A34B8C1EACBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Configuratiestatus </th> 
   <th colname="col2" class="entry"> POST-parameter </th> 
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

Met deze API&#39;s kunt u de `isCoopSafe` status overschrijven. Deze zijn nodig omdat u hiermee de postinstantiërings- of postaanmeldingsstatus van een bezoeker kunt wijzigen op een site of in een app van één pagina waar de pagina niet wordt vernieuwd. U moet deze API&#39;s bijvoorbeeld aanroepen als een gebruiker zich op uw site of app aanmeldt en later een gebruiksbeleid accepteert waarmee de Device Co-op hun gegevens kan gebruiken.

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
   <td colname="col2"> <p>Stelt POST-parameter <span class="codeph"> d_coop_safe=1 </span> in alle volgende gebeurtenisaanroepen in. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> bezoeker.setAsCoopUnsafe(); </span> </p> </td> 
   <td colname="col2"> <p>Stelt POST-parameter <span class="codeph"> d_coop_unsafe=1 in </span> alle volgende gebeurtenisaanroepen. </p> </td> 
  </tr> 
 </tbody> 
</table>

<!--
Wiki page https://wiki.corp.adobe.com/x/RCfFTg
-->

>[!MORELIKETHIS]
>
>* [DIL isCoopSafe](https://marketing.adobe.com/resources/help/en_US/aam/dil-coopsafe.html)

