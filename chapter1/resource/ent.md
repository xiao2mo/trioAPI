>#影视信息卡片

####1.测试 Demo
[^_^]:{%fbq%}
[^_^]:term:##影视名称##
[^_^]:ner:##FILM##
[^_^]:{%endfbq%}

####2.返回 Json 示例
>测试 query 内容：听说无问东西挺不错的，一起去看吧。



####3.返回字段说明
>卡片字段名称：<font clor="blue"> film_list </font>

|名称|子字段|说明|类型|示例|
|:---|:---|:---|:---|:---|
|name|------|名称|string|无问西东|
|point|------| 豆瓣评分 |string  |7.7  |
|type|------| 影片类型| string|剧情，爱情，战争 |
|id|------| 豆瓣id|string |6874741 |
|director|------| 导演|string |李芳芳 |
|actor|------| 主演|string |章子怡、黄晓明、张震 |
|posturl| ------|海报地址|string | https://img3.doubanio.com/view/photo/s_ratio_poster/public/p2507572275.jpg|
|year|------| 上映年份| string| 2018|
|summary|------| 影片简介| string| 如果提前了解了你所要面对的人生，你是否还会有勇气前来？吴岭澜、沈光耀、王敏佳、陈鹏、张果果，几个年轻人满怀诸多渴望，在四个非同凡响的时空中一路前行。\n吴岭澜（陈楚生 饰），出发时意气风发，却很快在途中迷失了方向。沈光耀（王力宏 饰），自愿参与了最残酷的战争，他一直在努力去做那些令他害怕，但重要的事。王敏佳（章子怡 饰）最初的错误，只是为了虚荣撒了一个小谎；最初的烦恼，只是在两个优秀的男人中选择一个。但命运，却把她拖入被众人唾骂的深渊。陈鹏（黄晓明 饰）把爱情摆在了理想前面，但爱情却没有把他摆在前面。他说，“我有人要照顾”，纵然这意味着与所有人作对，意味着要和她一起被放逐千里。张果果（张震 饰），身处尔虞我诈的职场，“赢”是他的习惯。为了赢，他总是见招拆招，先发制人。而有一天，他却面临了一个比“赢”更重要的选择。这几个年轻人，在最好的年纪迎来了最残酷的考验,并成就了永不褪色的青春传奇。|
|country| ------|上映地址| string| 中国大陆|
|buy_url| ------|购票链接| string| http://m.maoyan.com/cinema/movie/71946|
|casts|alt|演员信息链接|string | https://img3.doubanio.com/view/photo/s_ratio_poster/public/p2507572275.jpg|
|casts|avatarUrl| 演员肖像链接|string |https://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1359895311.0.jpg |
|casts|id|演员id |string |1041014|
|casts|name| 演员名称| string|章子怡 |
|url|------| 豆瓣链接| string| https://movie.douban.com/subject/6874741|
|intent|------|跳转链接 | string|douban://douban.com/movie/6874741?from=mdouba |
|source|------|来源标识 |string | DoubanFilm|
####4.UI 展示效果
