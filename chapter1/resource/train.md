>#火车信息卡片


####1.测试demo
{%fbq%}
term:##火车名称##
ner:##TRAIN_NUM##
{%endfbq%}


####2.返回 Json 示例


####3.返回字段说明

>卡片字段名称：train_list

|名称|说明|类型|示例|
|:---|:---|:---|:---|
|from|起始地|string|青岛|
|destination|目的地|string|兰州|
|start_time|起始时间|string|15:37|
|end_time|到站时间|string|15:48|
|mile_age|总里程|string||
|id|火车编号|string|K1026|
|stationInfo|车站信息|string||
|stationInfo.stationmile|至当前车站总里程|string|61|
|stationInfo.stationstart|出发时间|string|11:26|
|stationInfo.stationarrive|到站时间|string|11:16|
|stationInfo.stationtotal|时间总和|string|00:45|
|stationInfo.stationname|车站名称|string|东莞东|
|url|火车链接|string|https://kuai.baidu.com/webapp/train/stationlist.html?trainno=K1026|
|intent|跳转链接|string||
|source|来源标识|string|BaiduTrain|

####4.UI 效果展示


