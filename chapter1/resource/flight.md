>#航班信息卡片

####1.测试 Demo
{%fbq%}
term:##航班名称##
ner:##FLIGHT_NUM##
{%endfbq%}


####2.返回 Json 示例
>示例一：flight_list
```json
{
    "id": "ZH1883",
    "depCity": "北京",
    "arrCity": "上海",
    "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:DOrRtuZ2LOF81rDcB4SXeoVD_mvvEn6tJXZ8jdsh4UFBoDr5RgXbj4SDPNKO4zu2kerFyhQClnLjtzRvp-KMgdAtzsnEC-dl-Z9HaA_9F9uj_Qhw6HvTutoFWufiLP9YfZ43L4s8e5QimKiyYQ-BT6Cs96ZBJUCp28tYFwpisjGQGflaLkXf3xcZIXSBLx8Fy0V4W7hswTixPYOKT4r0KTK9C5t1RVFqVDGiWziBDWAT_orKFwbKBg=="
}
```

>示例二：feiyou_flight_list
```json
{
    "flightNo": "ZH1883",
    "flightCompany": "深圳航空",
    "flightDepcode": "PEK",
    "flightArrcode": "PVG",
    "FlightHTerminal": "T3",
    "FlightTerminal": "T2",
    "flightDeptimePlanDate": "2018-08-22 20:20:00",
    "flightArrtimePlanDate": "2018-08-22 22:35:00",
    "flightDep": "北京",
    "flightArr": "上海",
    "flightDepAirport": "北京首都",
    "flightArrAirport": "上海浦东",
    "ontimeRate": "100%",
    "flightState": "计划",
    "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:DOrRtuZ2LOF81rDcB4SXeoVD_mvvEn6tJXZ8jdsh4UFBoDr5RgXbj4SDPNKO4zu2kerFyhQClnLjtzRvp-KMgdAtzsnEC-dl5AMImwP866rTdqTfJRsjFeaCe2j2_GX6Ovvl478JeYYf7qxHnPMiBXqiYp90pwnWkkHnxpjCHQ8DCDi4WKMUz6EzTmcMqrlTQZ6CGKkEbq7E62ootjhd5b6zal1W0uc9LnogmP8XzQWaMuKTUIq9z2O9wqhZP_9QIVQibqr9o4Z7pn6s0r8LiY_TQPqHCjThItXBHML8o5vutbon0EUSfucnqLVfhitEFZ9L1Hpq3DmiyEh5W-yvfD6cCnAhbWwUHYdnKHV99Qk9JrhEkv8K3pk3vLlso28B6T29m_0XZra5aiAZG_Z6FGTbQGUP47Fv0ws7rViVlJLjANo27vg19rYItMf-K4lZ54eNinnLLk6vbErgHmGn3ujnVyvuJiee7pEMRNRjSbE=",
    "source": "Trio_Feiyou"
 }
```

####3.返回字段说明

>卡片字段名称：flight_list

|名称|说明|类型|示例|
|:---|:---|:---|:---|
|id|航班id|string|ZH1883|
|depCity|起始城市|string|北京|
|arrCity|目标城市|string|上海|
|url|航班链接|string|http://phoneapi.sanjiaoshou.net/nlp/q?key:DOrRtuZ2LOF81rDcB4SXeoVD_mvvEn6tJXZ8jdsh4UFBoDr5RgXbj4SDPNKO4zu2kerFyhQClnLjtzRvp-KMgdAtzsnEC-dl-Z9HaA_9F9uj_Qhw6HvTutoFWufiLP9YfZ43L4s8e5QimKiyYQ-BT6Cs96ZBJUCp28tYFwpisjGQGflaLkXf3xcZIXSBLx8Fy0V4W7hswTixPYOKT4r0KTK9C5t1RVFqVDGiWziBDWAT_orKFwbKBg==|

-------------------------------------------------------------
>卡片字段名称：feiyou_flight_list

|名称|说明|类型|示例|
|:---|:---|:---|:---|
|flightNo|航班id|string|KN5987|
|flightCompany|承运公司|string|深圳航空|
|flightDepcode|起始城市代码|string|PEK|
|flightArrcode|目标城市代码|string|PVG|
|FlightHTerminal|起始航站楼|string|T3|
|FlightTerminal|目标航站楼|string|T2|
|flightDeptimePlanDate|起飞预定时间|string|2018-08-22 20:20:00|
|flightArrtimePlanDate|抵达预定时间|string|2018-08-22 22:35:00|
|flightDep|起始城市|string|北京|
|flightArr|目标城市|string|上海|
|flightDepAirport|起始机场|string|北京首都|
|flightArrAirport|目标机场|string|上海浦东|
|ontimeRate|准点率|string|100%|
|flightState|航班状态|string|计划|
|url|订票链接|string|http://phoneapi.sanjiaoshou.net/nlp/q?key:DOrRtuZ2LOF81rDcB4SXeoVD_mvvEn6tJXZ8jdsh4UFBoDr5RgXbj4SDPNKO4zu2kerFyhQClnLjtzRvp-KMgdAtzsnEC-dl5AMImwP866rTdqTfJRsjFeaCe2j2_GX6Ovvl478JeYYf7qxHnPMiBXqiYp90pwnWkkHnxpjCHQ8DCDi4WKMUz6EzTmcMqrlTQZ6CGKkEbq7E62ootjhd5b6zal1W0uc9LnogmP8XzQWaMuKTUIq9z2O9wqhZP_9QIVQibqr9o4Z7pn6s0r8LiY_TQPqHCjThItXBHML8o5vutbon0EUSfucnqLVfhitEFZ9L1Hpq3DmiyEh5W-yvfD6cCnAhbWwUHYdnKHV99Qk9JrhEkv8K3pk3vLlso28B6T29m_0XZra5aiAZG_Z6FGTbQGUP47Fv0ws7rViVlJLjANo27vg19rYItMf-K4lZ54eNinnLLk6vbErgHmGn3ujnVyvuJiee7pEMRNRjSbE=|
|source|来源标识|string|Trio_Feiyou|




####4.UI 效果展示











