---
description: Steekproef gebruiksgevallen en oplossingen om de Opt-in dienst te beheren.
title: Gebruiksscenario's openen
exl-id: 4c57685f-40b7-4af4-8527-3c2795586f0f
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# Gebruiksscenario&#39;s openen {#opt-in-use-cases}

Steekproef gebruiksgevallen en oplossingen om de Opt-in dienst te beheren.

## Tips en probleemoplossing {#section-5c566366410f4a8f89eca0d3f556d99f}

* Bezoeker JS initialiseert is synchroon en wordt uitgevoerd tijdens het laden van de pagina. Als u met een CMP of toestemmingenpersistentie omzet die een hoge latentie heeft, zou het verkieslijk kunnen zijn om de asynchrone die functies te gebruiken in [ worden beschreven Opt-binnen Opstelling ](../../implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047).
* Inschakelen is een implementatie per domein. Het zal geen interdomeinimplementaties behandelen.
* Als u aanroepen van derden voor een specifieke bibliotheek wilt uitschakelen, moet u die voorkeur in elke bibliotheek afzonderlijk configureren.

## Opt-in-scenario&#39;s {#section-1178053c065c430bba26f82ef383a71c}

Deze gebruiksgevallen zijn voorbeelden van ideeën voor het gebruik van de Option-in-service.

<table id="table_83C85343611344D8A8315157C1B4240F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Vereiste </th> 
   <th colname="col2" class="entry"> Oplossingen </th> 
   <th colname="col3" class="entry"> Gevolgen </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Analyses kunnen alleen worden verzameld in de toestand vóór toestemming, maar alle andere bibliotheken kunnen pas worden geladen als er toestemming is gegeven </p> </td> 
   <td colname="col2"> <p>Inschakelen gebruiken om de categorie Analytics in de toestand vóór de toestemming in te schakelen </p> </td> 
   <td colname="col3"> <p>Analytics gebruikt de Analytics-id in plaats van ECID in de verzameling vóór toestemming. Zodra ECID is goedgekeurd, wordt een nieuwe id gebruikt en ontvangt de bezoeker een ECID die kan worden gebruikt voor activering en integratie. </p> <p>Verwacht wordt dat de bezoeker in de toestand vóór/na de toestemming versnippert. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>De meting van de eerste partij is oké om in pre-toestemmingsstaat te verzamelen. Alle andere soorten gegevensgebruik zijn voorkomen totdat de toestemming is ontvangen. </p> </td> 
   <td colname="col2"> <p>Gebruik Inschakelen om de status Analytics + ECID-bibliotheken in te schakelen voordat toestemming wordt verleend. </p> <p>Voeg het config-bestand "disablethirdpartycookies" toe aan de ECID-bibliotheek om cookie + ID-syncs van derden in de pre-toestemmingsstatus te blokkeren </p> </td> 
   <td colname="col3"> <p>Aanroep van Adobe Demdex wordt geactiveerd voor het ophalen van ECID, maar er zijn geen demdex-cookie, andere cookie van derden of ID-syncs aanwezig. </p> <p>Houdt constant bezoeker in pre/post toestemmingsstaat voor Analytics. Verzameling in de toestand vóór de instemming zal worden gekoppeld aan het verzamelen van gegevens na de instemming. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Metingen van de eerste partij plus het richten is aanvaardbaar in een staat van de pre-instemming. Alle andere soorten gegevensgebruik zijn voorkomen totdat de toestemming is ontvangen. </p> </td> 
   <td colname="col2"> <p>Gebruik Opt-in om Analytics + ECID + Target libraries in de pre-toestemmingsstaat toe te laten. </p> <p>Voeg <span class="codeph"> isablethirdpartycookies </span> config aan de bibliotheek ECID toe om derdekoekjes + de syncs van identiteitskaart in pre-toestemmingsstaat te blokkeren. Markering verwijderen in toestand na toestemming. </p> </td> 
   <td colname="col3"> <p>Aanroep van Adobe Demdex wordt geactiveerd voor het ophalen van ECID, maar er zijn geen demdex-cookie, cookie van andere derden of ID-syncs aanwezig. </p> <p>Houdt constant bezoeker in pre/post toestemmingsstaat voor eerste-partijoplossingen. Verzameling in de toestand vóór de instemming zal worden gekoppeld aan het verzamelen van gegevens na de instemming. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Er mogen geen cookies worden ingesteld in een status voorafgaand aan de toestemming </p> </td> 
   <td colname="col2"> <p>Gebruik Inschakelen om alle bibliotheken te blokkeren tijdens het laden tot er toestemming is ontvangen </p> </td> 
   <td colname="col3"> <p>De implementatie is zoals verwacht en alle bibliotheken, inclusief ECID, worden na de toestemming in de juiste volgorde geladen. </p> <p>Gegevensverlies voor klanten die nooit toestemming geven om te worden getraceerd. </p> </td> 
  </tr> 
 </tbody> 
</table>
