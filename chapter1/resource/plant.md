>#常见植物卡片


####1.测试 Demo
{%fbq%}
term:##动物名称##
ner:##ENTITY.PLANT##
{%endfbq%}
####2.返回 Json 示例
```json
{
    {
    "name": "松树",
    "pic_url": "http://a4.att.hudong.com/54/14/20300542501520139737149238323_140.jpg",
    "summary": "松树，松科（Pinaceae）松属植物的通称，常绿树。绝大多数是高大乔木。高20～50米，最高可达75米（美国的糖松P.lambertiana）。松树具有很强的抗旱性，耐阴性差。极少数为灌木状，如偃松（P.pumila）和地盘松（P.yunnanensis）。北半球森林的重要构成成分，人工造林的重要树种，也是很有价值的观赏树种。",
    "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:wmqrteS4gLFe3G7a8-hha62xyzjtw9Xz13cblksvZatIuz7IuTbNpg==",
    "source": "Hudong"
}
}
```

####3.返回字段说明
>卡片字段名称：plant_list

|名称|说明|类型|示例|
|:---|:---|:---|:---|
|name|动物名称|string|松树|
|pic_url|图片链接|string|http://a3.att.hudong.com/66/51/20300542684355141042518476164_140.jpg|
|summary|动物简介|string|西伯利亚雪橇犬，是动物界、脊索动物门的一种动物。 是原始的古老犬种，在西伯利亚东北部、格陵兰南部生活。哈士奇名字的由来，是源自其独特的嘶哑叫声。在西伯利亚东北部的原始部落楚克奇人（Chukchi)，用这种外型酷似狼的犬种，作为最原始的交通工具来拉雪橇，并用这种狗猎取和饲养驯鹿，或者繁殖这种狗，然后带出他们居住的冻土地，换取温饱。典型狼性犬。哈士奇性格多变，有的极端胆小，有的极端暴力，进入大陆和家庭的哈士奇，都已经没有了野性，比较温顺，是一种流行于全球的宠物犬。淘狗网一致认定哈士奇与金毛犬、拉布拉多并列为三大无攻击型犬类。|
|url|动物链接|string|http://phoneapi.sanjiaoshou.net/nlp/q?key:ypoT0XTkqe8HX3x0AmcZTSfcJWmF_VbcH_nF9xssYgkU_RrFOK_BVFGcHRErxQnN6yfUAmX6g-dAVvJAzf9ZegvGVBf-JFwwvBYQujA7r0Hq_8EaCL87b6JSvelEkQzDgD2ZY9hWZyO2BK69O3RkkwIuOutXqQcYb43rLPdkdq0=|
|source|来源标识|string|Hudong|


####4.UI 效果展示




