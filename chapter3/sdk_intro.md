##1.方案描述
    在手机端进行离线命名实体识别（NER),然后调用相应的资源接口，进行资源请求。
##2.接口描述
|接口名称|接口功能|请求示例|
|:---:|:---:|:---:|
|resource 接口|只实现资源请求|http://triotest.sanjiaoshou.net/nlp/resource|
##3.接口请求示例
####3.1请求接口 
    http://triotest.sanjiaoshou.net/nlp/resource
####3.2请求方式
该接口请求方式为 post 请求，可采用 postman 等工具进行测试，或在linux下可采用如下命令进行测试：

---
`curl -H "Content-Type:application/json" -X POST --data '{"{"nluTerms":[{"isSlot":false,"ner":"FILM","offset":0,"position":0,"prvSpace":false,"trailingWild":false,"word":"无问东西"}],"userId":"trio","timestamp":"1515391135","longitude":"113.937862","latitude":"22.521726"}"}' http://triotest.sanjiaoshou.net/nlp`

---

####3.3请求示例 
    {"nluTerms":[{"isSlot":false,"ner":"FILM","offset":0,"position":0,"prvSpace":false,"trailingWild":false,"word":"无问东西"}],"userId":"trio","timestamp":"1515391135","longitude":"113.937862","latitude":"22.521726"}
相应字段说明：

|参数名称|参数含义|
|:---:|:---:|
|isSlot|弃用字段|
|ner|命名实体识别结果|
|offset|以此可请求多个实体，从 0 开始索引|
|position|弃用字段|
|prvSpace|弃用字段|
|trailingWild|弃用字段|
|word|命名实体对应的文本|
|userId|厂商专用的 userId|
|longitude|GPS 经度|
|latitude|GPS 维度| 

####3.4请求结果
**<font color=#0099ff>注：@后边为字段解释</font>**

    {
    "error_code": 0,
    "error_msg": "success",
    "query": "我想去看无问西东",
    "result_list": [
        {
            "divided_list": [
                "我",
                "想",
                "去",
                "看",
                "无问西东"
            ],
            "domain_list": [
                {
                    "name": "地图",
                    "value": 0.2010011374950409
                },
                {
                    "name": "K12",
                    "value": 0.1644483357667923
                },
                {
                    "name": "医疗",
                    "value": 0.1300085335969925
                }
            ],
            "term_list": [
                {
                    "token": "我想",
                    "ner": "O",
                    "offset": 0,
                    "ner_prob": 0
                },
                {
                    "token": "去看",
                    "ner": "O",
                    "offset": 0,
                    "ner_prob": 0
                },
                {
                    "token": "无问西东",
                    "ner": "FILM",
                    "offset": -1,
                    "ner_prob": 0,
                    "film_list": [
                        {
                            "name": "无问西东",
                            "point": "7.7",
                            "type": "剧情,爱情,战争",
                            "id": "6874741",
                            "direcotr": "李芳芳",
                            "actor": "章子怡,黄晓明,张震",
                            "posturl": "https://img3.doubanio.com/view/photo/s_ratio_poster/public/p2507572275.jpg",
                            "year": "2018",
                            "summary": "如果提前了解了你所要面对的人生，你是否还会有勇气前来？吴岭澜、沈光耀、王敏佳、陈鹏、张果果，几个年轻人满怀诸多渴望，在四个非同凡响的时空中一路前行。\n吴岭澜（陈楚生 饰），出发时意气风发，却很快在途中迷失了方向。沈光耀（王力宏 饰），自愿参与了最残酷的战争，他一直在努力去做那些令他害怕，但重要的事。王敏佳（章子怡 饰）最初的错误，只是为了虚荣撒了一个小谎；最初的烦恼，只是在两个优秀的男人中选择一个。但命运，却把她拖入被众人唾骂的深渊。陈鹏（黄晓明 饰）把爱情摆在了理想前面，但爱情却没有把他摆在前面。他说，“我有人要照顾”，纵然这意味着与所有人作对，意味着要和她一起被放逐千里。张果果（张震 饰），身处尔虞我诈的职场，“赢”是他的习惯。为了赢，他总是见招拆招，先发制人。而有一天，他却面临了一个比“赢”更重要的选择。这几个年轻人，在最好的年纪迎来了最残酷的考验,并成就了永不褪色的青春传奇。",
                            "country": "中国大陆",
                            "buy_url": "http://m.maoyan.com/cinema/movie/71946",
                            "casts": [
                                {
                                    "alt": "https://movie.douban.com/celebrity/1041014/",
                                    "avatarUrl": "https://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1359895311.0.jpg",
                                    "id": "1041014",
                                    "name": "章子怡"
                                },
                                {
                                    "alt": "https://movie.douban.com/celebrity/1041404/",
                                    "avatarUrl": "https://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1472787652.32.jpg",
                                    "id": "1041404",
                                    "name": "黄晓明"
                                },
                                {
                                    "alt": "https://movie.douban.com/celebrity/1077991/",
                                    "avatarUrl": "https://img1.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1453574419.48.jpg",
                                    "id": "1077991",
                                    "name": "张震"
                                },
                                {
                                    "alt": "https://movie.douban.com/celebrity/1045243/",
                                    "avatarUrl": "https://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p21771.jpg",
                                    "id": "1045243",
                                    "name": "王力宏"
                                }
                            ],
                            "url": "https://movie.douban.com/subject/6874741",
                            "intent": "douban://douban.com/movie/6874741?from=mdouba",
                            "source": "DoubanFilm"
                        }
                    ],
                    "cinemaInfo_list": [
                        {
                            "id": "71946",
                            "name": "无问西东",
                            "point": "8.6",
                            "showst": "1",
                            "type": "爱情,战争",
                            "ticketUrl": "http://m.maoyan.com/cinema/movie/71946",
                            "trailerUrl": "http://maoyan.meituan.net/movie/videos/854x480a5a5aa819b504a80a9c84d2b03814feb.mp4",
                            "url": "http://triotest.sanjiaoshou.net/nlp/q?key:AhqjNOE0UVSxv5nRVdoEEK_EJ1bauqDggYGQG8aaK95LeNh47CL2rKQarFq4AkDotBC-Fs9g_pQksQOy5CzstS5pc5jEG0KHa14lS3Xd9xyxLzXjrovzUlZE0BT7uT7Yut6Q1qlSdZ6zNkQBW7L3PU74I6-vMzobzScCojdXM-elI7mnjSI-nS6MwiZj-OSuNb5T3xCZCzbVFMgOOKZXudgE_Ni_Q_5n",
                            "intent": "",
                            "source": "MaoyanFilm"
                        }
                    ]
                }
            ]
        }
    ]
