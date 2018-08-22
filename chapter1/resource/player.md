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

|名称|说明|类型|示例|
|:---|:---|:---|:---|
|name|动物名称|string|松树|
|pic_url|图片链接|string|http://a4.att.hudong.com/54/14/20300542501520139737149238323_140.jpg|
|summary|动物简介|string|松树，松科（Pinaceae）松属植物的通称，常绿树。绝大多数是高大乔木。高20～50米，最高可达75米（美国的糖松P.lambertiana）。松树具有很强的抗旱性，耐阴性差。极少数为灌木状，如偃松（P.pumila）和地盘松（P.yunnanensis）。北半球森林的重要构成成分，人工造林的重要树种，也是很有价值的观赏树种。|
|url|动物链接|string|http://phoneapi.sanjiaoshou.net/nlp/q?key:wmqrteS4gLFe3G7a8-hha62xyzjtw9Xz13cblksvZatIuz7IuTbNpg==|
|source|来源标识|string|Hudong|




####4.UI 效果展示




