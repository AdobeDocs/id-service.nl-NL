---
description: Volg deze instructies om het gebied van identiteitskaart van het Experience Cloud in Data Workbench te integreren. Met dit proces kunt u de permanente Experience Cloud-id in uw gegevensfeed gebruiken, waardoor u beter kunt integreren met andere producten in de Adobe Experience Cloud en bezoekers beter kunnen volgen.
keywords: ID-service
title: Data Workbench en de dienst Identiteit Experience Cloud
exl-id: 1903918d-44e4-4790-ab1f-49f5bb701e31
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 0%

---

# Data Workbench en de dienst Identiteit Experience Cloud {#data-workbench-and-the-experience-cloud-id-service}

Volg deze instructies om het gebied van identiteitskaart van het Experience Cloud in Data Workbench te integreren. Met dit proces kunt u de permanente Experience Cloud-id in uw gegevensfeed gebruiken, waardoor u beter kunt integreren met andere producten in de Adobe Experience Cloud en bezoekers beter kunnen volgen.

[ Data Workbench ](https://experienceleague.adobe.com/docs/data-workbench/using/home.html?lang=nl-NL) bijwerken om de dienst van identiteitskaart te gebruiken:

1. Bepaal de plaats van het huidige [&#128279;](https://experienceleague.adobe.com/docs/data-workbench/using/dataset/dataset-include-files/types-dataset-inc-files/c-text-file-dec-groups.html?lang=nl-NL) configuratiedossier van de Groep 0&rbrace; Decoder.

   De [!DNL Decoder Group] bevindt zich doorgaans in een [!UICONTROL Profile Manager] op dit pad: `Dataset\Log Processing\Decoding Instructions.cfg` . 1. Kopieer de huidige decoderingsindeling uit het configuratiebestand.
1. Plak de decoderingsindeling onder het origineel.
1. Open de decoderingsindeling en voeg de volgende nieuwe veldposities toe aan het einde van de lijst:

   * `x-mcvisid`
   * `x-tnt-action`

   Laat de velden leeg als u ze niet kunt gebruiken of definiëren.  **het Decoderen Instructies**

Zie de volledige onderstaande decoderingsinhoud, inclusief de hierboven vermelde nieuwe velden.

```js
Log Processing Include = LogProcessingInclude:   
   Decoder Groups = vector: 1 items
     0 = TextFileDecoderGroup: 
       Decoders = vector: 2 items
         0 = DelimitedDecoder:
          Delimiter = string: \t
           Fields = vector: 389 items  
            0 = string: x-insight-row_type
            1 = string: x-exclude_hit
            10 = string: x-visit_num
            100 = string: x-prop33
            101 = string: x-prop34
            102 = string: x-prop35
            103 = string: x-prop36
            104 = string: x-prop37
            105 = string: x-prop38
            106 = string: x-prop39
            107 = string: x-prop40
            108 = string: x-prop41
            109 = string: x-prop42
            11 = string: x-visit_page_num
            110 = string: x-prop43
            111 = string: x-prop44
            112 = string: x-prop45
            113 = string: x-prop46
            114 = string: x-prop47
            115 = string: x-prop48
            116 = string: x-prop49
            117 = string: x-prop50
            118 = string: x-prop51
            119 = string: x-prop52
            12 = string: x-hitid_high
            120 = string: x-prop53
            121 = string: x-prop54
            122 = string: x-prop55
            123 = string: x-prop56
            124 = string: x-prop57
            125 = string: x-prop58
            126 = string: x-prop59
            127 = string: x-prop60
            128 = string: x-prop61
            129 = string: x-prop62
            13 = string: x-hitid_low
            130 = string: x-prop63
            131 = string: x-prop64
            132 = string: x-prop65
            133 = string: x-prop66
            134 = string: x-prop67
            135 = string: x-prop68
            136 = string: x-prop69
            137 = string: x-prop70
            138 = string: x-prop71
            139 = string: x-prop72
            14 = string: x-accept_language
            140 = string: x-prop73
            141 = string: x-prop74
            142 = string: x-prop75
            143 = string: cs(referrer)
            144 = string: x-ref_domain
            145 = string: x-ref_type
            146 = string: x-resolution
            147 = string: x-s_resolution
            148 = string: x-search_engine
            149 = string: x-search_page_num
            15 = string: x-bot_type
            150 = string: x-state
            151 = string: x-transactionid
            152 = string: x-truncated_hit
            153 = string: x-ua_color
            154 = string: x-ua_os
            155 = string: x-ua_pixels
            156 = string: x-uniques_exceeded
            157 = string: cs(user-agent)
            158 = string: x-user_server
            159 = string: x-va_finder_id
            16 = string: x-bot_id
            160 = string: x-va_finder_detail
            161 = string: x-va_closer_id
            162 = string: x-va_closer_detail
            163 = string: x-va_instance_event
            164 = string: x-va_new_engagement
            165 = string: x-zip
            166 = string: x-last_hit_time_gmt
            167 = string: x-first_hit_time_gmt
            168 = string: x-visit_start_time_gmt
            169 = string: x-last_purchase_time_gmt
            17 = string: x-browser
            170 = string: x-last_purchase_num
            171 = string: x-first_hit_page_url
            172 = string: x-first_hit_pagename
            173 = string: x-visit_start_page_url
            174 = string: x-visit_start_pagename
            175 = string: x-first_hit_referrer
            176 = string: x-visit_referrer
            177 = string: x-visit_search_engine
            178 = string: x-visit_keywords
            179 = string: x-daily_visitor
            18 = string: x-browser_height
            180 = string: x-hourly_visitor
            181 = string: x-monthly_visitor
            182 = string: x-yearly_visitor
            183 = string: x-weekly_visitor
            184 = string: x-quarterly_visitor
            185 = string: x-preloaded
            186 = string: x-tnt
            187 = string: x-survey
            188 = string: x-mvvar1
            189 = string: x-mvvar2
            19 = string: x-browser_width
            190 = string: x-mvvar3
            191 = string: x-media
            192 = string: x-page_event_media
            193 = string: x-page_event_var3
            194 = string: x-tnt_instances
            195 = string: x-survey_instances
            196 = string: x-mvvar1_instances
            197 = string: x-mvvar2_instances
            198 = string: x-mvvar3_instances
            199 = string: x-campaign
            2 = string: x-userid
            20 = string: x-channel
            200 = string: x-purchaseid
            201 = string: x-product-num
            202 = string: x-category
            203 = string: x-product
            204 = string: x-units
            205 = string: x-revenue
            206 = string: x-order
            207 = string: x-cart_open
            208 = string: x-cart_view
            209 = string: x-checkout
            21 = string: x-click_action
            210 = string: x-cart_add
            211 = string: x-cart_remove
            212 = string: x-product_view
            213 = string: x-evar1
            214 = string: x-evar2
            215 = string: x-evar3
            216 = string: x-evar4
            217 = string: x-evar5
            218 = string: x-evar6
            219 = string: x-evar7
            22 = string: x-click_action_type
            220 = string: x-evar8
            221 = string: x-evar9
            222 = string: x-evar10
            223 = string: x-evar11
            224 = string: x-evar12
            225 = string: x-evar13
            226 = string: x-evar14
            227 = string: x-evar15
            228 = string: x-evar16
            229 = string: x-evar17
            23 = string: x-click_context
            230 = string: x-evar18
            231 = string: x-evar19
            232 = string: x-evar20
            233 = string: x-evar21
            234 = string: x-evar22
            235 = string: x-evar23
            236 = string: x-evar24
            237 = string: x-evar25
            238 = string: x-evar26
            239 = string: x-evar27
            24 = string: x-click_context_type
            240 = string: x-evar28
            241 = string: x-evar29
            242 = string: x-evar30
            243 = string: x-evar31
            244 = string: x-evar32
            245 = string: x-evar33
            246 = string: x-evar34
            247 = string: x-evar35
            248 = string: x-evar36
            249 = string: x-evar37
            25 = string: x-click_source_id
            250 = string: x-evar38
            251 = string: x-evar39
            252 = string: x-evar40
            253 = string: x-evar41
            254 = string: x-evar42
            255 = string: x-evar43
            256 = string: x-evar44
            257 = string: x-evar45
            258 = string: x-evar46
            259 = string: x-evar47
            26 = string: x-click_tag
            260 = string: x-evar48
            261 = string: x-evar49
            262 = string: x-evar50
            263 = string: x-evar51
            264 = string: x-evar52
            265 = string: x-evar53
            266 = string: x-evar54
            267 = string: x-evar55
            268 = string: x-evar56
            269 = string: x-evar57
            27 = string: x-code_ver
            270 = string: x-evar58
            271 = string: x-evar59
            272 = string: x-evar60
            273 = string: x-evar61
            274 = string: x-evar62
            275 = string: x-evar63
            276 = string: x-evar64
            277 = string: x-evar65
            278 = string: x-evar66
            279 = string: x-evar67
            28 = string: x-c_color
            280 = string: x-evar68
            281 = string: x-evar69
            282 = string: x-evar70
            283 = string: x-evar71
            284 = string: x-evar72
            285 = string: x-evar73
            286 = string: x-evar74
            287 = string: x-evar75
            288 = string: x-cust1
            289 = string: x-cust2
            29 = string: x-color
            290 = string: x-cust3
            291 = string: x-cust4
            292 = string: x-cust5
            293 = string: x-cust6
            294 = string: x-cust7
            295 = string: x-cust8
            296 = string: x-cust9
            297 = string: x-cust10
            298 = string: x-cust11
            299 = string: x-cust12
            3 = string: x-service
            30 = string: x-cookies
            300 = string: x-cust13
            301 = string: x-cust14
            302 = string: x-cust15
            303 = string: x-cust16
            304 = string: x-cust17
            305 = string: x-cust18
            306 = string: x-cust19
            307 = string: x-cust20
            308 = string: x-cust21
            309 = string: x-cust22
            31 = string: x-ct_connect_type
            310 = string: x-cust23
            311 = string: x-cust24
            312 = string: x-cust25
            313 = string: x-cust26
            314 = string: x-cust27
            315 = string: x-cust28
            316 = string: x-cust29
            317 = string: x-cust30
            318 = string: x-cust31
            319 = string: x-cust32
            32 = string: x-connection_type
            320 = string: x-cust33
            321 = string: x-cust34
            322 = string: x-cust35
            323 = string: x-cust36
            324 = string: x-cust37
            325 = string: x-cust38
            326 = string: x-cust39
            327 = string: x-cust40
            328 = string: x-cust41
            329 = string: x-cust42
            33 = string: x-country
            330 = string: x-cust43
            331 = string: x-cust44
            332 = string: x-cust45
            333 = string: x-cust46
            334 = string: x-cust47
            335 = string: x-cust48
            336 = string: x-cust49
            337 = string: x-cust50
            338 = string: x-cust51
            339 = string: x-cust52
            34 = string: x-currency
            340 = string: x-cust53
            341 = string: x-cust54
            342 = string: x-cust55
            343 = string: x-cust56
            344 = string: x-cust57
            345 = string: x-cust58
            346 = string: x-cust59
            347 = string: x-cust60
            348 = string: x-cust61
            349 = string: x-cust62
            35 = string: x-curr_rate
            350 = string: x-cust63
            351 = string: x-cust64
            352 = string: x-cust65
            353 = string: x-cust66
            354 = string: x-cust67
            355 = string: x-cust68
            356 = string: x-cust69
            357 = string: x-cust70
            358 = string: x-cust71
            359 = string: x-cust72
            36 = string: x-curr_factor
            360 = string: x-cust73
            361 = string: x-cust74
            362 = string: x-cust75
            363 = string: x-cust76
            364 = string: x-cust77
            365 = string: x-cust78
            366 = string: x-cust79
            367 = string: x-cust80
            368 = string: x-cust81
            369 = string: x-cust82
            37 = string: x-domain
            370 = string: x-cust83
            371 = string: x-cust84
            372 = string: x-cust85
            373 = string: x-cust86
            374 = string: x-cust87
            375 = string: x-cust88
            376 = string: x-cust89
            377 = string: x-cust90
            378 = string: x-cust91
            379 = string: x-cust92
            38 = string: x-geo_city
            380 = string: x-cust93
            381 = string: x-cust94
            382 = string: x-cust95
            383 = string: x-cust96
            384 = string: x-cust97
            385 = string: x-cust98
            386 = string: x-cust99
            387 = string: x-cust100
            388 = string: x-ecom_additional_data
            39 = string: x-geo_country
            4 = string: x-page_event
            40 = string: x-geo_dma
            41 = string: x-geo_region
            42 = string: x-geo_zip
            43 = string: x-hier1
            44 = string: x-hier2
            45 = string: x-hier3
            46 = string: x-hier4
            47 = string: x-hier5
            48 = string: x-homepage
            49 = string: c-ip
            5 = string: x-hit_source
            50 = string: x-j_jscript
            51 = string: x-javascript
            52 = string: x-java_enabled
            53 = string: x-keywords
            54 = string: x-language
            55 = string: x-mobile_id
            56 = string: x-new_visit
            57 = string: x-os
            58 = string: x-p_plugins
            59 = string: x-plugins
            6 = string: x-hit_time_gmt
            60 = string: x-page_event_var1
            61 = string: x-page_event_var2
            62 = string: x-page_type
            63 = string: cs-uri
            64 = string: x-pagename
            65 = string: x-paid_search
            66 = string: x-partner_plugins
            67 = string: x-persistent_cookie
            68 = string: x-prop1
            69 = string: x-prop2
            7 = string: x-date_time
            70 = string: x-prop3
            71 = string: x-prop4
            72 = string: x-prop5
            73 = string: x-prop6
            74 = string: x-prop7
            75 = string: x-prop8
            76 = string: x-prop9
            77 = string: x-prop10
            78 = string: x-prop11
            79 = string: x-prop12
            8 = string: x-visid_high
            80 = string: x-prop13
            81 = string: x-prop14
            82 = string: x-prop15
            83 = string: x-prop16
            84 = string: x-prop17
            85 = string: x-prop18
            86 = string: x-prop19
            87 = string: x-prop20
            88 = string: x-prop21
            89 = string: x-prop22
            9 = string: x-visid_low
            90 = string: x-prop23
            91 = string: x-prop24
            92 = string: x-prop25
            93 = string: x-prop26
            94 = string: x-prop27
            95 = string: x-prop28
            96 = string: x-prop29
            97 = string: x-prop30
            98 = string: x-prop31
            99 = string: x-prop32
        1 = DelimitedDecoder: 
          Delimiter = string: \t
          Fields = vector: 391 items
            0 = string: x-insight-row_type
            1 = string: x-exclude_hit
            10 = string: x-visit_num
            100 = string: x-prop33
            101 = string: x-prop34
            102 = string: x-prop35
            103 = string: x-prop36
            104 = string: x-prop37
            105 = string: x-prop38
            106 = string: x-prop39
            107 = string: x-prop40
            108 = string: x-prop41
            109 = string: x-prop42
            11 = string: x-visit_page_num
            110 = string: x-prop43
            111 = string: x-prop44
            112 = string: x-prop45
            113 = string: x-prop46
            114 = string: x-prop47
            115 = string: x-prop48
            116 = string: x-prop49
            117 = string: x-prop50
            118 = string: x-prop51
            119 = string: x-prop52
            12 = string: x-hitid_high
            120 = string: x-prop53
            121 = string: x-prop54
            122 = string: x-prop55
            123 = string: x-prop56
            124 = string: x-prop57
            125 = string: x-prop58
            126 = string: x-prop59
            127 = string: x-prop60
            128 = string: x-prop61
            129 = string: x-prop62
            13 = string: x-hitid_low
            130 = string: x-prop63
            131 = string: x-prop64
            132 = string: x-prop65
            133 = string: x-prop66
            134 = string: x-prop67
            135 = string: x-prop68
            136 = string: x-prop69
            137 = string: x-prop70
            138 = string: x-prop71
            139 = string: x-prop72
            14 = string: x-accept_language
            140 = string: x-prop73
            141 = string: x-prop74
            142 = string: x-prop75
            143 = string: cs(referrer)
            144 = string: x-ref_domain
            145 = string: x-ref_type
            146 = string: x-resolution
            147 = string: x-s_resolution
            148 = string: x-search_engine
            149 = string: x-search_page_num
            15 = string: x-bot_type
            150 = string: x-state
            151 = string: x-transactionid
            152 = string: x-truncated_hit
            153 = string: x-ua_color
            154 = string: x-ua_os
            155 = string: x-ua_pixels
            156 = string: x-uniques_exceeded
            157 = string: cs(user-agent)
            158 = string: x-user_server
            159 = string: x-va_finder_id
            16 = string: x-bot_id
            160 = string: x-va_finder_detail
            161 = string: x-va_closer_id
            162 = string: x-va_closer_detail
            163 = string: x-va_instance_event
            164 = string: x-va_new_engagement
            165 = string: x-zip
            166 = string: x-last_hit_time_gmt
            167 = string: x-first_hit_time_gmt
            168 = string: x-visit_start_time_gmt
            169 = string: x-last_purchase_time_gmt
            17 = string: x-browser
            170 = string: x-last_purchase_num
            171 = string: x-first_hit_page_url
            172 = string: x-first_hit_pagename
            173 = string: x-visit_start_page_url
            174 = string: x-visit_start_pagename
            175 = string: x-first_hit_referrer
            176 = string: x-visit_referrer
            177 = string: x-visit_search_engine
            178 = string: x-visit_keywords
            179 = string: x-daily_visitor
            18 = string: x-browser_height
            180 = string: x-hourly_visitor
            181 = string: x-monthly_visitor
            182 = string: x-yearly_visitor
            183 = string: x-weekly_visitor
            184 = string: x-quarterly_visitor
            185 = string: x-preloaded
            186 = string: x-tnt
            187 = string: x-survey
            188 = string: x-mvvar1
            189 = string: x-mvvar2
            19 = string: x-browser_width
            190 = string: x-mvvar3
            191 = string: x-media
            192 = string: x-page_event_media
            193 = string: x-page_event_var3
            194 = string: x-tnt_instances
            195 = string: x-survey_instances
            196 = string: x-mvvar1_instances
            197 = string: x-mvvar2_instances
            198 = string: x-mvvar3_instances
            199 = string: x-campaign
            2 = string: x-userid
            20 = string: x-channel
            200 = string: x-purchaseid
            201 = string: x-product-num
            202 = string: x-category
            203 = string: x-product
            204 = string: x-units
            205 = string: x-revenue
            206 = string: x-order
            207 = string: x-cart_open
            208 = string: x-cart_view
            209 = string: x-checkout
            21 = string: x-click_action
            210 = string: x-cart_add
            211 = string: x-cart_remove
            212 = string: x-product_view
            213 = string: x-evar1
            214 = string: x-evar2
            215 = string: x-evar3
            216 = string: x-evar4
            217 = string: x-evar5
            218 = string: x-evar6
            219 = string: x-evar7
            22 = string: x-click_action_type
            220 = string: x-evar8
            221 = string: x-evar9
            222 = string: x-evar10
            223 = string: x-evar11
            224 = string: x-evar12
            225 = string: x-evar13
            226 = string: x-evar14
            227 = string: x-evar15
            228 = string: x-evar16
            229 = string: x-evar17
            23 = string: x-click_context
            230 = string: x-evar18
            231 = string: x-evar19
            232 = string: x-evar20
            233 = string: x-evar21
            234 = string: x-evar22
            235 = string: x-evar23
            236 = string: x-evar24
            237 = string: x-evar25
            238 = string: x-evar26
            239 = string: x-evar27
            24 = string: x-click_context_type
            240 = string: x-evar28
            241 = string: x-evar29
            242 = string: x-evar30
            243 = string: x-evar31
            244 = string: x-evar32
            245 = string: x-evar33
            246 = string: x-evar34
            247 = string: x-evar35
            248 = string: x-evar36
            249 = string: x-evar37
            25 = string: x-click_source_id
            250 = string: x-evar38
            251 = string: x-evar39
            252 = string: x-evar40
            253 = string: x-evar41
            254 = string: x-evar42
            255 = string: x-evar43
            256 = string: x-evar44
            257 = string: x-evar45
            258 = string: x-evar46
            259 = string: x-evar47
            26 = string: x-click_tag
            260 = string: x-evar48
            261 = string: x-evar49
            262 = string: x-evar50
            263 = string: x-evar51
            264 = string: x-evar52
            265 = string: x-evar53
            266 = string: x-evar54
            267 = string: x-evar55
            268 = string: x-evar56
            269 = string: x-evar57
            27 = string: x-code_ver
            270 = string: x-evar58
            271 = string: x-evar59
            272 = string: x-evar60
            273 = string: x-evar61
            274 = string: x-evar62
            275 = string: x-evar63
            276 = string: x-evar64
            277 = string: x-evar65
            278 = string: x-evar66
            279 = string: x-evar67
            28 = string: x-c_color
            280 = string: x-evar68
            281 = string: x-evar69
            282 = string: x-evar70
            283 = string: x-evar71
            284 = string: x-evar72
            285 = string: x-evar73
            286 = string: x-evar74
            287 = string: x-evar75
            288 = string: x-cust1
            289 = string: x-cust2
            29 = string: x-color
            290 = string: x-cust3
            291 = string: x-cust4
            292 = string: x-cust5
            293 = string: x-cust6
            294 = string: x-cust7
            295 = string: x-cust8
            296 = string: x-cust9
            297 = string: x-cust10
            298 = string: x-cust11
            299 = string: x-cust12
            3 = string: x-service
            30 = string: x-cookies
            300 = string: x-cust13
            301 = string: x-cust14
            302 = string: x-cust15
            303 = string: x-cust16
            304 = string: x-cust17
            305 = string: x-cust18
            306 = string: x-cust19
            307 = string: x-cust20
            308 = string: x-cust21
            309 = string: x-cust22
            31 = string: x-ct_connect_type
            310 = string: x-cust23
            311 = string: x-cust24
            312 = string: x-cust25
            313 = string: x-cust26
            314 = string: x-cust27
            315 = string: x-cust28
            316 = string: x-cust29
            317 = string: x-cust30
            318 = string: x-cust31
            319 = string: x-cust32
            32 = string: x-connection_type
            320 = string: x-cust33
            321 = string: x-cust34
            322 = string: x-cust35
            323 = string: x-cust36
            324 = string: x-cust37
            325 = string: x-cust38
            326 = string: x-cust39
            327 = string: x-cust40
            328 = string: x-cust41
            329 = string: x-cust42
            33 = string: x-country
            330 = string: x-cust43
            331 = string: x-cust44
            332 = string: x-cust45
            333 = string: x-cust46
            334 = string: x-cust47
            335 = string: x-cust48
            336 = string: x-cust49
            337 = string: x-cust50
            338 = string: x-cust51
            339 = string: x-cust52
            34 = string: x-currency
            340 = string: x-cust53
            341 = string: x-cust54
            342 = string: x-cust55
            343 = string: x-cust56
            344 = string: x-cust57
            345 = string: x-cust58
            346 = string: x-cust59
            347 = string: x-cust60
            348 = string: x-cust61
            349 = string: x-cust62
            35 = string: x-curr_rate
            350 = string: x-cust63
            351 = string: x-cust64
            352 = string: x-cust65
            353 = string: x-cust66
            354 = string: x-cust67
            355 = string: x-cust68
            356 = string: x-cust69
            357 = string: x-cust70
            358 = string: x-cust71
            359 = string: x-cust72
            36 = string: x-curr_factor
            360 = string: x-cust73
            361 = string: x-cust74
            362 = string: x-cust75
            363 = string: x-cust76
            364 = string: x-cust77
            365 = string: x-cust78
            366 = string: x-cust79
            367 = string: x-cust80
            368 = string: x-cust81
            369 = string: x-cust82
            37 = string: x-domain
            370 = string: x-cust83
            371 = string: x-cust84
            372 = string: x-cust85
            373 = string: x-cust86
            374 = string: x-cust87
            375 = string: x-cust88
            376 = string: x-cust89
            377 = string: x-cust90
            378 = string: x-cust91
            379 = string: x-cust92
            38 = string: x-geo_city
            380 = string: x-cust93
            381 = string: x-cust94
            382 = string: x-cust95
            383 = string: x-cust96
            384 = string: x-cust97
            385 = string: x-cust98
            386 = string: x-cust99
            387 = string: x-cust100
            388 = string: x-ecom_additional_data
            389 = string: x-mcvisid
            39 = string: x-geo_country
            390 = string: x-tnt-action
            4 = string: x-page_event
            40 = string: x-geo_dma
            41 = string: x-geo_region
            42 = string: x-geo_zip
            43 = string: x-hier1
            44 = string: x-hier2
            45 = string: x-hier3
            46 = string: x-hier4
            47 = string: x-hier5
            48 = string: x-homepage
            49 = string: c-ip
            5 = string: x-hit_source
            50 = string: x-j_jscript
            51 = string: x-javascript
            52 = string: x-java_enabled
            53 = string: x-keywords
            54 = string: x-language
            55 = string: x-mobile_id
            56 = string: x-new_visit
            57 = string: x-os
            58 = string: x-p_plugins
            59 = string: x-plugins
            6 = string: x-hit_time_gmt
            60 = string: x-page_event_var1
            61 = string: x-page_event_var2
            62 = string: x-page_type
            63 = string: cs-uri
            64 = string: x-pagename
            65 = string: x-paid_search
            66 = string: x-partner_plugins
            67 = string: x-persistent_cookie
            68 = string: x-prop1
            69 = string: x-prop2
            7 = string: x-date_time
            70 = string: x-prop3
            71 = string: x-prop4
            72 = string: x-prop5
            73 = string: x-prop6
            74 = string: x-prop7
            75 = string: x-prop8
            76 = string: x-prop9
            77 = string: x-prop10
            78 = string: x-prop11
            79 = string: x-prop12
            8 = string: x-visid_high
            80 = string: x-prop13
            81 = string: x-prop14
            82 = string: x-prop15
            83 = string: x-prop16
            84 = string: x-prop17
            85 = string: x-prop18
            86 = string: x-prop19
            87 = string: x-prop20
            88 = string: x-prop21
            89 = string: x-prop22
            9 = string: x-visid_low
            90 = string: x-prop23
            91 = string: x-prop24
            92 = string: x-prop25
            93 = string: x-prop26
            94 = string: x-prop27
            95 = string: x-prop28
            96 = string: x-prop29
            97 = string: x-prop30
            98 = string: x-prop31
            99 = string: x-prop32
       Name = string: Adobe SC decoder
  Fields = vector: 0 items
  Log Entry Condition = AndCondition: 0 items
  Parameters = vector: 0 items
  Stage = string: Default
  Transformations = vector: 0 items
```
