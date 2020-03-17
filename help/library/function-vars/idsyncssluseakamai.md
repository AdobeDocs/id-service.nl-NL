---
description: Hiermee wordt opgegeven of de doelpublicatiesjabloon Akamai moet gebruiken voor HTTPS-verbindingen.
keywords: ID Service
seo-description: Hiermee wordt opgegeven of de doelpublicatiesjabloon Akamai moet gebruiken voor HTTPS-verbindingen.
seo-title: idSyncSSLUseAkamai
title: idSyncSSLUseAkamai
uuid: 501ccc37-c3ab-4454-bfcf-3e3c3e8b5ca3
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# idSyncSSLUseAkamai{#idsyncssluseakamai}

Hiermee wordt opgegeven of de doelpublicatiesjabloon Akamai moet gebruiken voor HTTPS-verbindingen.

De `idSyncSSLUseAkamai` configuratie wordt toegelaten op een per-partnerbasis.

**Syntaxis:** `idSyncSSLUseAkamai: true`

**Codevoorbeeld**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
 
    //Set Akamai URL for ID sync container 
    idSyncSSLUseAkamai:true 
 
    ... 
});
```

