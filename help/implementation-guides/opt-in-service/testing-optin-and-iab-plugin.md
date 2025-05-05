---
description: Zodra u Opt-in op uw website hebt toegelaten, gebruik de bevestigingsmethodes om te testen dat de dienst zoals verwacht gebruikend de ontwikkelaarshulpmiddelen in uw browser werkt.
title: Opt-in-service valideren
exl-id: f0bcb32a-ccad-40a4-b031-2584e4136ace
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '441'
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

Klik in Chrome met de rechtermuisknop op de webpagina en selecteer Inspect. Zoals in het schermschot hierboven, selecteer het *1&rbrace; lusje van het Netwerk &lbrace;om de verzoeken te bekijken die van browser worden gemaakt.*

In het bovenstaande voorbeeld zijn de volgende JS-tags voor Adobe op de pagina geïnstalleerd: ECID, AAM, Analytics en Target.

**hoe te om te bewijzen dat Opt-in zoals verwacht werkt:**

U zou geen verzoeken aan de servers van de Adobe moeten zien:

* demdex.net/id
* demdex.net/event
* omtrdc.net/b/ss
* omtrdc.net/m2
* everesttech.net

>[!NOTE]
>
>U zou een vraag aan `http://dpm.demdex.net/optOutStatus` kunnen zien, die een ALLEEN-LEZEN eindpunt is dat wordt gebruikt om de status van de bezoeker Weigeren-uit terug te winnen. Dit eindpunt zal niet in derdekoekjes resulteren die worden gecreeerd, en zal geen informatie van de pagina verzamelen.

U zou geen koekjes moeten zien die door de markeringen van de Adobe worden gecreeerd: (AMCV_{{YOUR_ORG_ID}}, mbox, demdex, s_cc, s_sq, everest_g_v2, everest_session_v2)

In Chrome, ga naar het *lusje van de Toepassing*, breid *Cookies* sectie onder *Opslag* uit, en selecteer de domeinnaam van uw website:

![](assets/use_case_1_2.png)

## Hoofdlettergebruik 2: Opt-in en Opslag inschakelen {#section-bd28326f52474fa09a2addca23ccdc0f}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isOptInStorageEnabled: true 
});
```

Het enige verschil in gebruiksgeval 2 is dat u *een nieuw koekje* zult zien dat de Opt-in toestemmingen zal bevatten die door uw bezoeker worden verstrekt: **adobeujs-optin**

## Hoofdlettergebruik 3: Opt-in inschakelen en Adobe Analytics vooraf goedkeuren {#section-257fe582b425496cbf986d0ec12d3692}

```
var preApproveAnalytics = {}; 
preApproveAnalytics[adobe.OptInCategories.ANALYTICS] = true;

Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    preOptInApprovals: preApproveAnalytics 
});
```

Aangezien Adobe Analytics vooraf is goedgekeurd voor aanmelding, worden op het tabblad Netwerk aanvragen weergegeven voor uw traceringsserver:

![](assets/use_case_3_1.png)

en op het tabblad Toepassing ziet u de cookies Analytics:

![](assets/use_case_3_2.png)

## Hoofdlettergebruik 4: Opt-in en IAB inschakelen {#section-64331998954d4892960dcecd744a6d88}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isIabContext: true 
});
```

**hoe te om uw huidige toestemming IAB op de pagina te bekijken:**

Open de ontwikkelaarshulpmiddelen en selecteer het *1&rbrace; lusje van de Console &lbrace;.* Plak het volgende codefragment en druk op Enter:

```
<codeblock>
  __cmp("getVendorConsents", null, function (vendorConsents) { 
     console.log("Vendor Consent:", vendorConsents); }) 
</codeblock>  
  
```

Hier is een voorbeeldoutput wanneer de doeleinden 1, 2, en 5 worden goedgekeurd, en identiteitskaart van de verkoper van de Audience Manager wordt goedgekeurd:

* demdex.net/id: De aanwezigheid van deze oproep bewijst dat ECID een id heeft aangevraagd bij demdex.net
* demdex.net/event: De aanwezigheid van deze vraag bewijst dat de de gegevensverzamelingsvraag van de DIL zoals verwacht werkt.
* demdex.net/dest5.html: De aanwezigheid van deze vraag toont aan dat de Syncs van identiteitskaart worden teweeggebracht.

![](assets/use_case_4_1.png)

Als één van het volgende ongeldig is, zult u geen verzoeken aan de servers van de Adobe zien, en geen koekjes van de Adobe:

* De doelstellingen 1, 2 of 5 worden niet goedgekeurd.
* De leverancier-id van de Audience Manager is niet goedgekeurd.
