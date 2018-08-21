>#图书信息卡片


####1.测试 Demo
{%fbq%}
term:##图书名称##
ner:##BOOK##
{%endfbq%}

####2.返回 Json 示例
```json
{
    "id": "1034282",
    "name": "时间简史",
    "point": "8.8",
    "tag": "科普,史蒂芬·霍金,时间简史",
    "author": "[英] 史蒂芬·霍金",
    "authorList": [
        {
            "name": "[英] 史蒂芬·霍金",
            "url": "http://www.baike.com/wiki/%E5%8F%B2%E8%92%82%E8%8A%AC%C2%B7%E9%9C%8D%E9%87%91"
        }
    ],
    "image": "https://img3.doubanio.com/view/subject/m/public/s1914861.jpg",
    "binding": "平装",
    "pages": "245",
    "publisher": "湖南科学技术出版社",
    "isbn13": "9787535732309",
    "summary": "《时间简史》讲述是探索时间和空间核心秘密的故事，是关于宇宙本性的最前沿知识，包括我们的宇宙图像、空间和时间、膨胀的宇宙不确定性原理、基本粒子和自然的力、黑洞、黑洞不是这么黑、时间箭头等内容。第一版中的许多理论预言，后来在对微观或宏观宇宙世界观测中得到证实。\n自1988年首版以来，《时间简史》已成为全球科学著作的里程碑。它被翻译成40种文字，销售了近1000万册。此版更新了内容，把许多观测揭示的新知识，以及霍金最新的研究纳入，并配以250幅照片和电脑制作的三维和四维空间图。",
    "price": "45.00元",
    "pubdate": "2010-4",
    "comments": [
        {
            "title": "给自己一个理由，让世界活下去",
            "content": "这本科普读物我前前后后看了6年。2003年初，我浏览了书中所有的彩图、注释及部分章节，这一切对于当时的我来说充满新奇却也过于深奥。2007年夏，...",
            "id": "1660312",
            "score": 0,
            "uid": "2139340",
            "uname": "川貝",
            "uurl": "https://api.douban.com/v2/user/2139340"
        },
        {
            "title": "史蒂芬霍金的七条名言",
            "content": "7.当爱因斯坦说到“上帝不掷骰子”的时候，他错了。鉴于黑洞给予我们的暗示，上帝不仅掷筛子，而且往往将骰子掷到我们看不见的地方以迷惑我们。\n6.我...",
            "id": "1288668",
            "score": 0,
            "uid": "1379863",
            "uname": "Ethan",
            "uurl": "https://api.douban.com/v2/user/1379863"
        },
        {
            "title": "本体论哲学家霍金与上帝的终极之战",
            "content": "本体论哲学家霍金与上帝的终极之战\n\n       故事有一个冗长的开头。\n\n       我们身处的世界是怎样的？自人类文明开始，这类诘问就伴随...",
            "id": "7578212",
            "score": 0,
            "uid": "4504804",
            "uname": "名花零落",
            "uurl": "https://api.douban.com/v2/user/4504804"
        },
        {
            "title": "王不写诗",
            "content": "前几天和朋友聊天，我说现在这个时代就是没有力量，没有大哥，只有妖孽。朋友说或许有大哥我们不知道，也许是吧，不过从科学上来讲，这个大哥的存在还没有...",
            "id": "2768181",
            "score": 0,
            "uid": "1458759",
            "uname": "扎那",
            "uurl": "https://api.douban.com/v2/user/1458759"
        },
        {
            "title": "时间简史",
            "content": "原文和翻译本结合起来看的,文科出生的科学弱童,有不少疑惑之处\n\n时间简史读书笔记 - 第七章1 关于事件视界的疑问\nhttp://blog.si...",
            "id": "1947511",
            "score": 0,
            "uid": "3019581",
            "uname": "ellie",
            "uurl": "https://api.douban.com/v2/user/3019581"
        }
    ],
    "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:T06b7qBVFOAtNe0eVnSAZ5mfqVKeH-s7ES04r7BqcugoRbSnJDIpkbJYPXwWt-YevwzGF34yWUFo0goHvcfBHYE6-Qn-HESb7H99vPWefcdRYg0cmVZjEiejtWvDlx9-cG0G_nqBnNowXy4PSBP-Zw==",
    "intent": "douban://douban.com/book/1034282?from=mdouba",
    "source": "DoubanBook"
}
```
####3.返回字段说明
>卡片字段名称：book_list

|名称|说明|类型|示例|
|:---|:---|:---|:---|
|id|豆瓣id|string|1034282|
|name|图书名称|string|时间简史|
|point|豆瓣评分|string|8.8|
|tag|图书标签|string|科普,史蒂芬·霍金,时间简史|
|author|作者名称|string|[英] 史蒂芬·霍|
|authorList|作者信息|string[]||
|authorList.name|作者名称|string|[英] 史蒂芬·霍|
|authorList.url|百科链接|string|http://www.baike.com/wiki/%E5%8F%B2%E8%92%82%E8%8A%AC%C2%B7%E9%9C%8D%E9%87%91|
|image|图书封面|string|https://img3.doubanio.com/view/subject/m/public/s1914861.jpg|
|binding|装订方式|string|平装|
|pages|总页数|string|245|
|publisher|出版社名称|string|湖南科学技术出版社|
|isbn13|ISBN图书编号|string|9787535732309|
|summary|图书简介|string|《时间简史》讲述是探索时间和空间核心秘密的故事，是关于宇宙本性的最前沿知识，包括我们的宇宙图像、空间和时间、膨胀的宇宙不确定性原理、基本粒子和自然的力、黑洞、黑洞不是这么黑、时间箭头等内容。第一版中的许多理论预言，后来在对微观或宏观宇宙世界观测中得到证实。\n自1988年首版以来，《时间简史》已成为全球科学著作的里程碑。它被翻译成40种文字，销售了近1000万册。此版更新了内容，把许多观测揭示的新知识，以及霍金最新的研究纳入，并配以250幅照片和电脑制作的三维和四维空间图。|
|price|图书价格|string|45.00元|
|pubdate|发行日期|string|2010-4|
|comments|豆瓣长评|string[]||
|comments.title|评论标题|string|给自己一个理由，让世界活下去|
|comments.content|评论内容|string|这本科普读物我前前后后看了6年。2003年初，我浏览了书中所有的彩图、注释及部分章节，这一切对于当时的我来说充满新奇却也过于深奥。2007年夏，...|
|comments.id|评论id|string|1660312|
|comments.score|评论得分|string|0|
|comments.uid|用户id|string|2139340|
|comments.uname|用户名称|string|川貝|
|comments.uurl|用户连接|string|https://api.douban.com/v2/user/2139340|
|url|图书链接|string|https://book.douban.com/subject/1034282/|
|intent|跳转链接|string|douban://douban.com/book/1034282?from=mdouba|
|source|来源标识|string|DoubanBook|

####4.UI 效果展示



