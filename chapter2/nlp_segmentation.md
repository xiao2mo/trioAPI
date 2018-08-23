># 在线识别

在线识别部分分为两个接口，分别是 segmentation 接口和 nlp 接口。

####1.在线识别增量参数

|参数名|参数含义|类型|示例|是否必须|
|:---:|:---:|:---:|:---:|:---:|
|query|用户检索语句|string|"我想去吃肯德基"|y|


####2.请求 json 示例
>请求接口：segmentation
>请求地址：http://phoneapi.sanjiaoshou.net/nlp/segmentation
>请求 json：如下所示

```json
{
  "userId": "trio",
  "longitude": 113.937862,
  "latitude": 22.521726,
  "gpsType": "GCJ02",
  "timestamp":1535026759,
  "signature":b893e573bb320bd0ba2f51fe873cb5a897c9ef46,
  "query":"我想去吃肯德基" 
}
```

-----------------------------
>请求接口：nlp
>请求地址：http://phoneapi.sanjiaoshou.net/nlp
>请求 json：如下所示

```json
{
  "userId": "trio",
  "longitude": 113.937862,
  "latitude": 22.521726,
  "gpsType": "GCJ02",
  "timestamp":1535026759,
  "signature":b893e573bb320bd0ba2f51fe873cb5a897c9ef46,
  "query":"我想去吃肯德基" 
}

```


####3.返回 json 结构
>下表中各类资源卡片的具体信息，可参照智慧识屏部分各类卡片的请求、结构和展现。

>请求接口：segmentation
>返回字段：如下表

|字段名称|子字段|字段含义|字段类型|
|:---:|:---:|:---:|:---:|
|error_code|------|返回状态码|int|
|error_msg|------|返回状态信息|string|
|query|------|用户检索|string|
|result_list|（下方 ** 开头的项为其子元素）|结果列表|list|
|**divided_list|------|分词列表|list|
|** domain_list|name|领域名称|string|
|** domain_list|value|领域概率|float|
|** term_list|token|实体词|string|
|** term_list|ner|实体类别|string|
|log_id|------|请求 id|string|




--------------------------------------------------

>请求接口：nlp
>返回字段：如下表

|字段名称|子字段|字段含义|字段类型|
|:---:|:---:|:---:|:---:|
|error_code|------|返回状态码|int|
|error_msg|------|返回状态信息|string|
|query|------|用户检索|string|
|result_list|（下方 ** 开头的项为其子元素）|结果列表|list|
|** divided_list|------|分词列表|list|
|** domain_list|name|领域名称|string|
|** domain_list|value|领域概率|float|
|** term_list|token|实体词|string|
|** term_list|ner|实体类别|string|
|** term_list|offset|槽位偏移|string|
|** term_list|ner_prob|实体概率|float|
|** term_list|film_list|电影资源|float|
|** term_list|custom_player_list|球员资源|float|
|** term_list|custom_team_list|球队资源|float|
|** term_list|travel_poi_list|景点资源|float|
|** term_list|cinemaInfo_list|影院资源|float|
|** term_list|book_list|图书资源|float|
|** term_list|cater_list|餐馆资源|float|
|** term_list|waimai_list|外卖资源|float|
|** term_list|taokouling_list|淘口令资源|float|
|** term_list|feiyou_flight_list|飞机票资源|float|
|** term_list|train_list|火车资源|float|
|** term_list|address_list|地址资源|float|
|** term_list|person_list|人物资源|float|
|** term_list|plant_list|植物资源|float|
|** term_list|animal_list|动物资源|float|
|** term_list|meituan_list|美团资源|float|
|** term_list|stock_list|股票资源|float|
|** term_list|wangyi_music_list|音乐资源|float|
|** term_list|jd_ware_list|商品资源|float|
|** term_list|calendar_list|日程资源|float|
|** term_list|kuaidi_list|快递资源|float|
|** term_list|baidu_poi_list|地图资源|float|
|** custom_info_list|------|通用卡片资源|list|


####4.返回 json 示例

>请求接口：segmentation
>返回字段：如下所示

```json
{
    "error_code": 0,
    "error_msg": "success",
    "query": "我想去吃肯德基",
    "result_list": [
        {
            "divided_list": [
                "我",
                "想",
                "去",
                "吃",
                "肯德基"
            ],
            "domain_list": [
                {
                    "name": "美食",
                    "value": 0.9472566843032837
                },
                {
                    "name": "其它",
                    "value": 0.02021510899066925
                },
                {
                    "name": "地图",
                    "value": 0.014596251770853996
                }
            ],
            "term_list": [
                {
                    "token": "我",
                    "ner": "O"
                },
                {
                    "token": "想",
                    "ner": "O"
                },
                {
                    "token": "去",
                    "ner": "O"
                },
                {
                    "token": "吃",
                    "ner": "O"
                },
                {
                    "token": "肯德基",
                    "ner": "CATER"
                }
            ]
        }
    ],
    "log_id": "9f6e34dd-4744-4055-b8d0-843690d43bd4"
}
```



-------------------------------------------------
>请求接口：nlp
>返回字段：如下所示


```json
{
    "error_code": 0,
    "error_msg": "success",
    "query": "我想去吃肯德基",
    "log_id": "26a740ac-4729-4af6-a0ee-21c745deb63c",
    "result_list": [
        {
            "divided_list": [
                "我",
                "想",
                "去",
                "吃",
                "肯德基"
            ],
            "domain_list": [
                {
                    "name": "美食",
                    "value": 0.9472566843032837
                },
                {
                    "name": "其它",
                    "value": 0.02021510899066925
                },
                {
                    "name": "地图",
                    "value": 0.014596251770853996
                }
            ],
            "term_list": [
                {
                    "token": "我",
                    "ner": "O",
                    "offset": 0,
                    "ner_prob": 0.9999748468399048
                },
                {
                    "token": "想",
                    "ner": "O",
                    "offset": 0,
                    "ner_prob": 0.9999933242797852
                },
                {
                    "token": "去",
                    "ner": "O",
                    "offset": 0,
                    "ner_prob": 0.9999969005584717
                },
                {
                    "token": "吃",
                    "ner": "O",
                    "offset": 0,
                    "ner_prob": 0.9998648166656494
                },
                {
                    "token": "肯德基",
                    "ner": "CATER",
                    "offset": -1,
                    "ner_prob": 0,
                    "address_list": [
                        {
                            "name": "肯德基",
                            "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:L9jI2NvDhiH9VyzMs3BTSDg_x5ueFGYOXELOAckkUQkZ1ib0p03XqZK00dzxrvi8tP1vm5c06DryDUF-HUC2cVkwI2-kYRlywQ2arcmDZ0g12woSxB9_JYEZlw5Da_czDHBdHG9VsRs=",
                            "intent": "androidamap://poi?sourceApplication=trio&dev=0&keywords=%E8%82%AF%E5%BE%B7%E5%9F%BA"
                        },
                        {
                            "name": "肯德基",
                            "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:Dgf0Y2xbrvAV0PjsGUg82a_KC9JVt_YYVcyAPzo_O1nu0w2BigEm-1DYgrh116PDButxCMIqwqRtqEE2y4t5XFTg_IMO2DvfEr1-tkuUAX16kMwdFsEWELeFpwUF-CP1MBO1h_TcA3coFXsCF7S68LEgunV8tV3mQgGn3mX7GJI=",
                            "intent": "baidumap://map/geocoder?src=trio&address=%E8%82%AF%E5%BE%B7%E5%9F%BA"
                        }
                    ],
                    "meituan_list": [
                        {
                            "id": "179185504",
                            "name": "肯德基（科园店）",
                            "cityname": "深圳",
                            "address": "南山区海天一路16号软件产业基地5栋裙楼01层28号",
                            "frontimg": "",
                            "openinfo": "周一至周日\n10:00-22:00",
                            "cate": "美食",
                            "subcate": "小吃快餐",
                            "price": "￥0.0",
                            "point": "0.0",
                            "phone": "13686493637",
                            "lat": "22.523795",
                            "lng": "113.940367",
                            "gpsType": "GCJ02",
                            "thumbNail": "http://api.map.baidu.com/staticimage/v2?ak=ERcMaGj5nOE3EdvHYEEIKBeavMDpEkex&mcode=666666&width=480&height=360&zoom=18&center=113.946915,22.52945&markers=113.946915,22.52945",
                            "wifi": "0",
                            "waimai": "0",
                            "subSource": "meituan",
                            "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:J8Vfos5KMouAhYX9AKXko7V0BsXq2rc38_XzSreTSNXvGAxLXqCBpX21UT8YgTOhRUAlcid7If1pz7ZeXIvqGz00cVw8mrsmvY7RnOKRgeAnokSAdFmrwV-Jz2RaodxfHKpydlsehr2MMLetIoLKm9nGrsbOF6P1fvp4005JbEjhUDcoNw0Et02wcvC3iyjV780SBEHNFGBMCcAH7M4EsVQlBXpcI6LsPch01xZtRhKBa2nSKwGs1tXTJnUbe2L5kXt-SgOjlWvGaGzf7NbuZA==",
                            "intent": "imeituan://www.meituan.com/merchant?id=179185504",
                            "source": "meituanTuangou"
                        },
                        {
                            "id": "617652",
                            "name": "肯德基（保利文化广场店）",
                            "cityname": "深圳",
                            "address": "南山区文心五路保利文化广场1层",
                            "frontimg": "https://img.meituan.net/msmerchant/4f63c1475c1e6edaa2210d7416145f8b120120.jpg",
                            "openinfo": "周一至周日\n全天",
                            "cate": "美食",
                            "subcate": "小吃快餐",
                            "price": "￥28.0",
                            "point": "4.0",
                            "phone": "0755-86287286",
                            "lat": "22.51725",
                            "lng": "113.937201",
                            "gpsType": "GCJ02",
                            "thumbNail": "http://api.map.baidu.com/staticimage/v2?ak=ERcMaGj5nOE3EdvHYEEIKBeavMDpEkex&mcode=666666&width=480&height=360&zoom=18&center=113.943756,22.52291&markers=113.943756,22.52291",
                            "wifi": "1",
                            "waimai": "1",
                            "subSource": "bdLocalSearch",
                            "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:J8Vfos5KMouAhYX9AKXko7V0BsXq2rc38_XzSreTSNXvGAxLXqCBpX21UT8YgTOhRUAlcid7If1pz7ZeXIvqGz00cVw8mrsmvY7RnOKRgeAnokSAdFmrwV-Jz2RaodxfHKpydlsehr2MMLetIoLKm9nGrsbOF6P1fvp4005JbEjhUDcoNw0Et02wcvC3iyjV780SBEHNFGBMCcAH7M4EsVQlBXpcI6LsPch01xZtRhKBa2nSKwGs1tXTJnUbe2L5bMu2BeFt89MWlzzARqf11g==",
                            "intent": "imeituan://www.meituan.com/merchant?id=617652"
                        },
                        {
                            "id": "78445348",
                            "name": "肯德基（五山店）",
                            "cityname": "广州",
                            "address": "天河区五山岳洲路8号首,二层",
                            "frontimg": "https://img.meituan.net/msmerchant/4f63c1475c1e6edaa2210d7416145f8b120120.jpg",
                            "openinfo": "周一至周日\n全天",
                            "cate": "美食",
                            "subcate": "小吃快餐",
                            "price": "￥31.0",
                            "point": "4.0",
                            "phone": "020-85284721",
                            "lat": "23.152384",
                            "lng": "113.35223",
                            "gpsType": "GCJ02",
                            "thumbNail": "http://api.map.baidu.com/staticimage/v2?ak=ERcMaGj5nOE3EdvHYEEIKBeavMDpEkex&mcode=666666&width=480&height=360&zoom=18&center=113.35877,23.15811&markers=113.35877,23.15811",
                            "wifi": "0",
                            "waimai": "1",
                            "subSource": "bdRegionSearch",
                            "comments": [
                                {
                                    "content": "最喜欢新奥尔良烤翅和鸡米花啦，豆浆也挺好的。地理位置很便利，就在五山b出口，所以很好找。中午去的时候人比较多，虽然有二层但是位子还不是不够，人多的时候都排到门口了。店员服务态度挺好的，工作麻利的。",
                                    "time": "1419695089",
                                    "imgurls": [],
                                    "rating": "40"
                                }
                            ],
                            "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:J8Vfos5KMouAhYX9AKXko7V0BsXq2rc38_XzSreTSNXvGAxLXqCBpS6fJfqAAm1pcNsHoCQ15DvaZHA6SQOPGQp3bxSmDGwjWu0U28QkJuTInCLsRDNUDLpdAaQRrH2sJzPIgZRykYHf_hx_qD3gaRahOyY7wwYArAgFzzaxuk8SRZZEPWpNOiSTil9hD_h0Jsvj-kqrduJ2LeD6Y3THNA7Ig-CTjh072Qx_8aOnXKAcJEfMiuZqarDo1klhhQvRwmNVT-ucMdg=",
                            "intent": "imeituan://www.meituan.com/merchant?id=78445348"
                        }
                    ],
                    "baidu_poi_list": [
                        {
                            "id": "d6c5d9917f3c89f131169b92",
                            "gpsType": "GCJ02",
                            "phone": "(0755)86287286",
                            "name": "肯德基(保利餐厅)",
                            "address": "深圳市南山区文心六路保利文化广场F1",
                            "lat": "22.51712327259213",
                            "lng": "113.93720325174111",
                            "subSource": "bdLocalSearch",
                            "thumbnail": "http://api.map.baidu.com/staticimage/v2?ak=ERcMaGj5nOE3EdvHYEEIKBeavMDpEkex&mcode=666666&width=480&height=360&zoom=18&center=113.943755,22.522782&markers=113.943755,22.522782",
                            "relScore": 1,
                            "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:J8Vfos5KMouAhYX9AKXko7V0BsXq2rc38_XzSreTSNXvGAxLXqCBpX21UT8YgTOhRUAlcid7If1pz7ZeXIvqG28g_gVOLOnBk7SJAVEndhKHqWBVsbctaPo7rqqHD_RMMZyg1ZGlftfsByLLHTqTP8ZRJ1AbJInwKZ3SIXOj-FHPqeKxDG13r3IxWGZg2ZGCE2DkAkwwTkjmF3KGGCGtjieHqRAieHiyRQvCp2QBpE4LIs78q1WudbnHdo2i6vSMJHfXWxe1ZpyzGLEbLg4HcQ==",
                            "intent": "baidumap://map/geocoder?src=trio&address=肯德基(保利餐厅)",
                            "source": "locBaidu"
                        }
                    ]
                }
            ],
            "custom_info_list": []
        }
    ]
}
```



