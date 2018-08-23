>#电影购票卡片

####1.测试 Demo
{%fbq%}
term:##影视名称##
ner:##FILM##
{%endfbq%}


####2.返回 Json 示例
```json
{
    "id": "1200486",
    "name": "我不是药神",
    "point": "9.6",
    "showst": "1",
    "type": "剧情,喜剧",
    "ticketUrl": "http://m.maoyan.com/cinema/movie/1200486",
    "trailerUrl": "http://maoyan.meituan.net/movie/videos/854x4804c109134879943f4b24387adc040504b.mp4",
    "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:aqEytw5QLU5geveQ0G8gZIrxYddpHu0Q0QZNxGSYusOrwLEsB7TwTPR3toED_4OQbDdsivVG7f9ktdmdHNN2Yo6AB-FC9g63UU_2o4-A-tDVtsGGQdarNuRpUfzOXqdTiyzkk0v2wRXCDuhewmf8T71iZvocq8aMki4mcKjqcZslc5VsSqI1aI9Pguvzu_uCQEIG4XZptsE=",
    "intent": "",
    "source": "MaoyanFilm"
}
```
####3.返回字段说明

>卡片字段名称：cinemaInfo_list

|名称|说明|类型|示例|
|:---|:---|:---|:---|
|id|  猫眼id| string |  1200486|
|name| 名称 | string | 我不是药神 |
|point| 猫眼评分 |  string| 9.6 |
|showst| 展示个数|  string | 1 |
|type| 类型|string | 剧情、喜剧|
|ticketUrl|购票链接 |string | http://m.maoyan.com/cinema/movie/1200486|
|trailerUrl|预览链接 |string |http://maoyan.meituan.net/movie/videos/854x4804c109134879943f4b24387adc040504b.mp4 |
|url| 电影链接|string |http://phoneapi.sanjiaoshou.net/nlp/q?key:aqEytw5QLU5geveQ0G8gZIrxYddpHu0Q0QZNxGSYusOrwLEsB7TwTPR3toED_4OQbDdsivVG7f9ktdmdHNN2Yo6AB-FC9g63UU_2o4-A-tDVtsGGQdarNuRpUfzOXqdTiyzkk0v2wRXCDuhewmf8T71iZvocq8aMki4mcKjqcZslc5VsSqI1aI9Pguvzu_uCQEIG4XZptsE=|
|intent|跳转链接 |string | |
|source| 来源标识| string| MaoyanFilm|


####4.UI 效果展示

>订票资源卡片展示

<div align="center">
<img src="/assets/chapter1/yaoshen_film.png" align="center" alt="电影资源卡片实例">
</div>



