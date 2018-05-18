>#图书信息卡片

#### ui展示效果
#### 测试demo
#### 返回字段说明
>卡片字段名称：book_list

|名称|说明|类型|示例|
|:---:|:---:|:----:|:---:|
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




