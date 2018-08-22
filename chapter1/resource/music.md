>#音乐资源卡片


####1.测试 Demo
{%fbq%}
term:##音乐名称##
ner:##MUSIC##
{%endfbq%}
####2.返回 Json 示例
```json
{
    "id": "01ce186799a7ee26a12aba4e3bb5d600",
    "album": "欧若拉 Aurora",
    "released_time": "2012-01-01",
    "score": 50,
    "name": "快乐崇拜",
    "language": "国语",
    "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:6wOz3aRoPLLzJH69EeqEpSRwvCu38INZLFf33SMHSuJEHtw5fmj4a_mbCV117qb39bb0jA8gY4jyXSdLhhP92c8AuS7QXy2skkr8HpmI9hlQDvA--IZ5h3RiYEMZAUv1U9T-CioqhpZDkDdd99jM-g==",
    "source": "WangyiMusic"
}
```

####3.返回字段说明

>卡片字段名称：wangyi_music_list


|名称|说明|类型|示例|
|:---|:---|:---|:---|
|id|歌曲id|string|01ce186799a7ee26a12aba4e3bb5d600|
|album|歌曲专辑|string|欧若拉 Aurora|
|released_time|发行时间|string|2012-01-01|
|score|歌曲评分|string|50|
|name|歌曲名称|string|快乐崇拜|
|language|歌曲语言|string|国语|
|url|歌曲链接|string|http://phoneapi.sanjiaoshou.net/nlp/q?key:6wOz3aRoPLLzJH69EeqEpSRwvCu38INZLFf33SMHSuJEHtw5fmj4a_mbCV117qb39bb0jA8gY4jyXSdLhhP92c8AuS7QXy2skkr8HpmI9hlQDvA--IZ5h3RiYEMZAUv1U9T-CioqhpZDkDdd99jM-g==|
|source|来源标识|string|WangyiMusic|

####4.UI 效果展示







