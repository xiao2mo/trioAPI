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
|custom_info|stat|球队状态|string|{\"key\":\"2018世界杯\",\"win_score\":\"1\",\"draw_score\":\"1\",\"fail_score\":\"2\"}|
|custom_info|rank|球队排名|string|{\"key\":\"FIFA排名\",\"value\":\"5\"}|
|custom_info|tag|球员标签|string|------|
|url|------|球队链接|string|http://kg.sanjiaoshou.net/football/1/football_team/html/index.html?uid=50000067&log_id=bfc6f91c-88fa-49cf-9078-856505a4f300|


####4.UI 效果展示
>球队资源卡片展示

<div align="center">
<img src="/assets/chapter1/agenting.png" align="center" alt="电影资源卡片实例">
</div>

>世界杯资源卡片展示（可定制）

<div align="center">
<img src="/assets/chapter1/shijiebei.png" align="center" alt="电影资源卡片实例">
</div>










