>#地图资源卡片


####1.测试demo
{%fbq%}
term:##地点名称##
ner:##ADMIN##
{%endfbq%}
####2.返回 Json 示例


####3.返回字段说明

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


