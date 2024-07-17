---
description: setCustomerIDs plaatst 1 of meer zeer belangrijk-waardeparen die klant IDs en hun authentificatiestatus bepalen.
keywords: ID-service
title: setCustomerIDs
exl-id: 8fc549d3-2a6f-4214-bb0d-3e0bc1501ce2
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '60'
ht-degree: 0%

---

# setCustomerIDs{#setcustomerids}

setCustomerIDs plaatst 1 of meer zeer belangrijk-waardeparen die klant IDs en hun authentificatiestatus bepalen.

**Syntaxis:** `visitor.setCustomerIDs()`

U kunt een of meer id&#39;s instellen, zoals in het onderstaande codevoorbeeld wordt getoond. Zie [ identiteitskaarts van de Klant en de Staten van de Authentificatie ](../../reference/authenticated-state.md) voor meer informatie en voorbeelden.

```js
// Single ID with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
//Multiple IDs with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":"550e8400-e29b-41d4-a716-446655440000" 
});
```
