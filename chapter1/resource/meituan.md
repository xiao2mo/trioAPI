>#美团卡片

####1.测试 Demo
{%fbq%}
term:##餐馆名称##
ner:##CATER##
{%endfbq%}
####2.返回 Json 示例
```json
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
    "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:QKyOG0SrO01xXiVNO2x80LCED-FjiEE8n0ICBZHZzE-fDjNgTdXweeByT99Itmq-Ic-PmHQJtX30jR6mbd4H-yxJL9QcIFwf8ZwHJCGz1wV6sn3UXckbIye8_2m8SbKX7GKDOfSM_yBMISRxA3dTp7mWwt84m9bcWy9CTHe19VHVS0tZuEfIR2xXAGt4sslGwMfY-BOUIOMnIHi_kUqOOJ0RbHzkWGILqc7cCZSQylNFtlVgA9uszieM2qCIUGZobnRBO59uu2FIlmN_dwRLfQ==",
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
    "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:QKyOG0SrO01xXiVNO2x80LCED-FjiEE8n0ICBZHZzE-fDjNgTdXweeByT99Itmq-Ic-PmHQJtX30jR6mbd4H-yxJL9QcIFwf8ZwHJCGz1wV6sn3UXckbIye8_2m8SbKX7GKDOfSM_yBMISRxA3dTp7mWwt84m9bcWy9CTHe19VHVS0tZuEfIR2xXAGt4sslGwMfY-BOUIOMnIHi_kUqOOJ0RbHzkWGILqc7cCZSQylNFtlVgA9uszieM2qCIUGZoedCCfzRX2Iqb8yHfcemn2A==",
    "intent": "imeituan://www.meituan.com/merchant?id=617652"
                        },
                        {
    "id": "600681",
    "name": "肯德基（六约店）",
    "cityname": "深圳",
    "address": "龙岗区横岗镇深惠公路新亚洲广场首层",
    "frontimg": "https://img.meituan.net/msmerchant/4f63c1475c1e6edaa2210d7416145f8b120120.jpg",
    "openinfo": "",
    "cate": "美食",
    "subcate": "小吃快餐",
    "price": "￥27.0",
    "point": "4.0",
    "phone": "0755-28628083",
    "lat": "22.64211",
    "lng": "114.196602",
    "gpsType": "GCJ02",
    "thumbNail": "http://api.map.baidu.com/staticimage/v2?ak=ERcMaGj5nOE3EdvHYEEIKBeavMDpEkex&mcode=666666&width=480&height=360&zoom=18&center=114.203125,22.647886&markers=114.203125,22.647886",
    "wifi": "0",
    "waimai": "1",
    "subSource": "bdRegionSearch",
    "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:QKyOG0SrO01xXiVNO2x80LCED-FjiEE8n0ICBZHZzE-fDjNgTdXweb4VQMXMlqsvfrAqDoPmsgkBAXMAInDRhEVf7LQSzaNJpymAly1pNXvzBtYQroT1kZsgOJUINUBsie5y5HAJN1nmlfKsn_OmvjsQv00NxjYN-dogsawvz2Bvb1-meG7-OiKEmNaFK0x9b549mFlzoqm68ilp3xvu_0jzrO9xzgkOR6w1nrgUQZK0xM6hVj7IoSkdpZ8odoqfWsfWlIGOWa8=",
    "intent": "imeituan://www.meituan.com/merchant?id=600681"
                        }
}
```

####3.返回字段说明

>卡片字段名称：meituan_list(以返回的第一个资源为例)

|名称|说明|类型|示例|
|:---|:---|:---|:---|
|id|美团id|string|179185504|
|name|餐馆名称|string|肯德基（科园店）|
|cityname|城市名称|string|深圳|
|address|餐馆地址|string|南山区海天一路16号软件产业基地5栋裙楼01层28号|
|frontimg|餐馆图片|string|------|
|openinfo|营业信息|string|周一至周日\n10:00-22:00|
|cate|主类别|string|美食|
|subcate|次类别|string|小吃快餐|
|price|价格|string|￥0.0|
|point|评分|string|0.0|
|phone|联系方式|string|13686493637|
|lat|经度|string|22.523688|
|lng|纬度|string|113.941458|
|gpsType|GPS类型|string|GCJ02|
|thumbNail|地理缩略图|string|http://api.map.baidu.com/staticimage/v2?ak=ERcMaGj5nOE3EdvHYEEIKBeavMDpEkex&mcode=666666&width=480&height=360&zoom=18&center=113.948006,22.529343&markers=113.948006,22.529343|
|wifi|是否支持wifi|string|0|
|waimai|是否提供外卖|string|1|
|subSource|兜底资源|string|meituan|
|url|美团链接|string|https://kuai.baidu.com/webapp/train/stationlist.html?trainno=K1026|
|intent|跳转链接|string||
|source|来源标识|string|BaiduTrain|

####4.UI 效果展示














