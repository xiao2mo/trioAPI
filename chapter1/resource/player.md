>#常见球员卡片


####1.测试 Demo
{%fbq%}
term:##球员名称##
ner:##SPORTS_PLAYER##
{%endfbq%}
####2.返回 Json 示例
```json
{
    "cn_name": "内马尔",
    "birthday": "1992-02-05",
    "pic_url": "http://kg.sanjiaoshou.net/footballImg/players/50069499",
    "custom_info": [
        {
            "birthday": "1992-02-05",
            "number": "10",
            "stat": "{\"key\":\"2018世界杯\",\"score\":\"2\",\"assist\":\"1\"}",
            "nation": "巴西",
            "postion": "前锋",
            "club": "巴黎圣日耳曼",
            "tag": "助攻榜第二"
        }
    ],
    "url": "http://kg.sanjiaoshou.net/football/1/worldcup/html/index.html?uid=50069499&log_id=c4f46fa1-abb8-4382-81a2-cba80b009dc4"
}
```

####3.返回字段说明
>卡片字段名称：custom_player_list

|名称|子字段|说明|类型|示例|
|:---|:---|:---|:---|:---|
|cnname|------|中文名称|string|内马尔|
|birthday|------|球员名称|string|1992-02-05|
|pic_url|------|图片地址|string|http://kg.sanjiaoshou.net/footballImg/players/50069499|
|custom_info|birthday|球员生日|string|1992-02-05|
|custom_info|number|球员编号|string|10|
|custom_info|stat|球员状态|string|{\"key\":\"2018世界杯\",\"score\":\"2\",\"assist\":\"1\"}|
|custom_info|nation|球员国家|string|巴西|
|custom_info|postion|球员位置|string|前锋|
|custom_info|club|俱乐部名称|string|无巴黎圣日耳曼|
|custom_info|tag|球员标签|string|助攻榜第二|
|url|------|球员链接|string|http://kg.sanjiaoshou.net/football/1/worldcup/html/index.html?uid=50069499&log_id=c4f46fa1-abb8-4382-81a2-cba80b009dc4|
####4.UI 效果展示

>球员资源卡片展示

<div align="center">
<img src="/assets/chapter1/film.png" align="center" alt="电影资源卡片实例">
</div>





