---
description: Een optionele Booleaanse markering die een kenmerk "Secure" toevoegt aan het AMCV-cookie.
keywords: ID Service
seo-description: Een optionele Booleaanse markering die een kenmerk "Secure" toevoegt aan het AMCV-cookie.
seo-title: secureCookie
title: secureCookie
uuid: 995d19f6-9c9d-4493-9c9c-545b0b5696b0
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# secureCookie{#securecookie}

Een optionele Booleaanse markering die een kenmerk &quot;Secure&quot; toevoegt aan het AMCV-cookie.

Dit configuratiekenmerk is beschikbaar in `visitorAPI`, versie 3.3.0.

>[!NOTE]
>
>De `SecureCookie` configuratie werkt niet op onbeveiligde domeinen en kan ertoe leiden dat u de MID-waarden niet ontvangt voor bezoeken die een onbeveiligd protocol gebruiken. De `secureCookie` configuratie zou aan `true` slechts moeten worden geplaatst wanneer u zeker bent dat alle pagina&#39;s en subdomeinen een veilig protocol altijd gebruiken.

**Syntaxis:** `secureCookie: true | false` (standaard)

**Codevoorbeeld**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE",{ 
 
        //Set secure cookie property 
        secureCookie: true 
 });
```

