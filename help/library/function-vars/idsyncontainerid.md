---
description: Deze eigenschap stelt de gegevensbroncontainer-id in die u voor id-syncs wilt gebruiken.
keywords: ID-service
title: idSyncContainerID
exl-id: 6c4cd41b-902b-4872-8c3f-475a834b76f4
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# idSyncContainerID{#idsynccontainerid}

Deze eigenschap stelt de gegevensbroncontainer-id in die u voor id-syncs wilt gebruiken.

Inhoud:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-b0c50732b1c84bed8616e82e8e83d58c" format="dita" scope="local"> Syntaxis en codevoorbeeld </a> </li> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-6aed44fbe9d6401a8f912cb0d98339a7" format="dita" scope="local"> Wat zijn containers en wanneer zou ik dit gebruiken? </a> </li> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-f283cb69c8de4348b5316cc4e02a3e9e" format="dita" scope="local"> Container-id's instellen wanneer u DIL en BezoekerAPI.js gebruikt </a> </li> 
</ul>

## Syntaxis en codevoorbeeld {#section-b0c50732b1c84bed8616e82e8e83d58c}

**Syntaxis:** ` idSyncContainerID: *` waarde van containeridentiteitskaart `*`

**Steekproef van de Code:**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Set container ID 
   idSyncContainerID:80 
});
```

## Wat zijn containers en wanneer zou ik dit gebruiken? {#section-6aed44fbe9d6401a8f912cb0d98339a7}

**Containers**

Containers zijn objecten die zijn gemaakt door [!DNL Audience Manager] . Hoewel ze niet extern toegankelijk zijn, worden in deze container alle gegevensbronnen weergegeven die:

* Deze bestanden zijn beschikbaar voor u, maar worden niet gebruikt voor het synchroniseren van id&#39;s.
* Wordt gebruikt voor id-synchronisatie.

Zelfs als u geen [!DNL Audience Manager] klant bent, heeft uw account deze containers als u id&#39;s met verschillende gegevensbronnen op verschillende pagina&#39;s in uw domein uitwisselt. Dit komt omdat [!DNL Audience Manager] de technologie en de achterste-eindfunctionaliteit verstrekt die identiteitskaart synchronisatie toelaat.

**Gevallen van het Gebruik**

Afhankelijk van uw situatie, kunt u deze configuratie aan uw de dienstcode van identiteitskaart al dan niet moeten toevoegen.

<table id="table_48621F343C7F4760A75F6BCC2DB2DA20"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Voorwaarde </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b> niet nodig </b> </p> </td> 
   <td colname="col2"> <p>U hoeft deze configuratie niet te gebruiken als: </p> <p> 
     <ul id="ul_4D6F794CD65C43D0BEFBA6F5DE420C2E"> 
      <li id="li_0F048A6AC7BE4450AFA1B20B1AC25808">U gebruikt de id-service met een <span class="keyword"> Experience Cloud </span> -oplossing en voert geen id-syncs uit met andere gegevensbronnen. In dit geval heeft uw account een standaardcontainer met ID 0 en is geen actie vereist. </li> 
      <li id="li_5657D64D9406407D9B4DB7D8BE4F8EE4">Al uw gegevensbronnen bevinden zich in één container. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> nodig </b> </p> </td> 
   <td colname="col2"> <p>U moet deze configuratie gebruiken wanneer elk van deze voorwaarden van toepassing zijn: </p> <p> 
     <ul id="ul_9AFD14FC5A2745F7BD7BE7B64545DA62"> 
      <li id="li_04F0EFBBD71B43608CAAA7E7409D33FE">U gebruikt <span class="keyword"> Audience Manager </span> niet. </li> 
      <li id="li_4BFA6DC76CE9455EBBC337FD2FE820BF">U moet IDs met andere gegevensbronnen synchroniseren die door containers worden georganiseerd. </li> 
      <li id="li_731DA5D1CBF244F8BEBE57C0E2EBA713">U moet id's synchroniseren met gegevensbronnen in verschillende containers op verschillende pagina's in uw domein. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Container-id&#39;s instellen wanneer u DIL en BezoekerAPI.js gebruikt {#section-f283cb69c8de4348b5316cc4e02a3e9e}

Als u [!UICONTROL DIL]*en* VisitorAPI.js op de zelfde pagina hebt opgesteld:

* De de dienstcode van bezoekersidentiteitskaart neemt belangrijkheid over DIL voor de syncs van identiteitskaart.
* Stel de `idSyncContainerID` -configuratie alleen in de ID-servicecode in.
