---
description: Zodra u Opt-in op uw website hebt toegelaten, gebruik de bevestigingsmethodes om te testen dat de dienst zoals verwacht gebruikend de ontwikkelaarshulpmiddelen in uw browser werkt.
title: Opt-in-service valideren
exl-id: f0bcb32a-ccad-40a4-b031-2584e4136ace
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# Opt-in-service valideren{#validating-opt-in-service}

Zodra u Opt-in op uw website hebt toegelaten, gebruik de bevestigingsmethodes om te testen dat de dienst zoals verwacht gebruikend de ontwikkelaarshulpmiddelen in uw browser werkt.

## Hoofdlettergebruik 1: Inschakelen inschakelen {#section-c8fe1ee3711b420c8186c7057abbecb3}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true 
});
```

![](assets/use_case_1_1.png)

Wis voordat u de pagina laadt de cache en cookies.

Klik in Chrome met de rechtermuisknop op de webpagina en selecteer Inspect. Net als in de bovenstaande schermafbeelding, selecteert u de optie *Netwerk* om de aanvragen van de browser weer te geven.

In het bovenstaande voorbeeld zijn de volgende Adobe JS-tags op de pagina geïnstalleerd: ECID, AAM, Analytics en Target.

**Hoe kan worden aangetoond dat Opt-in werkt zoals u verwacht:**

U zou geen verzoeken aan de servers van Adobe moeten zien:

* demdex.net/id
* demdex.net/event
* omtrdc.net/b/ss
* omtrdc.net/m2
* everesttech.net

>[!NOTE]
>
>U zou een vraag aan kunnen zien `http://dpm.demdex.net/optOutStatus`, wat een ALLEEN-LEZEN eindpunt is dat wordt gebruikt om de status Opt-out van de bezoeker op te halen. Dit eindpunt zal niet in derdekoekjes resulteren die worden gecreeerd, en zal geen informatie van de pagina verzamelen.

Er worden geen cookies weergegeven die met de Adobe-tags zijn gemaakt: (AMCV_{{YOUR_ORG_ID}}, mbox, demdex, s_cc, s_sq, everest_g_v2, everest_session_v2)

Ga in Chrome naar de *Toepassing* tabblad, vouwt u de *Cookies* deel onder *Opslag* en selecteer de domeinnaam van uw website:

![](assets/use_case_1_2.png)

## Hoofdlettergebruik 2: Opt-in en opslag inschakelen {#section-bd28326f52474fa09a2addca23ccdc0f}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isOptInStorageEnabled: true 
});
```

Het enige verschil in gebruikscase 2 is dat je ziet *een nieuw cookie* die de door uw bezoeker verschafte aanmeldingsmachtigingen bevat: **adobeujs-optin**

## Hoofdlettergebruik 3: Inschakelen en vooraf goedkeuren van Adobe Analytics inschakelen {#section-257fe582b425496cbf986d0ec12d3692}

```
var preApproveAnalytics = {}; 
preApproveAnalytics[adobe.OptInCategories.ANALYTICS] = true;

Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    preOptInApprovals: preApproveAnalytics 
});
```

Aangezien Adobe Analytics vooraf is goedgekeurd voor aanmelding, worden op het tabblad Netwerk aanvragen weergegeven voor de volgende server:

![](assets/use_case_3_1.png)

en op het tabblad Toepassing ziet u de cookies Analytics:

![](assets/use_case_3_2.png)

## Hoofdlettergebruik 4: Inschakelen en IAB inschakelen {#section-64331998954d4892960dcecd744a6d88}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isIabContext: true 
});
```

**Hoe te om uw huidige toestemming IAB op de pagina te bekijken:**

Open de gereedschappen voor ontwikkelaars en selecteer de *Console* tab. Plak het volgende codefragment en druk op Enter:

```
<codeblock>
  __cmp("getVendorConsents", null, function (vendorConsents) { 
     console.log("Vendor Consent:", vendorConsents); }) 
</codeblock>  
  
```

Hier is een voorbeeldoutput wanneer de doeleinden 1, 2, en 5 worden goedgekeurd, en identiteitskaart van de verkoper van de Audience Manager wordt goedgekeurd:

* demdex.net/id: De aanwezigheid van deze oproep bewijst dat ECID een id heeft aangevraagd bij demdex.net
* demdex.net/event: De aanwezigheid van deze vraag toont aan dat de de gegevensverzamelingsvraag van de DIL zoals verwacht werkt.
* demdex.net/dest5.html: De aanwezigheid van deze vraag toont aan dat de Syncs van identiteitskaart worden teweeggebracht.

![](assets/use_case_4_1.png)

Als één van het volgende ongeldig is, zult u geen verzoeken aan Adobe servers, en geen koekjes van de Adobe zien:

* De doelstellingen 1, 2 of 5 worden niet goedgekeurd.
* De leverancier-id van de Audience Manager is niet goedgekeurd.
