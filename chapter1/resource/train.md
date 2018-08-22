>#火车信息卡片


####1.测试 Demo
{%fbq%}
term:##火车名称##
ner:##TRAIN_NUM##
{%endfbq%}


####2.返回 Json 示例
```json
{
    "from": "青岛",
    "destination": "兰州",
    "start_time": "10:08",
    "end_time": "15:48",
    "mile_age": "",
    "id": "K1026",
    "stationInfo": "[{\"stationarrive\": \"10:08\", \"stationmile\": \"01\", \"stationname\": \"青岛\", \"stationstart\": \"10:08\", \"stationtotal\": \"----\"},{\"stationarrive\": \"11:13\", \"stationmile\": \"02\", \"stationname\": \"蓝村\", \"stationstart\": \"11:16\", \"stationtotal\": \"3min\"},{\"stationarrive\": \"11:32\", \"stationmile\": \"03\", \"stationname\": \"胶州\", \"stationstart\": \"11:35\", \"stationtotal\": \"3min\"},{\"stationarrive\": \"12:43\", \"stationmile\": \"05\", \"stationname\": \"潍坊\", \"stationstart\": \"12:47\", \"stationtotal\": \"4min\"},{\"stationarrive\": \"13:51\", \"stationmile\": \"07\", \"stationname\": \"淄博\", \"stationstart\": \"13:57\", \"stationtotal\": \"6min\"},{\"stationarrive\": \"15:22\", \"stationmile\": \"09\", \"stationname\": \"济南\", \"stationstart\": \"15:37\", \"stationtotal\": \"15min\"},{\"stationarrive\": \"16:29\", \"stationmile\": \"11\", \"stationname\": \"泰山\", \"stationstart\": \"16:42\", \"stationtotal\": \"13min\"},{\"stationarrive\": \"17:40\", \"stationmile\": \"12\", \"stationname\": \"兖州\", \"stationstart\": \"17:43\", \"stationtotal\": \"3min\"},{\"stationarrive\": \"18:21\", \"stationmile\": \"14\", \"stationname\": \"滕州\", \"stationstart\": \"18:25\", \"stationtotal\": \"4min\"},{\"stationarrive\": \"18:47\", \"stationmile\": \"15\", \"stationname\": \"枣庄西\", \"stationstart\": \"18:49\", \"stationtotal\": \"2min\"},{\"stationarrive\": \"19:52\", \"stationmile\": \"16\", \"stationname\": \"徐州\", \"stationstart\": \"20:10\", \"stationtotal\": \"18min\"},{\"stationarrive\": \"21:11\", \"stationmile\": \"17\", \"stationname\": \"砀山\", \"stationstart\": \"21:15\", \"stationtotal\": \"4min\"},{\"stationarrive\": \"23:23\", \"stationmile\": \"24\", \"stationname\": \"开封\", \"stationstart\": \"23:27\", \"stationtotal\": \"4min\"},{\"stationarrive\": \"00:15\", \"stationmile\": \"25\", \"stationname\": \"郑州\", \"stationstart\": \"00:27\", \"stationtotal\": \"12min\"},{\"stationarrive\": \"01:59\", \"stationmile\": \"26\", \"stationname\": \"洛阳\", \"stationstart\": \"02:05\", \"stationtotal\": \"6min\"},{\"stationarrive\": \"06:20\", \"stationmile\": \"28\", \"stationname\": \"渭南\", \"stationstart\": \"06:41\", \"stationtotal\": \"21min\"},{\"stationarrive\": \"07:37\", \"stationmile\": \"29\", \"stationname\": \"西安\", \"stationstart\": \"07:47\", \"stationtotal\": \"10min\"},{\"stationarrive\": \"09:42\", \"stationmile\": \"33\", \"stationname\": \"宝鸡\", \"stationstart\": \"09:48\", \"stationtotal\": \"6min\"},{\"stationarrive\": \"11:27\", \"stationmile\": \"34\", \"stationname\": \"天水\", \"stationstart\": \"11:32\", \"stationtotal\": \"5min\"},{\"stationarrive\": \"12:14\", \"stationmile\": \"35\", \"stationname\": \"甘谷\", \"stationstart\": \"12:26\", \"stationtotal\": \"12min\"},{\"stationarrive\": \"13:15\", \"stationmile\": \"37\", \"stationname\": \"陇西\", \"stationstart\": \"13:19\", \"stationtotal\": \"4min\"},{\"stationarrive\": \"14:15\", \"stationmile\": \"38\", \"stationname\": \"定西\", \"stationstart\": \"14:18\", \"stationtotal\": \"3min\"},{\"stationarrive\": \"15:48\", \"stationmile\": \"39\", \"stationname\": \"兰州\", \"stationstart\": \"15:48\", \"stationtotal\": \"----\"}]",
    "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:SyVs8_lemRqQKWvAERdWznZ_9YlxDiqMxAUvQLHHnZEkJs8NpIhyf9E_4eEjhvZGROrN-tEynA9MhzbSHug5byB_0-g0PrlMmsmO3RPAd4-3E_TMcxx_TLWBMKu0ymwzFt9ztxuhZJquC81L608kQ-aInig1xkXVvytA0LXSC6zH0G7jBN5qcg==",
    "intent": "",
    "source": "BaiduTrain"
}
```

####3.返回字段说明

>卡片字段名称：train_list

|名称|子字段|说明|类型|示例|
|:---|:---|:---|:---|:---|
|from|------|起始地|string|青岛|
|destination|------|目的地|string|兰州|
|start_time|------|起始时间|string|15:37|
|end_time|------|到站时间|string|15:48|
|mile_age|------|总里程|string||
|id|------|火车编号|string|K1026|
|stationInfo|stationmile|至当前车站总里程|string|待定|
|stationInfo|stationstart|出发时间|string|待定|
|stationInfo|stationarrive|到站时间|string|待定|
|stationInfo|stationtotal|时间总和|string|待定|
|stationInfo|stationname|车站名称|string|待定|
|url|火车链接|http://phoneapi.sanjiaoshou.net/nlp/q?key:SyVs8_lemRqQKWvAERdWznZ_9YlxDiqMxAUvQLHHnZEkJs8NpIhyf9E_4eEjhvZGROrN-tEynA9MhzbSHug5byB_0-g0PrlMmsmO3RPAd4-3E_TMcxx_TLWBMKu0ymwzFt9ztxuhZJquC81L608kQ-aInig1xkXVvytA0LXSC6zH0G7jBN5qcg==|
|intent|------|跳转链接|string|------|
|source|------|来源标识|string|BaiduTrain|

####4.UI 效果展示

>火车资源卡片展示

<div align="center">
<img src="/assets/chapter1/huoche.png" align="center" alt="电影资源卡片实例">
</div>



