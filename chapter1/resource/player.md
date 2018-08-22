>#常见球员卡片


####1.测试 Demo
{%fbq%}
term:##球员名称##
ner:##SPORTS_PLAYER##
{%endfbq%}
####2.返回 Json 示例
```json
{
    "cn_name": "罗纳尔多",
    "birthday": "1996-08-22",
    "pic_url": "https://img.dongqiudi.com/soccer/data/logo/person/234055.jpg",
    "custom_info": [
        {
            "birthday": "1996-08-22",
            "number": "12号",
            "stat": "{\"key\":\"2018世界杯\",\"score\":\"0\",\"assist\":\"0\"}",
            "nation": "巴西",
            "postion": "守门员",
            "club": "维多利亚",
            "tag": ""
        }
    ],
    "url": "http://kg.sanjiaoshou.net/football/1/worldcup/html/index.html?uid=50234055&log_id=af5f9846-57b1-4306-8a31-1f50d935a650"
}
```

####3.返回字段说明
>卡片字段名称：custom_player_list

|名称|子字段|说明|类型|示例|
|:---|:---|:---|:---|:---|
|cnname|------|中文名称|string|无问西东|
|birthday|------|中文名称|string|无问西东|
|pic_url|------|中文名称|string|无问西东|
|custom_info|birthday|中文名称|string|无问西东|
|custom_info|number|中文名称|string|无问西东|
|custom_info|stat|中文名称|string|无问西东|
|custom_info|nation|中文名称|string|无问西东|
|custom_info|postion|中文名称|string|无问西东|
|custom_info|club|中文名称|string|无问西东|
|custom_info|tag|中文名称|string|无问西东|
|url|------|中文名称|string|无问西东|
####4.UI 效果展示




