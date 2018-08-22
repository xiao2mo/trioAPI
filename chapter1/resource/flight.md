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

####3.返回字段说明

>卡片字段名称：flight_list

|名称|说明|类型|示例|
|:---|:---|:---|:---|
|id|航班id|string|KN5987|
|depCity|起始城市|string|北京|
|arrCity|目标城市|string|上海|
|url|航班链接|string|http://m.veryzhun.com/flight/details.html?fnum=KN5987&n_calendar=2018-05-18&token=edea7b58ec74c0202774394e0e884383|

####4.UI 效果展示











