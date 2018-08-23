># 在线获取资源

####1.在线获取资源增量参数
>新增实体结构体 NluTerms，其包含的字段如下所示：

|参数名|参数含义|类型|示例|是否必须|
|:---|:---|:---|:---|:---|
|ner|实体名称|string|-|y|
|word|实体内容|string|-|y|


####2.请求 json 示例
```json
{
  "userId": "11000",
  "longitude": 113.937862,
  "latitude": 22.521726,
  "gpsType": "GCJ02",
  "timestamp":1535026759,
  "signature":b893e573bb320bd0ba2f51fe873cb5a897c9ef46,
  "nluTerms": [
    {
      "word": "七天连锁酒店",
      "ner": "HOTEL",
      "offset": "0"
    }
  ]
}

```

####3.返回 json 结构
>下表中各类资源卡片的具体信息，可参照智慧识屏部分各类卡片的请求、结构和展现。

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
```json
{
    "error_code": 0,
    "error_msg": "success",
    "result_list": [
        {
            "divided_list": [],
            "domain_list": [],
            "term_list": [
                {
                    "token": "七天连锁酒店",
                    "ner": "HOTEL",
                    "offset": 0,
                    "ner_prob": 0,
                    "address_list": [
                        {
                            "name": "七天连锁酒店",
                            "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:L9jI2NvDhiGnXXA5hCoXXWdM5jwzvVUJZ1TPn99uMROc18HcoZDAnN8rvX2GTZY6nCRrXai-_uRVI7Z3zZgVZd3a44Gfy1YVIrJSV88UtozEuyUXtR6kNbfcEjTpQXLryMttsH5t8Yybyo_Qyb1q1BbeIBlwQY2cgfph3MstTtvyzUE2OG1Ouw==",
                            "intent": "androidamap://poi?sourceApplication=trio&dev=0&keywords=%E4%B8%83%E5%A4%A9%E8%BF%9E%E9%94%81%E9%85%92%E5%BA%97"
                        },
                        {
                            "name": "七天连锁酒店",
                            "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:Dgf0Y2xbrvC09krvHAA-1IUcl46DTmGY8TsavqA1sIPI4Eq0-7xUmyPlSy5c_icKokbvSV7V68H5PaITiQBERTSPl554z6zkFDr4ZivJ_rAPiZ09hMfi4jGydwOxnhTrZKxuhp9WzmJcQMj_tnF27X25L5wNVbmTIxIili_i-ICCjcx2mDgeS0xPuqrMQSiZjvCCy_2MOrDhJxVrawMm4z-Jz2hosits",
                            "intent": "baidumap://map/geocoder?src=trio&address=%E4%B8%83%E5%A4%A9%E8%BF%9E%E9%94%81%E9%85%92%E5%BA%97"
                        }
                    ],
                    "meituan_list": [
                        {
                            "id": "77240963",
                            "name": "7天优品酒店（深圳南山地铁站店）",
                            "cityname": "深圳",
                            "address": "南山区南山大道与桂庙路口交汇处光彩新世纪1楼，南山地铁站D出口旁",
                            "frontimg": "http://p1.meituan.net/tdchotel/f024b16f27b7d8472a87cc0f39817cd524213.jpg",
                            "openinfo": "",
                            "cate": "酒店",
                            "subcate": "经济型酒店",
                            "price": "￥0.0",
                            "point": "4.7",
                            "phone": "0755-86358777",
                            "lat": "22.523221",
                            "lng": "113.923668",
                            "gpsType": "GCJ02",
                            "thumbNail": "http://api.map.baidu.com/staticimage/v2?ak=ERcMaGj5nOE3EdvHYEEIKBeavMDpEkex&mcode=666666&width=480&height=360&zoom=18&center=113.93019,22.528992&markers=113.93019,22.528992",
                            "wifi": "0",
                            "waimai": "0",
                            "subSource": "meituan",
                            "comments": [
                                {
                                    "content": "房间太小，还有味，窗户内窗",
                                    "time": "1534940459",
                                    "imgurls": [],
                                    "rating": "20"
                                },
                                {
                                    "content": "#位置繁华##非常干净##价格划算#",
                                    "time": "1534655516",
                                    "imgurls": [],
                                    "rating": "50"
                                },
                                {
                                    "content": "还不错，就是洗澡的比较小",
                                    "time": "1533375832",
                                    "imgurls": [],
                                    "rating": "30"
                                },
                                {
                                    "content": "洗澡间太小了，其他还好",
                                    "time": "1533375772",
                                    "imgurls": [],
                                    "rating": "30"
                                },
                                {
                                    "content": "和还来就菊花好？！？，",
                                    "time": "1533186984",
                                    "imgurls": [],
                                    "rating": "10"
                                }
                            ],
                            "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:aDM79-CtElTCnTpD-YEa5ZjAYnJMM7dl0nkQsh_BSHvJXfyZZd1EMIBxm-4JFeApnzA--eqvLTAPAg2iz1yf1DMQdEWGzNQAmi7nSkeERbf_owUZVCuLA6psRtkxgRnWm2t4l8OzDTA62aW-BE5C9yG3BU6aPVe_CcVSKJhcOCX164SZdHaxPgz1eq_3MOWeSCbdCU2e1urNoadrzROt1yso-SB_KGZmzzjggQiWP5MyhLoyba4591wvZ_lLYmuIpt3oHJoSlnmeV6Y756O8fTbJoWaBAlSk",
                            "intent": "imeituan://www.meituan.com/merchant?id=77240963",
                            "source": "meituanTuangou"
                        },
                        {
                            "id": "1514803",
                            "name": "7天连锁酒店（深圳南油店）",
                            "cityname": "深圳",
                            "address": "南山区向南路36号贵航大厦",
                            "frontimg": "http://p1.meituan.net/tdchotel/656a155e6763741d5030aa996aaaa6c7475019.jpg",
                            "openinfo": "24小时营业",
                            "cate": "酒店",
                            "subcate": "经济型酒店",
                            "price": "￥150.0",
                            "point": "4.3",
                            "phone": "0755-86371399",
                            "lat": "22.510016",
                            "lng": "113.922552",
                            "gpsType": "GCJ02",
                            "thumbNail": "http://api.map.baidu.com/staticimage/v2?ak=ERcMaGj5nOE3EdvHYEEIKBeavMDpEkex&mcode=666666&width=480&height=360&zoom=18&center=113.929085,22.515804&markers=113.929085,22.515804",
                            "wifi": "1",
                            "waimai": "0",
                            "subSource": "bdLocalSearch",
                            "url": "http://r.union.meituan.com/url/viset/?key=9a0f5d17c6edb18445a3e76f172f3d39683&sid=trioai-default&url=https://i.meituan.com/poi/1514803",
                            "intent": "imeituan://www.meituan.com/merchant?id=1514803"
                        },
                        {
                            "id": "60429021",
                            "name": "7天连锁酒店（深圳机场后瑞地铁站店）",
                            "cityname": "深圳",
                            "address": "宝安区西乡街道后瑞社区爱民路5号C栋（后瑞地铁站B出口约200米）",
                            "frontimg": "http://p1.meituan.net/tdchotel/ad58ca29008d6898eab22839c77fa47d7104837.jpg",
                            "openinfo": "",
                            "cate": "酒店",
                            "subcate": "经济型酒店",
                            "price": "￥0.0",
                            "point": "4.8",
                            "phone": "0755-29987377",
                            "lat": "22.62946",
                            "lng": "113.83753",
                            "gpsType": "GCJ02",
                            "thumbNail": "http://api.map.baidu.com/staticimage/v2?ak=ERcMaGj5nOE3EdvHYEEIKBeavMDpEkex&mcode=666666&width=480&height=360&zoom=18&center=113.84406,22.63525&markers=113.84406,22.63525",
                            "wifi": "0",
                            "waimai": "0",
                            "subSource": "bdRegionSearch",
                            "url": "http://r.union.meituan.com/url/viset/?key=9a0f5d17c6edb18445a3e76f172f3d39683&sid=trioai-default&url=https://i.meituan.com/poi/60429021",
                            "intent": "imeituan://www.meituan.com/merchant?id=60429021"
                        }
                    ],
                    "baidu_poi_list": [
                        {
                            "id": "fc7675243834e6e34e776e7c",
                            "gpsType": "GCJ02",
                            "phone": "(0755)86371399",
                            "name": "7天连锁酒店(深圳南油店)",
                            "address": "广东省深圳市南山区向南路48号贵航大厦",
                            "lat": "22.51009695155137",
                            "lng": "113.92253740579383",
                            "subSource": "bdLocalSearch",
                            "thumbnail": "http://api.map.baidu.com/staticimage/v2?ak=ERcMaGj5nOE3EdvHYEEIKBeavMDpEkex&mcode=666666&width=480&height=360&zoom=18&center=113.929069,22.515886&markers=113.929069,22.515886",
                            "relScore": 0.8133333333333332,
                            "url": "https://api.map.baidu.com/geocoder?output=html&src=trio&address=7%E5%A4%A9%E8%BF%9E%E9%94%81%E9%85%92%E5%BA%97%28%E6%B7%B1%E5%9C%B3%E5%8D%97%E6%B2%B9%E5%BA%97%29",
                            "intent": "baidumap://map/geocoder?src=trio&address=7天连锁酒店(深圳南油店)",
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