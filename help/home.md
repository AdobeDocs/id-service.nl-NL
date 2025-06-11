---
description: De Experience Cloud Identity Service maakt het gemeenschappelijke identificatiekader voor Experience Cloud Application and Services mogelijk. Dit werkt door een unieke, permanente id, de Experience Cloud-id (ECID), toe te wijzen aan een bezoeker van de site.
keywords: ID-service; Identiteitsservice; Experience Cloud-identiteitsservice
title: Experience Cloud Identity-service
exl-id: fe1368db-06ca-4c79-b655-b7064e316d74
source-git-commit: 507b5c9fed0d6d16828522c0fd9c7db4fdeefe3d
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 2%

---

# Adobe Experience Cloud Identity Service {#experience-cloud-id-service}

De Experience Cloud Identity Service maakt het gemeenschappelijke identificatiekader voor Experience Cloud Application and Services mogelijk. Dit werkt door een unieke, permanente id, de Experience Cloud-id (ECID), toe te wijzen aan een bezoeker van de site.

## Werken met de belangrijkste identiteitsentiteiten

Voor een beter inzicht in hoe Adobe bezoekers op unieke wijze kan identificeren en identiteitsgegevens kan oplossen, leest u de onderstaande uitsplitsing:

* **Dienst van de Identiteit van Experience Cloud**: De Dienst van de Identiteit van Experience Cloud **is verantwoordelijk voor het plaatsen van identiteitskaart van Experience Cloud (ECID)**. Voor meer informatie, lees het [ overzicht van de Dienst van de Identiteit van Experience Cloud ](./introduction/overview.md).
* **identiteitskaart van Experience Cloud (ECID)**: ECID is een gedeelde identiteit namespace die over de toepassingen van Adobe Experience Platform en van Adobe Experience Cloud wordt gebruikt om mensen en apparaten te identificeren. Voor meer informatie over ECID, lees het [ overzicht ECID ](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html).
* **de Dienst van de Identiteit van Experience Platform**: De Dienst van de Identiteit van Experience Platform voorziet u van een uitvoerige mening van uw klanten en hun gedrag door identiteiten over apparaten en systemen te overbruggen. Voor meer informatie, lees [ overzicht van de Dienst van de Identiteit van Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=nl).

<!-- The Adobe Experience Cloud Identity Service provides a universal, persistent ID that identifies your visitors across all the solutions in the Experience Cloud. It can replace ID generation code for Experience Cloud solutions and services. -->

<table id="table_5E612F746A704FE095B809A013EE977F" class="simpletable"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b> Begonnen het worden </b> </p> <p> 
     <ul id="ul_D5EC6A54A03F4AB595B588116A7C1296"> 
      <li id="li_845F6DE25A1241439BCDCBC00459D7EB"> <a href="introduction/overview.md" format="dita" scope="local"> Overzicht </a> </li> 
      <li id="li_47F399E1D4AF4F08BD647DF01A423BA7"> <a href="reference/requirements.md" format="dita" scope="local"> Vereisten voor de Experience Cloud Identity Service </a> </li> 
      <li id="li_CBEEE79B45644F28A52B58DDF23DAD4F"> <a href="https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en" format="html" scope="external"> Standaardimplementatie met platformlabels </a> </li> 
     </ul> </p> <p><b> Javascript van identiteitskaart van Experience Cloud Bibliotheken </b> </p> <p>JavaScript for the Experience Cloud Identity Service bevindt zich op: <a href="https://github.com/Adobe-Marketing-Cloud/id-service/releases" format="https" scope="external"> https://github.com/Adobe-Marketing-Cloud/id-service/releases</a> </p> <p> <b> Nieuwe of Aanbevolen Punten </b> </p> <p> 
     <ul id="ul_B0A25B6827734D55BB1E20D12334AC21"> 
      <li id="li_A66924F4948F4A5ABA545A89A28A6F6A"><a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> Inschakelen-service </a> </li> 
      <li id="li_92D49CB788AD478EA74BCF5328CB9A14"> <a href="library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues </a> </li> 
      <li id="li_9E512C6DD15C46C3ABD06ACD60D97E4A"> <a href="faq-intro/faq-intro.md" format="dita" scope="local"> Veelgestelde vragen </a> </li> 
      <li id="li_7744A4898EA542B9BF009D2066810050"> <a href="library/function-vars/idsyncontainerid.md#reference-5cfbed2240fa4def90f535f017a36015" format="dita" scope="local"> idSyncContainerID </a> </li> 
     </ul> </p> 
     <!-- 
     <p> <b>Announcements:</b> </p> 
     <p> <p>Important:  ID service support for Internet Explorer 6, 7, and 8 is deprecated and will be discontinued in a future release. </p> </p> 
     --> </td> 
   <td colname="col2"> <p> <b>Release-opmerkingen</b> </p> <p><b> Versie 4.4 </b> 17 juli, omvat de versie van 2019 steun voor het <a href="reference/hashing-support.md" format="dita" scope="local"> SHA-256 het hakken algoritme </a> dat u toestaat om in klant IDs of e-mailadressen over te gaan, en gehakt IDs over te gaan.</p><p><b> Versie 4.0 </b> 12 februari, omvat de versie van 2019 de <a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> Opt-binnen dienst </a> wordt gebruikt om te identificeren als u een koekje op het apparaat of browser van een gebruiker kunt plaatsen wanneer het bezoeken van uw plaats. </p> <p> 
     <ul id="ul_4F06F170F214492780C7D25A069F799F"> 
      <li id="li_45A7CD556FE44F4DAB035C736A058F36"> Zie de nieuwste <a href="https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=en" format="https" scope="external"> Opmerkingen bij de release van Experience Cloud </a> voor nieuwe functies en oplossingen. </li> 
      <li id="li_10CC4FBFEFC947CA9AD15F52D9715257">Zie de sectie <a href="https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=en" format="html" scope="external"> Opmerkingen bij vorige release </a> voor oudere releases. </li> 
     </ul> </p> <p> <b> Middelen van Experience Cloud </b> </p> <p> 
     <ul id="ul_E30EC96BDC624B5591F0470D430B7F41"> 
      <li id="li_F3A5CCFAE0F247CEB41A03CA8E03106B"> <a href="http://www.adobe.com/privacy.html" format="http" scope="external"> Adobe Privacy Center </a> </li> 
      <li id="li_A54C1EB170EA4B8FA6A81B90AB0C39DD"> <a href="https://experienceleague.adobe.com/docs/home.html?lang=en" scope="external" format="http"> Adobe Experience Cloud </a> </li> 
      <li id="li_1938F7044F544481A6CC0F45CC22B80A"> <a href="http://helpx.adobe.com/learning.html?promoid=KAUDK" scope="external" format="http"> Adobe Training en zelfstudies </a> </li> 
      <li id="li_C71459E0D1464C05B8B9387C43541F17"> <a href="https://helpx.adobe.com/nl/support/experience-cloud.html" scope="external" format="https"> Introductiepagina van productdocumentatie </a> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
