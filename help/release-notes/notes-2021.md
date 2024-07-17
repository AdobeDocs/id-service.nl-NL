---
description: De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van het Experience Cloud.
keywords: ID-service
title: Opmerkingen bij de release 2021
exl-id: 56bffb6f-a4fc-40df-8bb2-17e43772fe60
source-git-commit: 52956b38c59f60507aaf236b152ce41fc1229d14
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 1%

---

# Opmerkingen bij de release Experience Cloud Identity Service - 2021

De versies van de eigenschap, updates, of veranderingen in de Dienst van de Identiteit van het Experience Cloud.

## Bezoeker 5.3.0

De volgende updates zijn opgenomen in de release van bezoeker 5.3.0:

* Bijgewerkt algoritme om lokale ECID te genereren.
* De meest recente optie met `Secure` en `SameSite` markeert voor privacycookie.
* Reparatie voor problemen met een Firefox-browser wanneer een pagina in een onderliggend iFrame wordt geladen.

## Bezoeker 5.2.0

De volgende updates zijn opgenomen in de release van bezoeker 5.2.0:

* In deze versie wordt een gebeurtenis `onReceiveEcid` geïntroduceerd die wordt aangeroepen wanneer een ECID wordt ontvangen van de Identity Service. Bijvoorbeeld:

```js
visitorInstance.onReceiveEcid(callback(ecid){
 console.log(ecid)
})
```
