># 在线获取资源

####1.在线获取资源增量参数
>新增实体结构体 NluTerms，其包含的字段如下所示：

|参数名|参数含义|类型|示例|是否必须|
|:---|:---|:---|:---|:---|
|isSlot|是否是槽位|bool|-|y|
|ner|实体名称|string|-|y|
|offset|槽位偏移量|int|-|y|
|position|实体偏移量|int|-|y|
|prvSpace|前边是否有空格|string|-|y|
|trailingWild|是否是槽位|bool|-|y|
|word|实体内容|string|-|y|

####2.请求 json 示例
```json
{"nluTerms":[{"isSlot":false,"ner":"HOTEL","offset":0,"position":0,"prvSpace":false,"trailingWild":false,"word":"七天连锁酒店"}],"userId":"trio","timestamp":"1515391135","longitude":"113.937862","latitude":"22.521726"}
```

####3.返回 json 结构

####4.返回 json 示例
