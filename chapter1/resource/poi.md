>#地图资源卡片


####1.测试 Demo
{%fbq%}
term:##地点名称##
ner:##ADMIN##
{%endfbq%}
####2.返回 Json 示例
>示例一：address_list

```json
{
    {
        "name": "肯德基",
        "url": "http://phoneapi.sanjiaoshou.net/nlp/qkey:L9jI2NvDhiH9VyzMs3BTSDg_x5ueFGYOXELOAckkUQkZ1ib0p03XqZK00dzxrvi8tP1vm5c06DryDUF-HUC2cVkwI2-kYRlywQ2arcmDZ0g12woSxB9_JYEZlw5Da_czDHBdHG9VsRs=",
        "intent": "androidamap://poi?sourceApplication=trio&dev=0&keywords=%E8%82%AF%E5%BE%B7%E5%9F%BA"
    },
    {
        "name": "肯德基",
        "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:Dgf0Y2xbrvAV0PjsGUg82a_KC9JVt_YYVcyAPzo_O1nu0w2BigEm-1DYgrh116PDButxCMIqwqRtqEE2y4t5XFTg_IMO2DvfEr1-tkuUAX16kMwdFsEWELeFpwUF-CP1MBO1h_TcA3coFXsCF7S68LEgunV8tV3mQgGn3mX7GJI=",
        "intent": "baidumap://map/geocoder?src=trio&address=%E8%82%AF%E5%BE%B7%E5%9F%BA"
    }
}
```

>示例二：baidu_poi_list

```json
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
    "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:QKyOG0SrO01xXiVNO2x80LCED-FjiEE8n0ICBZHZzE-fDjNgTdXweeByT99Itmq-Ic-PmHQJtX30jR6mbd4H-_unwoeHH8RRPtrEv_XVkGVbzF3Ut1shf9XRFwnNykeF8TwzKnS_XnlEmC_XBj1sTi7DWuw3NhrMpRcdi3dPI0_VSn-EAv2_mHTSZm0rpwERDplUiTMKP4oAvS9FecZKaTAWyvCgUjmbNe7rNRGB4f4pQQ5BGaFD5NJop7UFDzMMbUtvDCp4gouLmKPm-UNr2g==",
    "intent": "baidumap://map/geocoder?src=trio&address=肯德基(保利餐厅)",
    "source": "locBaidu"
}
```


####3.返回字段说明

>卡片字段名称：address_list

|名称|说明|类型|示例|
|:---|:---|:---|:---|


>卡片字段名称：baidu_poi_list

|名称|说明|类型|示例|
|:---|:---|:---|:---|
|id|地址id|string|3dee767333bdcf173586f447|
|gpsType|GPS类型|string|GCJ02|
|name|POI名称|string|五道口保理学院|
|address|具体地址|string|深圳市南山区桃园路8号田厦国际中心B座1918室|
|lat|经度|string|22.53270639342764|
|lng|纬度|string|113.92731915040862|
|subSource|兜底资源|string|bdLocalSearch|
|thumbnail|地址缩略图|string|http://api.map.baidu.com/staticimage/v2?ak=ERcMaGj5nOE3EdvHYEEIKBeavMDpEkex&mcode=666666&width=480&height=360&zoom=18&center=113.933853,22.538433&markers=113.933853,22.538433|
|relScore|百度链接|string|1|
|url|百度链接|string|http://map.baidu.com/?l=&s=s%26wd%3D五道口保理学院|
|intent|跳转链接|string|baidumap://map/geocoder?src=openApiDemo&address=五道口保理学院|
|source|来源标识|string|locBaidu|


####4.UI 效果展示


