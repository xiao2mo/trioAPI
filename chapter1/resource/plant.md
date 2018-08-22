>#常见植物卡片


####1.测试 Demo
{%fbq%}
term:##动物名称##
ner:##ENTITY.PLANT##
{%endfbq%}
####2.返回 Json 示例
```json

{
    "name": "松树",
    "pic_url": "http://a4.att.hudong.com/54/14/20300542501520139737149238323_140.jpg",
    "summary": "松树，松科（Pinaceae）松属植物的通称，常绿树。绝大多数是高大乔木。高20～50米，最高可达75米（美国的糖松P.lambertiana）。松树具有很强的抗旱性，耐阴性差。极少数为灌木状，如偃松（P.pumila）和地盘松（P.yunnanensis）。北半球森林的重要构成成分，人工造林的重要树种，也是很有价值的观赏树种。",
    "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:wmqrteS4gLFe3G7a8-hha62xyzjtw9Xz13cblksvZatIuz7IuTbNpg==",
    "source": "Hudong"
}
```

####3.返回字段说明
>卡片字段名称：plant_list

|名称|说明|类型|示例|
|:---|:---|:---|:---|
|name|动物名称|string|松树|
|pic_url|图片链接|string|http://a4.att.hudong.com/54/14/20300542501520139737149238323_140.jpg|
|summary|动物简介|string|松树，松科（Pinaceae）松属植物的通称，常绿树。绝大多数是高大乔木。高20～50米，最高可达75米（美国的糖松P.lambertiana）。松树具有很强的抗旱性，耐阴性差。极少数为灌木状，如偃松（P.pumila）和地盘松（P.yunnanensis）。北半球森林的重要构成成分，人工造林的重要树种，也是很有价值的观赏树种。|
|url|动物链接|string|http://phoneapi.sanjiaoshou.net/nlp/q?key:wmqrteS4gLFe3G7a8-hha62xyzjtw9Xz13cblksvZatIuz7IuTbNpg==|
|source|来源标识|string|Hudong|


####4.UI 效果展示

>植物资源卡片展示

<div align="center">
<img src="/assets/chapter1/zhiwu.png" align="center" alt="植物资源卡片实例">
</div>








