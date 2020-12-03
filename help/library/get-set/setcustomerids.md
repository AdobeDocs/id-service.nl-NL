---
description: setCustomerIDs plaatst 1 of meer zeer belangrijk-waardeparen die klant IDs en hun authentificatiestatus bepalen.
keywords: ID Service
seo-description: setCustomerIDs plaatst 1 of meer zeer belangrijk-waardeparen die klant IDs en hun authentificatiestatus bepalen.
seo-title: setCustomerIDs
title: setCustomerIDs
uuid: 4f960f98-cec2-4db6-84ea-0259e2128ea2
translation-type: tm+mt
source-git-commit: 21fb12b817b7c8cd34e6022ca6c188229228d1df
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 1%

---


# setCustomerIDs{#setcustomerids}

setCustomerIDs plaatst 1 of meer zeer belangrijk-waardeparen die klant IDs en hun authentificatiestatus bepalen.

**Syntaxis:** `visitor.setCustomerIDs()`

U kunt een of meer id&#39;s instellen, zoals in het onderstaande codevoorbeeld wordt getoond. Zie [Klantnamen en Verificatiestatus](../../reference/authenticated-state.md) voor meer informatie en voorbeelden.

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

