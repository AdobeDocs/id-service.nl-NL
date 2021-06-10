---
description: Een optionele Booleaanse markering die een kenmerk "Secure" toevoegt aan het AMCV-cookie.
keywords: ID-service
title: secureCookie
exl-id: ba281b1c-1112-4ed6-b4fd-b8f87cabc575
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 2%

---

# secureCookie{#securecookie}

Een optionele Booleaanse markering die een kenmerk &quot;Secure&quot; toevoegt aan het AMCV-cookie.

Dit configuratiekenmerk is beschikbaar in `visitorAPI`, versie 3.3.0.

>[!NOTE]
>
>De `SecureCookie` configuratie werkt niet op onbeveiligde domeinen en kan ertoe leiden dat u de MID-waarden niet ontvangt voor bezoeken die een onbeveiligd protocol gebruiken. De `secureCookie` configuratie zou aan `true` slechts moeten worden geplaatst wanneer u zeker bent dat alle pagina&#39;s en sub-domeinen een veilig protocol altijd gebruiken.

**Syntaxis:** `secureCookie: true | false` (standaard)

**Codevoorbeeld**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE",{ 
 
        //Set secure cookie property 
        secureCookie: true 
 });
```
