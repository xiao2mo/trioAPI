>#常见球队卡片


####1.测试 Demo
{%fbq%}
term:##球队名称##
ner:##SPORTS_TEAM##
{%endfbq%}
####2.返回 Json 示例
```json
{
    "name": "阿根廷",
    "pic_url": "https://img.dongqiudi.com/data/pic/132.png",
    "custom_info": [
        {
            "stat": "{\"key\":\"2018世界杯\",\"win_score\":\"1\",\"draw_score\":\"1\",\"fail_score\":\"2\"}",
            "rank": "{\"key\":\"FIFA排名\",\"value\":\"5\"}",
            "tag": ""
        }
    ],
    "url": "http://kg.sanjiaoshou.net/football/1/football_team/html/index.html?uid=50000067&log_id=bfc6f91c-88fa-49cf-9078-856505a4f300"
}
```

####3.返回字段说明
>卡片字段名称：custom_team_list

|名称|子字段|说明|类型|示例|
|:---|:---|:---|:---|:---|
|cnname|------|中文名称|string|阿根廷|
|pic_url|------|图片地址|string|https://img.dongqiudi.com/data/pic/132.png|
|custom_info|birthday|球员生日|string|1992-02-05|
|custom_info|number|球员编号|string|10|
|custom_info|stat|球员状态|string|{\"key\":\"2018世界杯\",\"score\":\"2\",\"assist\":\"1\"}|
|custom_info|nation|球员国家|string|巴西|
|custom_info|postion|球员位置|string|前锋|
|custom_info|club|俱乐部名称|string|无巴黎圣日耳曼|
|custom_info|tag|球员标签|string|助攻榜第二|
|url|------|球员链接|string|http://kg.sanjiaoshou.net/football/1/worldcup/html/index.html?uid=50069499&log_id=c4f46fa1-abb8-4382-81a2-cba80b009dc4|


####4.UI 效果展示




