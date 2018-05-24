# 三角兽自然语言理解关联资源语法(TRES)

三角兽自然语言理解关联资源语法 Trio nlu REsource Syntax(TRES), 通过json格式关联自然语言
理解的解析结果和三角兽卡片资源的字段，实现自然语言输入，富媒体卡片输出。

|name|格式|说明|示例|
|:---|:---|:---|:---|
|requestType|string|关联的卡片|film_list|
|term|string|实体word|红海行动|
|ner|string|命名实体类型|FILM [\*](http://10.0.2.200:4000/chapter1/nlp_ner.html)|


除了单个卡片的抽取外，语法还支持复杂的逻辑表达式，目前包括 与(&)，或(|)，非(^) 三种简单的逻辑表达式,
包含(<) 的列表逻辑操作，以及 any(*), multiple(+), zero or many(?) 的正则表达式操作.

实现如下的的效果
```
# 同一个资源的多个字段
{requestType=film,term=红海行动,ner=FILM,requestField=releaseTime & requestField=buy_url}

# 多个资源的字段
{requestType=film,term=红海行动,ner=FILM,requestField=buy_url} | {requestType=film,term=头号玩家,ner=FILM,requestField=buy_url}

# 非操作
{requestType=film,term=复仇者联盟,ner=FILM,requestField=director^<乔斯·韦登}
```


[ner_example]: "http://10.0.2.200:400" "三角兽命名实体体系说明"