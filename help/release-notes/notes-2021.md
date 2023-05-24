---
description: De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van de Experience Cloud.
keywords: ID-service
title: Opmerkingen bij de release 2021
exl-id: f0bbb100-49a9-4bba-8cee-5f40bec87984
source-git-commit: fcd3e8b65bb84e94eabac7ffec6a34f4cf75ec3d
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 1%

---

# Opmerkingen bij de release van Experience Cloud Identity Service - 2021

De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van de Experience Cloud.

## Bezoeker 5.3.0

De volgende updates zijn opgenomen in de release van bezoeker 5.3.0:

* Bijgewerkt algoritme om lokale ECID te genereren.
* Meest recente opt-in met `Secure` en `SameSite` vlaggen voor privacycookie.
* Reparatie voor problemen met een Firefox-browser wanneer een pagina in een onderliggend iFrame wordt geladen.

## Bezoeker 5.2.0

De volgende updates zijn opgenomen in de release van bezoeker 5.2.0:

* Deze versie introduceert een gebeurtenis `onRecieveEcid`, die wordt opgeroepen wanneer een ECID wordt ontvangen van de Identity Service. Bijvoorbeeld:

```js
visitorInstance.onRecieveEcid(callback(ecid){
 console.log(ecid)
})
```
