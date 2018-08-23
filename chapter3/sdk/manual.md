## 标准Trio SDK文档 2.6版本


####1. 概述
#####SDK核心功能
Trio SDK提供了文字语义理解功能，根据输入的文字，返回识别出的意图，你的app可以根据这个意图做出相应的动作。SDK提供的功能包括切词，NER识别等两大功能。

####2. 版本历史
```
Version: 1.0
Release Date: 2018-1-30
1.	第一版，提供了两个接口，分词和NER识别接口。完全使用的网络数据，尚未加入本地逻辑

Version: 1.1
Release Date: 2018-2-2
1.	初始化加入回调函数，初始化结束后会调用回调函数
2.	混淆规则加入相应的规则，注意替换
3.	PERSON_NAME类型的实体返回信息PersonInfo中加入is_contact字段标志这个人名是否在手机通讯录
4.	PERSON_NAME类型的实体返回信息PersonInfo中加入人物简介summary字段

Version: 1.2
Release Date: 2018-2-5
1.	删除了返回数据中的空列表
2.	添加了两个接口的返回示例数据，包括有网情况和没网情况，使得理解起来更直观
3.	加入了本地日程数据的添加，一段话最多添加一个日程，如果有日程的话，日程信息挂靠在第一个出现的DATA、DAY或CLOCK类型下面

Version: 1.3
Release Date: 2018-2-26
1.	修改了日程实体CalendarInfo字段名称


Version: 1.4
Release Date: 2018-3-8
1.	修改了NER识别接口英文分词的bug
2.	火车实体类型返回字段添加了跨天字段

Version：1.5
Release Date: 2018-3-27
1.	网络出问题的时候使用本地的接口进行解析

Version：1.6
Release Date: 2018-4-8
1.	给NER解析的接口requestNERInfo添加了一个同名函数，该函数可以接收由调用者传入的GPS信息，包括： GPS坐标系类型和经纬度，此时SDK内部将不再获取GPS，而是使用传入的GPS。如果外部没有传入GPS，SDK内部将获取GPS。之前的接口依然兼容。

Version：1.7
Release Date: 2018-5-18
1.	添加了快递类型资源的返回
2.	修改了部分日志，修改了so文件的潜在bug

Version：1.8
Release Date: 2018-5-21
1.纯表情调用接口后也会调用回调函数

Version：1.9
Release Date: 2018-5-23
1.本地分词由按句子分词，改成整体分词，这样和服务器返回的结果一致了
2.修改了部分jni代码，修复潜在的bug

Version：2.0
Release Date：2018-6-1
1.加入了分词热身功能，解决某些情况下分词结果为单字的问题

Version：2.1
Release Date: 2018-6-4
1.更新了文档，明确了本地支持的类型：联系人，电话号码，日程

Version：2.2
Release Date: 2018-6-12
1.NER识别接口加入了整句话所属类别的信息，也就是Domain信息
2.删除了初始化过程的who()函数

Version：2.3
Release Date: 2018-6-21
1.修改了jni stack corruption的问题

Version：2.4
Release Date: 2018-7-9
1.修改了friso so崩溃的问题

Version：2.5
Release Date: 2018-8-15
1.加入了网络请求的鉴权机制，需要修改初始化调用方式，设置appkey，详见文档“模型加载及单例初始化”部分

Version：2.6
Release Date: 2018-8-20
加入了通用卡片
```

#### 3. 功能介绍
我们以这句话作为输入，“**明天上午9点去惠新西街甲7号住总地产大厦**"，分别介绍两大功能。

**切词功能：**

SDK会将输入的一段文字进行切词，返回两个单词列表，一个是单纯的分词结果，另一个是考虑了NER识别结果的分词结果，如下：
简单分词结果：

**[“明天” “上午” “9点” “去” “惠新西街” “甲7号” “住总地产大厦”]**

考虑了NER识别的结果：

**[“明天上午9点” “去” “惠新西街甲7号住总地产大厦”]**

**NER识别**：

NER识别通过对输入内容分析，返回所有识别出的实体的类别，包括：
CLOCK：明天上午9点
ADDR : 惠新西街甲7号住总地产大厦

完整的类型列表可查看附录表一《类型表》。

#### 4. SDK接口使用步骤
我们通过一个AAR文件打包封装了SDK上述三个功能，在Android Studio工程引入该AAR文件即可调用三大功能。
SDK接入步骤：
#####4.1 引入AAR
在Android app工程下新建libs文件夹，将我们提供的nnpredictmodule-release.aar放在libs文件夹下。
![](/assets/sdk/1.png)
在app下的gradle文件中添加repositories段，指明aar所在的文件夹。
![](/assets/sdk/2.png)

同时在dependencies段添加对aar的引用以及对gson的引用（我们的sdk使用gson进行json对象的解析）：
```
compile(name: 'nnpredictmodule-release', ext: 'aar')
compile 'com.google.code.gson:gson:2.3.1'
```
![](/assets/sdk/3.png)

最后在proguard-rules.pro中添加混淆规则：
```
-keep class com.trio.nnpredict.Requests.RequestCallback { *; }

-keep class com.trio.nnpredict.TrioWrap.Trio { *; }
-keep class com.trio.nnpredict.TrioWrap.Trio$** { # keep enum in Trio
**[] $VALUES;
public *;
}

-keep class com.trio.nnpredict.TrioWrap.InitProgressListener { *; }
-keep class com.trio.nnpredict.TrioWrap.Model.** { *; }

-keep class com.trio.nnpredict.BaseModel { *; }
-keep class com.trio.nnpredict.TrioWrap.Model.TrioResult$** { *; } # keep inner class in TrioResult

-keep class com.trio.nnpredict.Http.HttpCallback { *; }
-keep class com.trio.nnpredict.Utils.** { *; }


-keep class com.trio.nnpredict.LocalPredict.NNPredict {
public static void init(**);
}

-keep class com.trio.nnpredict.Friso.FrisoWrapper { *; }

-keep class com.trio.nnpredict.rule.ai.trio.nlu.rule.** { *; }

##---------------Begin: proguard configuration for Gson ----------
-keepattributes Signature
-keepattributes *Annotation*
-dontwarn sun.misc.**
#-keep class com.google.gson.stream.** { *; }
-keep class com.google.gson.examples.android.model.** { *; }
-keep class * implements com.google.gson.TypeAdapterFactory
-keep class * implements com.google.gson.JsonSerializer
-keep class * implements com.google.gson.JsonDeserializer

##---------------End: proguard configuration for Gson ----------

```

这样，就完成了aar的引入，可以调用aar的各个接口函数了。

#####4.2 模型加载及单例初始化
在Application的onCreate中添加以下代码，完成Trio单例的设置和初始化，所有可供调用的接口都是通过Trio单例提供的：

```
Trio trio = new Trio.Builder()
                .context(getApplicationContext())
                .assetManager(getAssets())
                .timeOut(5000)
                .userID("YOUR USERID")  // YOUR USERID
                .appkey("YOUR APPKEY") // YOUR APPKEY
                .build(new InitProgressListener() {
                    @Override
                    public void onCompleted() {
                        // Init success
                    }

                    @Override
                    public void onError(String errorMsg, int errorCode) {
                        // Init fail
                    }
                });
```

**assetManager**

设置assetManager

**timeOut**

设置超时时间，超过这个时间返回出错信息

**userID**

设置分配给调用方的userID

**setSingletonInstance**

完成Trio单例的构造后，通过setSingletonInstance设置全局单例。通过with函数可以获取该全局单例。

#####4.3 获取分词结果
根据输入的文字，返回分词的结果，输入为字符串，输出为String列表。
接口定义：
```
Public void requestDivided(String query, RequestCallback<DivideResult> callback)
```

用法如下：
```
Trio.with().requestDivided(inputStr, new RequestCallback<DivideResult>() {
                    @Override
                    public void onSuccess(DivideResult result) {
                        // success
                    }

                    @Override
                    public void onError(String errorMsg) {
                        // fail
                    }
                });
```

其中DivideResult定义如下：
```
public class DivideResult extends BaseModel {
    // 网络结果还是本地结果，true为网络结果，false为本地结果
    public boolean fromRemote = true;
    
    // 出错码
    @SerializedName("error_code")
    public int errorCode;
    
    // 出错信息
    @SerializedName("error_msg")
    public String errorMsg;
    
    // 原始输入的待分析文字
    @SerializedName("query")
    public String query;
    
    // 列表的每一项代表一句话对应的分词结果
    @SerializedName("result_list")
    public ArrayList<SentenceDivideResult> sentenceDivideResults;
    
    
    public static class SentenceDivideResult extends BaseModel {
        // 未考虑实体识别结果的分词
        @SerializedName("divided_list")
        public ArrayList<String> wordsDividedList;
        
        // 考虑了实体识别的结果的分词
        @SerializedName("term_list")
        public ArrayList<NerDivideItem> nerDividedList;
    }
    
    public static class NerDivideItem extends BaseModel {
        // 识别出来的实体的名称, 如"五道口"
        @SerializedName("token")
        public String token;
        
        // 识别出来的实体的类别,如"ADDR"
        @SerializedName("ner")
        public String ner;
    }
}
```
DivideResult各字段含义：

![](/assets/sdk/1534910287472.jpg)

SentenceDivideResult各字段含义：
![](/assets/sdk/1534910362200.jpg)



示例返回（有网情况）：
```
{
    "error_code": 0,
    "error_msg": "success",
    "query": "我上午要去五道口，看羞羞的铁拳。",
    "result_list": [
        {
            "divided_list": [
                "我",
                "上午",
                "要去",
                "五道口",
                "，",
                "看",
                "羞羞",
                "的",
                "铁拳",
                "。"
            ],
            "domain_list": [
                {
                    "name": "其它",
                    "value": 0.40110480785369873
                },
                {
                    "name": "地图",
                    "value": 0.27494409680366516
                },
                {
                    "name": "娱乐",
                    "value": 0.125632181763649
                }
            ],
            "term_list": [
                {
                    "token": "我",
                    "ner": "O"
                },
                {
                    "token": "上午",
                    "ner": "CLOCK"
                },
                {
                    "token": "要去",
                    "ner": "O"
                },
                {
                    "token": "五道口",
                    "ner": "ADDR"
                },
                {
                    "token": "，",
                    "ner": "O"
                },
                {
                    "token": "看",
                    "ner": "O"
                },
                {
                    "token": "羞羞的铁拳",
                    "ner": "FILM"
                },
                {
                    "token": "。",
                    "ner": "O"
                }
            ]
        }
    ],
    "log_id": "334e7525-c785-4d7c-9f19-c6465fe67fa3"
}
```

示例返回（无网情况）：
```
{
    "error_code":0,
    "fromRemote":false,
    "query":"我上午要去五道口，看羞羞的铁拳。",
    "result_list":[
        {
            "divided_list":[
                "我",
                "上午",
                "要去",
                "五道口",
                "，",
                "看",
                "羞羞",
                "的",
                "铁拳",
                "。"
            ]
        }
    ]
}
```

#####4.4 获取NER结果
根据输入的一段文字，返回识别的NER，输入为字符串，输出为NerResult的对象，每一项代表一句话的识别结果。
接口定义:
```
    public void requestNERInfo(final @NonNull String originalQuery, @NonNull RequestCallback<NerResult> callback)
```
或
```
    public void requestNERInfo(final @NonNull String originalQuery, GPS_TYPE gpsType, double longitude, double latitude, @NonNull RequestCallback<NerResult> callback) 
```
其中：
```
public enum GPS_TYPE {
        WGS84, // 国际坐标系
        GCJ02, //  火星坐标系
        BD09  //   百度坐标系
    }
```

用法如下（SDK内部获取GPS）：
```
Trio.with().requestNERInfo(inputStr, new RequestCallback<NerResult>() {
            @Override
            public void onSuccess(NerResult result) {
                // Deal with success
            }

            @Override
            public void onError(String errorMsg) {
                // Deal with error
            }
        });
```

或（外部传入GPS）：
```
Trio.with().requestNERInfo(inputStr, 
                           Trio.GPS_TYPE.GCJ02,
                           "116.41127139",
                           "39.99479325", new RequestCallback<NerResult>() {
            @Override
            public void onSuccess(NerResult result) {
                // Deal with success
            }

            @Override
            public void onError(String errorMsg) {
                // Deal with error
            }
        });
```

其中NerResult结构定义如下：
```
public class NerResult extends BaseModel{
    // 网络结果还是本地结果，true为网络结果，false为本地结果
    public boolean fromRemote = true;
    
    // 出错码
    @SerializedName("error_code")
    public int errorCode;
    
    // 出错信息
    @SerializedName("error_msg")
    public String errorMsg;
    
    // 原始输入的待分析文字
    @SerializedName("query")
    public String query;
    
    // 列表的每一项代表一句话对应的NER结果
    @SerializedName("result_list")
    public ArrayList<NerResultItem> resultItems;
    
    public static class NerResultItem extends BaseModel {
    // 细粒度分词结果
    @SerializedName("divided_list")
    public ArrayList<String> words;
    
    // 每句话识别出的NER列表
    @SerializedName("term_list")
    public ArrayList<NERItem> nerItems;
    
    // 这句话所属的可能的类别信息，列表按概率由高到低排序
    @SerializedName("domain_list")
    public ArrayList<DomainItem> domainItems;
    
    // 通用卡片数据
    @SerializedName("custom_info_list")
    public ArrayList<CustomInfoItem> customInfoItems;
    }
}
```
DomainItem定义如下，表示这句话所属类别的名称和概率，只有在线请求会返回，没网情况下无内容：
```
public class DomainItem extends BaseModel {
    @SerializedName("name")
    public String name; // Domain类别，如"地图"
    
    @SerializedName("value")
    public double value; // 概率，如0.8
}
```

CustomInfoItem用于通用卡片展示，在后面会有单独的小节讲到。
NERItem定义如下:
```
public class NERItem extends BaseModel {
    @SerializedName("token") // 实体名称，如"五道口"
    public String token;
    
    @SerializedName("ner") // 实体类型，如"ADDR"
    public String ner;
    
    @SerializedName("ner_prob")
    public double probability; // 概率，如0.7
    
    
    @SerializedName("film_list")
    public ArrayList<FilmInfo> filmInfoList; // 电影、电视预览信息
    
    @SerializedName("cinemaInfo_list")
    public ArrayList<CinemaInfo> cinemaInfoList; // 影院预览信息
    
    @SerializedName("meituan_list")
    public ArrayList<MeituanInfo> meituanInfoList; // 美团网预览信息
    
    @SerializedName("taokouling_list")
    public ArrayList<TaoKouLingInfo> taoKouLingInfoList; // 淘口令预览信息
    
    @SerializedName("feiyou_flight_list")
    public ArrayList<FeiyouFlightInfo> feiyouFlightInfoList; // 飞友航班预览信息
    
    @SerializedName("train_list")
    public ArrayList<TrainInfo> trainInfoList; // 火车预览信息
    
    @SerializedName("address_list")
    public ArrayList<AddressInfo> addressInfoList; // 地点预览信息
    
    @SerializedName("person_list")
    public ArrayList<PersonInfo> personInfoList; // 名人信息
    
    @SerializedName("calendar_list")
    public ArrayList<CalendarInfo> calendarInfoList; // 日程
    
    @SerializedName("kuaidi_list")
    public ArrayList<ExpressInfo> expressInfoList; // 快递
    // 下面是各种资源类型的定义详情，参考附录
    ......
}

```

其中各种嵌套子类的定义如FilmInfo，CinemaInfo等见附录2。

示例返回（有网情况）：
```
{
    "error_code": 0,
    "error_msg": "success",
    "query": "我明天上午开会，结束后去五道口看芳华。",
    "log_id": "1ee2e0fc-4a6c-4b51-a81c-122537978c2b",
    "result_list": [
        {
            "divided_list": [
                "我",
                "明天",
                "上午",
                "开会",
                "，",
                "结束",
                "后",
                "去",
                "五道口",
                "看",
                "芳华",
                "。"
            ],
            "domain_list": [
                {
                    "name": "其它",
                    "value": 0.3091542422771454
                },
                {
                    "name": "阅读",
                    "value": 0.2992916405200958
                },
                {
                    "name": "娱乐",
                    "value": 0.14238117635250092
                }
            ],
            "term_list": [
                {
                    "token": "我",
                    "ner": "O",
                    "offset": 0,
                    "ner_prob": 0.9999712705612183
                },
                {
                    "token": "明天上午",
                    "ner": "CLOCK",
                    "offset": -1,
                    "ner_prob": 0,
                    "calendar_list": [
                        {
                            "startTimeStamp": 1535072400000,
                            "startOffset": 1,
                            "endTimeStamp": -1,
                            "endOffset": 0,
                            "startTimeStr": "2018-08-24 09",
                            "theme": "观影提醒：芳华",
                            "themeOffset": 0
                        }
                    ]
                },
                {
                    "token": "开会",
                    "ner": "O",
                    "offset": 0,
                    "ner_prob": 0.9999582767486572
                },
                {
                    "token": "，",
                    "ner": "O",
                    "offset": 0,
                    "ner_prob": 0.9999957084655762
                },
                {
                    "token": "结束",
                    "ner": "O",
                    "offset": 0,
                    "ner_prob": 0.9999715089797974
                },
                {
                    "token": "后",
                    "ner": "O",
                    "offset": 0,
                    "ner_prob": 0.9999974966049194
                },
                {
                    "token": "去",
                    "ner": "O",
                    "offset": 0,
                    "ner_prob": 0.9999608993530273
                },
                {
                    "token": "五道口",
                    "ner": "ADDR",
                    "offset": 0,
                    "ner_prob": 0.9717825651168823,
                    "address_list": [
                        {
                            "name": "五道口",
                            "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:ZhdDU0aB2mBxFRllaUvDSqKGHAoPYWOxHZhQ0eexRIS-jPXY6FKpwe_YKDaRCr6T-HbqFna4Ave4yjE_NFzKacTeMb4zZ8vOddyUvMijjpGmFV63a-zLOI_nO_cvzz3thTbCnaiYbj0=",
                            "intent": "androidamap://poi?sourceApplication=trio&dev=0&keywords=%E4%BA%94%E9%81%93%E5%8F%A3"
                        },
                        {
                            "name": "五道口",
                            "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:Dgf0Y2xbrvDHt_qG05VcBRjOWCWP4uUrKJL8nTeZfA4aoVhhXnBihdlF0rX-_qF65PC_Z_UZo6IkNZUBeXNjAIWtRo0XxL8DGkruJakJoskx_sGKEgSIRM55eEdVUw66Dt0nKZWY1puQHT9ROFuL74phKYV9UAmdCI9KKwApRP4=",
                            "intent": "baidumap://map/geocoder?src=trio&address=%E4%BA%94%E9%81%93%E5%8F%A3"
                        }
                    ],
                    "baidu_poi_list": [
                        {
                            "id": "3dee767333bdcf173586f447",
                            "gpsType": "GCJ02",
                            "name": "五道口保理学院",
                            "address": "深圳市南山区桃园路8号田厦国际中心B座1918室",
                            "lat": "22.53270639342764",
                            "lng": "113.92731915040862",
                            "subSource": "bdLocalSearch",
                            "thumbnail": "http://api.map.baidu.com/staticimage/v2?ak=ERcMaGj5nOE3EdvHYEEIKBeavMDpEkex&mcode=666666&width=480&height=360&zoom=18&center=113.933853,22.538433&markers=113.933853,22.538433",
                            "relScore": 1,
                            "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:pbiG8JmqcuHwxriIIUL1u0gMuyeGnSD-jzbeU7FXs19NViBPYcwc8i9RQEk-9XTov9GC8okf0ff0o_aI2foraAUaKRzvDSzkxxGMDE1r9S8SaO3yktxrywIi6I29GTU6kBtW_ZG1dVd65toRLsyfvBXcBxa4zRVAv7mlAacS7Udk96GXpohE8yVyawzaZKv2rBIlk-HK67K-O0fMzvMEF5Vxv5zMPrtrj36ZEXGogAMCZFntGGq4QCq3N8qgqv3UaJcSeDagGP4=",
                            "intent": "baidumap://map/geocoder?src=trio&address=五道口保理学院",
                            "source": "locBaidu"
                        },
                        {
                            "id": "fc272e4a8d1788696040a9de",
                            "gpsType": "GCJ02",
                            "name": "五道口",
                            "address": "地铁13号线",
                            "lat": "39.99290863835344",
                            "lng": "116.33779587861828",
                            "subSource": "bdRegionSearch",
                            "thumbnail": "http://api.map.baidu.com/staticimage/v2?ak=ERcMaGj5nOE3EdvHYEEIKBeavMDpEkex&mcode=666666&width=480&height=360&zoom=18&center=116.34443389838,39.998568108173&markers=116.34443389838,39.998568108173",
                            "relScore": 1,
                            "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:pbiG8JmqcuHwxriIIUL1u0gMuyeGnSD-jzbeU7FXs19NViBPYcwc8i9RQEk-9XTov9GC8okf0ff0o_aI2foraAUaKRzvDSzkxxGMDE1r9S8SaO3yktxrywIi6I29GTU6kBtW_ZG1dVd65toRLsyfvBXcBxa4zRVAv7mlAacS7Udk96GXpohE8yVyawzaZKv2rBIlk-HK67K-O0fMzvMEFyQTUlt6bxZD",
                            "intent": "baidumap://map/geocoder?src=trio&address=五道口",
                            "source": "baiduMap"
                        },
                        {
                            "id": "BV10006886",
                            "cate": "交通设施服务;地铁站;地铁站",
                            "gpsType": "GCJ02",
                            "price": "",
                            "point": "",
                            "phone": "",
                            "name": "五道口(地铁站)",
                            "address": "北京市海淀区13号线",
                            "lat": "39.992894",
                            "lng": "116.337742",
                            "subSource": "gaodeRegionSearch",
                            "thumbnail": "http://api.map.baidu.com/staticimage/v2?ak=ERcMaGj5nOE3EdvHYEEIKBeavMDpEkex&mcode=666666&width=480&height=360&zoom=18&center=116.34437983754765,39.99855385030868&markers=116.34437983754765,39.99855385030868",
                            "relScore": 1,
                            "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:pbiG8JmqcuHwxriIIUL1u0gMuyeGnSD-jzbeU7FXs19NViBPYcwc8hifnVWmNHqQVjxWoUQhl3LzpfMpY_vxhMUk4elVp4ei_EQvTSqgXohx5gLdemwB75RNEwDeER7oIJPcqIEHuHMb7O5MnPfxxH-bWgXSNTtHo_Ucee4cteb-lDuZ00czWJBUufj4aILG",
                            "intent": "androidamap://poi?sourceApplication=trio&dev=0&keywords=%E4%BA%94%E9%81%93%E5%8F%A3",
                            "source": "Gaode"
                        }
                    ]
                },
                {
                    "token": "看",
                    "ner": "O",
                    "offset": 0,
                    "ner_prob": 0.9998791217803955
                },
                {
                    "token": "芳华",
                    "ner": "FILM",
                    "offset": -1,
                    "ner_prob": 0,
                    "film_list": [
                        {
                            "name": "芳华",
                            "point": "7.8",
                            "type": "剧情,战争,历史",
                            "id": "26862829",
                            "direcotr": "冯小刚",
                            "actor": "黄轩,苗苗,钟楚曦",
                            "posturl": "https://img3.doubanio.com/view/photo/s_ratio_poster/public/p2507227732.jpg",
                            "year": "2017",
                            "summary": "故事发生在上世纪七十年代，寄人篱下的少女何小萍（苗苗 饰）经过重重试炼终于加入了梦寐以求的文工团，哪知道这里和她曾经待过的那些地方并无不同，她依然得忍受遭人唾弃和欺侮的生活。唯一给过她温暖的，是刘峰（黄轩 饰），不仅仅是对何小萍，被称为“活雷锋”的刘峰把自己的爱情和温暖无私的奉献给每一个人。 实际上，刘峰一直爱慕着美丽活泼的林丁丁（杨采钰 饰），当他选择将这份感情勇敢的表达出来时，却让自己的人生走向了完全不同的方向。战争开始了，刘峰、何小萍和萧穗子前赴后继的走上了前线，在枪弹和炮火之中，每一个人都在用生命和热血绽放着属于他们的芳华。",
                            "country": "内地",
                            "casts": [
                                {
                                    "alt": "https://movie.douban.com/celebrity/1276105",
                                    "avatarUrl": "https://img1.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1449935218.59.jpg",
                                    "id": "1276105",
                                    "name": "黄轩"
                                },
                                {
                                    "alt": "https://movie.douban.com/celebrity/1366978",
                                    "avatarUrl": "https://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/pPfkhkmfc5Eocel_avatar_uploaded1483942631.13.jpg",
                                    "id": "1366978",
                                    "name": "苗苗"
                                },
                                {
                                    "alt": "https://movie.douban.com/celebrity/1357009",
                                    "avatarUrl": "https://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1513674760.63.jpg",
                                    "id": "1357009",
                                    "name": "钟楚曦"
                                }
                            ],
                            "preview": [
                                "",
                                "https://movie.douban.com/trailer/221510/#content"
                            ],
                            "rec_rel": [
                                {
                                    "name": "无问西东",
                                    "image": "https://img3.doubanio.com/view/photo/s_ratio_poster/public/p2507572275.jpg",
                                    "uid": "d807b1ed44f4e2846cbd3c43ad42348f",
                                    "year": "2018",
                                    "doubanId": "6874741",
                                    "type": [
                                        "剧情",
                                        "战争",
                                        "爱情"
                                    ],
                                    "intent": "douban://douban.com/movie/6874741?from=mdouba",
                                    "url": "https://movie.douban.com/subject/6874741"
                                },
                                {
                                    "name": "敦刻尔克",
                                    "image": "https://img3.doubanio.com/view/photo/s_ratio_poster/public/p2494950714.jpg",
                                    "uid": "82ec63df057fbf05ca0d4476a1881c2c",
                                    "year": "2017",
                                    "doubanId": "26607693",
                                    "type": [
                                        "剧情",
                                        "历史",
                                        "战争"
                                    ],
                                    "intent": "douban://douban.com/movie/26607693?from=mdouba",
                                    "url": "https://movie.douban.com/subject/26607693"
                                },
                                {
                                    "name": "嘉年华",
                                    "image": "https://img1.doubanio.com/view/photo/s_ratio_poster/public/p2503644828.jpg",
                                    "uid": "ec1195fbdc27f097bd53870b4c5c3fb6",
                                    "year": "2017",
                                    "doubanId": "27019527",
                                    "type": [
                                        "剧情"
                                    ],
                                    "intent": "douban://douban.com/movie/27019527?from=mdouba",
                                    "url": "https://movie.douban.com/subject/27019527"
                                }
                            ],
                            "rec_series": [],
                            "releaseTime": "2017-12-15",
                            "play_link": [
                                {
                                    "url": "http://v.youku.com/v_show/id_XMzM5NzQ0MTMwNA==.html",
                                    "source": "优酷视频"
                                },
                                {
                                    "url": "http://www.iqiyi.com/v_19rr7pe5k4.html",
                                    "source": "爱奇艺视频"
                                },
                                {
                                    "url": "http://v.qq.com/x/cover/ly2d18qrdchs2mm.html",
                                    "source": "腾讯视频"
                                }
                            ],
                            "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:pbiG8JmqcuHwxriIIUL1u0gMuyeGnSD-jzbeU7FXs19NViBPYcwc8i9RQEk-9XTo6NhUdbglVhs3WxlfdBJOnW30-KdvmFujwqgYMS59b09uaL6UAAe2EU3CDHGHgSmKJUdi0KaAb6DPPYgSF5y2dw==",
                            "intent": "douban://douban.com/movie/26862829?from=mdouba",
                            "source": "TrioFilm"
                        }
                    ]
                },
                {
                    "token": "。",
                    "ner": "O",
                    "offset": 0,
                    "ner_prob": 0.9999997615814209
                }
            ],
            "custom_info_list": [
                {
                    "id": "1167549",
                    "discript": "",
                    "thumbUrl": "http://img.gmw.cn/gmapp/gmrb_app_logo_900x500.jpg",
                    "pubTime": "2018-08-10 19:15:21",
                    "title": "​《粤韵芬芳》：向一代粤剧人的芳华致敬",
                    "url": "https://s.cloud.gmw.cn/2016/c/2018-08-10/1167549.shtml",
                    "source": "GM_NEWS",
                    "ref": {
                        "text": "我明天上午开会，结束后去五道口",
                        "attrMap": {
                            "endOffset": "15",
                            "startOffset": "0"
                        }
                    }
                },
                {
                    "id": "1163881",
                    "discript": "",
                    "thumbUrl": "https://s.cloud.gmw.cn/gmrb/upload/resources/image/2018/07/31/6575073.jpg",
                    "pubTime": "2018-07-31 14:27:59",
                    "title": "独臂退伍老兵创业致富绽芳华 ",
                    "url": "https://s.cloud.gmw.cn/2016/c/2018-07-31/1163881.shtml",
                    "source": "GM_NEWS",
                    "ref": {
                        "text": "我明天上午开会，结束后去五道口",
                        "attrMap": {
                            "endOffset": "15",
                            "startOffset": "0"
                        }
                    }
                }
            ]
        }
    ]
}
```
示例返回（无网情况）：
```
{
    "error_code":0,
    "fromRemote":false,
    "query":"我明天上午开会，结束后去五道口看芳华。",
    "result_list":[
        {
            "term_list":[
                {
                    "ner":"O",
                    "ner_prob":0,
                    "token":"我"
                },
                {
                    "calendar_list":[
                        {
                            "endTimeStamp":-1,
                            "startTimeStamp":1535072400000,
                            "theme":"会议提醒"
                        }
                    ],
                    "ner":"CLOCK",
                    "ner_prob":0,
                    "token":"明天上午"
                },
                {
                    "ner":"O",
                    "ner_prob":0,
                    "token":"开会"
                },
                {
                    "ner":"O",
                    "ner_prob":0,
                    "token":"，"
                },
                {
                    "ner":"O",
                    "ner_prob":0,
                    "token":"结束"
                },
                {
                    "ner":"O",
                    "ner_prob":0,
                    "token":"后"
                },
                {
                    "ner":"O",
                    "ner_prob":0,
                    "token":"去"
                },
                {
                    "ner":"O",
                    "ner_prob":0,
                    "token":"五道口"
                },
                {
                    "ner":"O",
                    "ner_prob":0,
                    "token":"看"
                },
                {
                    "ner":"O",
                    "ner_prob":0,
                    "token":"芳华"
                },
                {
                    "ner":"O",
                    "ner_prob":0,
                    "token":"。"
                }
            ],
            "divided_list":[
                "我",
                "明天上午",
                "开会",
                "，",
                "结束",
                "后",
                "去",
                "五道口",
                "看",
                "芳华",
                "。"
            ]
        }
    ]
}
```

对于一种类型对应多个服务的情况，我们会返回每个服务跳转APP的intentUri和H5页面的url，有些App没有跳转的intent或者H5页面，则此项为空。

**【注意】手机ROM需要给SDK开启位置获取权限，否则基于用户当前位置的实体信息将无法返回，如美团网信息。**

##### 4.5 通用卡片展示
通用卡片是指我们提前在客户端埋设一些模板样式，然后由服务器动态指定需要展示的目标类型，并下发展示数据，从而实现相对灵活的展示效果。通用卡片的数据放在NerResultItem下面的customInfoItems里面。
![](/assets/sdk/custom_info_list.png)
CustomInfoItem定义如下，用于存储各类通用卡片的信息：

```
public class CustomInfoItem extends BaseModel {
    public String viewId;  // 卡片模板编号
    public String type;    // 卡片类型，如"AD"代表广告
    public CustomItemHeader header;  // 卡片头部信息
    public CustomItemData data; // 卡片主体信息
    public CustomItemRef ref;   // 卡片对应的实体信息

    public class CustomItemData extends BaseModel {
        // 标题
        public CustomItemDataTitle title;
        // 副标题
        public ArrayList<CustomItemDataSubTitle> subTitles;
        // 描述信息，例如导演，简介等。attr中保存部分特殊ui元素，如评分等
        public ArrayList<CustomItemDataDesc> descs;
        // 主要图片url
        public ArrayList<CustomItemDataPic> pics;
        // 点击跳转url
        public ArrayList<CustomItemDataUrl> urls;
        // buttons 信息
        public ArrayList<CustomItemDataButton> buttons;
        // 若卡片样式中包含小图标，此处保存小图标url
        public ArrayList<CustomItemDataUrl> iconUrls;

        public class CustomItemDataTitle extends BaseModel {
            public String content;
        }

        public class CustomItemDataSubTitle extends BaseModel {
            public String content;
        }

        public class CustomItemDataDesc extends BaseModel {
            public ArrayList<Attr> attr;
            public String content;

            public class Attr {
                public String key;
                public String value;
            }
        }

        public class CustomItemDataPic extends BaseModel {
            public String url;

        }

        public class CustomItemDataUrl extends BaseModel {
            public String url;
            public ArrayList<CustomItemDataAttr> attr;

            public class CustomItemDataAttr extends BaseModel {
                public String key;
                public String value;
            }
        }

        public class CustomItemDataButton extends BaseModel {
            public String content;
        }
    }

    public class CustomItemRef extends BaseModel {
        public String text;
        public String ner;
        public CustomItemRefAttr attrMap;


        public class CustomItemRefAttr extends BaseModel {
            public String position;
        }
    }

    public class CustomItemHeader extends BaseModel {
        public String logoPicUrl;
        public String name;
    }

}
```
卡片类型
ui_tpl_13（目前只定义了这一种通用卡片，接下来会加入更多）：
界面元素分布如下：
![](/assets/sdk/ui_tpl_13.png)
视觉效果可以参考下面两种：
![](/assets/sdk/ui_tpl_13_demo.png)

#### 5. 附录
#####附录1：支持类型表（动态扩展中）
![](/assets/sdk/support_type_1)
![](/assets/sdk/support_type_2.jpg)
![](/assets/sdk/support_type_3.jpg)
![](/assets/sdk/support_type_4.jpg)

#####附录2：NERItem数据结构的详细定义
```
public class NERItem extends BaseModel {
    public NERItem() {
    }

    public NERItem(String token, String ner) {
        this.token = token;
        this.ner = ner;
    }

    @SerializedName("token")  // 实体名称，如"五道口"
    public String token;

    @SerializedName("ner")  // 实体类型，如"ADDR"
    public String ner;

    @SerializedName("ner_prob")
    public double probability; // 概率，如0.7


    @SerializedName("film_list")
    public ArrayList<FilmInfo> filmInfoList; // 电影、电视预览信息

    @SerializedName("cinemaInfo_list")
    public ArrayList<CinemaInfo> cinemaInfoList; // 影院预览信息

    @SerializedName("meituan_list")
    public ArrayList<MeituanInfo> meituanInfoList; // 美团网预览信息

    @SerializedName("taokouling_list")
    public ArrayList<TaoKouLingInfo> taoKouLingInfoList; // 淘口令预览信息

    @SerializedName("feiyou_flight_list")
    public ArrayList<FeiyouFlightInfo> feiyouFlightInfoList; // 飞友航班预览信息

    @SerializedName("train_list")
    public ArrayList<TrainInfo> trainInfoList; // 火车预览信息

    @SerializedName("address_list")
    public ArrayList<AddressInfo> addressInfoList; // 地点预览信息

    @SerializedName("person_list")
    public ArrayList<PersonInfo> personInfoList; // 名人信息

    @SerializedName("calendar_list")
    public ArrayList<CalendarInfo> calendarInfoList; // 日程

    @SerializedName("kuaidi_list")
    public ArrayList<ExpressInfo> expressInfoList; // 快递


    public static abstract class InfoBase extends BaseModel { // 公共部分
        @SerializedName("url") // 跳转H5页面的url
        public String url;

        @SerializedName("intent") // 跳转App的intent
        public String intentUri;
    }

    public static class FilmInfo extends InfoBase {
        @SerializedName("id") // 电影id
        public String id;

        @SerializedName("type") // 电影类别，多个类别用英文逗号分隔，如"惊悚,悬疑"
        public String type;

        @SerializedName("name") // 电影名
        public String name;

        @SerializedName("buy_url") // 电影购票链接（在映的电影有这个字段，否则为空）
        public String buyUrl;

        @SerializedName("point") // 电影得分
        public String point;

        @SerializedName("direcotr") // 导演
        public String direcotr;

        @SerializedName("actor") // 演员表
        public String actor;

        @SerializedName("posturl") // 海报
        public String posturl;

        @SerializedName("year") // 年份
        public String year;

        @SerializedName("summary") // 简介
        public String summary;

        @SerializedName("country") // 国家
        public String country;
    }

    public static class CinemaInfo extends InfoBase {
        @SerializedName("type") // 电影类别，多个类别用英文逗号分隔，如"惊悚,悬疑"
        public String type;

        @SerializedName("name") //电影名称
        public String name;

        @SerializedName("point") //电影评分
        public String point;

        @SerializedName("showst") //是否上映 0:未上映  1:上映
        public String showst;
    }

    public static class MeituanInfo extends InfoBase {
        @SerializedName("id") // 商铺id
        public String id;

        @SerializedName("name") // 商铺名
        public String name;

        @SerializedName("address") // 位置
        public String address;

        @SerializedName("price") // 人均消费
        public String price;

        @SerializedName("point") // 评分
        public String point;

        @SerializedName("distance") // 距离
        public String distance;

        @SerializedName("phone") // 电话列表，010-84613688/84899003/84899013
        public String phone;

        @SerializedName("cityname") // 城市名
        public String cityname;

        @SerializedName("frontimg") // 海报
        public String frontimg;

        @SerializedName("cate") // 类别 （酒店）
        public String cate;

        @SerializedName("subcate") // 子类 （经济型酒店）
        public String subcate;

        @SerializedName("wifi") // 是否有wifi，1表示有，0没有
        public String wifi;

        @SerializedName("waimai") // 是否提供外卖，1提供，0不提供
        public String waimai;
    }

    public static class TaoKouLingInfo extends InfoBase {
        @SerializedName("name") // 商品信息
        public String name;

        @SerializedName("price") // 价格
        public String price;

        @SerializedName("id") // 商品id
        public String id;

        @SerializedName("thumb_pic_url") // 商品缩略图
        public String thumbPicUrl;
    }


    public static class FeiyouFlightInfo extends InfoBase {
        @SerializedName("flightNo") // 航班号 CA4506
        public String flightNo;

        @SerializedName("flightCompany") // 航空公司  中国国际航空股份有限公司
        public String flightCompany;

        @SerializedName("flightDepcode") // 出发城市三字码 NKG
        public String flightDepcode;

        @SerializedName("flightArrcode") // 到达城市三字码 XIY
        public String flightArrcode;

        @SerializedName("FlightHTerminal") // 出发航站楼
        public String flightStartTerminal;

        @SerializedName("FlightTerminal")  // 到达航站楼
        public String flightEndTerminal;

        @SerializedName("flightDeptimePlanDate") // 计划起飞时间 2017-07-30 16:35:00
        public String flightDeptimePlanDate;

        @SerializedName("flightArrtimePlanDate") // 计划到达时间 2017-07-31 00:00:00
        public String flightArrtimePlanDate;

        @SerializedName("flightDep") // 起飞城市 南京
        public String flightDepCity;

        @SerializedName("flightArr") // 到达城市 西安
        public String flightArrCity;

        @SerializedName("flightDepAirport") // 起飞机场 南京禄口
        public String flightDepAirport;

        @SerializedName("flightArrAirport") // 到达机场 西安咸阳
        public String flightArrAirport;

        @SerializedName("ontimeRate") // 准点率 100.00%
        public String ontimeRate;

        @SerializedName("flightDuration") // 飞行时间 104
        public String flightDuration;

        @SerializedName("distance") // 飞行距离 1104
        public String distance;
    }

    public static class AddressInfo extends InfoBase {
        @SerializedName("name") // 地点名
        public String name;
    }

    public static class TrainInfo extends InfoBase {
        @SerializedName("from") // 火车出发站
        public String from;

        @SerializedName("destination") // 终点站
        public String destination;

        @SerializedName("start_time") // 发车时间
        public String startTime;

        @SerializedName("end_time") // 到达时间
        public String endTime;

        @SerializedName("id") // 火车班次
        public String id;

        @SerializedName("cross_days")
        public int crossDays = -1; // 跨天数量：<0:没有跨天信息 0:当天到达  1:第二天到达  2:第三天到达，依次类推
    }

    public static class PersonInfo extends InfoBase {
        @SerializedName("name")  // 人名
        public String name;

        @SerializedName("job")  // 职业
        public String job;

        @SerializedName("pic_url") // 海报
        public String picUrl;

        @SerializedName("summary") // 人物简介
        public String summary;

        @SerializedName("is_contact") // 是否在通讯录
        public boolean isContact;
    }

    public static class CalendarInfo extends InfoBase {
        @SerializedName("startTimeStamp")
        public long startTimeStamp;  // 开始时间戳

        @SerializedName("endTimeStamp")
        public long endTimeStamp;  // 结束时间戳 <0表示没有截止时间

        @SerializedName("theme")
        public String theme;   // 主题  "开会"
    }

    public static class ExpressInfo extends InfoBase {
        @SerializedName("id") // id
        public String id;

        @SerializedName("detail_url") // 详情页url
        public String detailUrl;

        @SerializedName("source") // 数据来源，如"KD100"
        public String source;

        @SerializedName("vendor") // 快递公司名，如"韵达快递"
        public String vendor;

        @SerializedName("tel") // 快递电话
        public String tel;

        @SerializedName("state") // 快递状态
        public String state;

        @SerializedName("detail") // 快递行程列表
        public ArrayList<ExpressDetailInfo> expressDetailInfoList;
    }

    public static class ExpressDetailInfo extends InfoBase {
        @SerializedName("time") // 时间
        public String time;

        @SerializedName("context") // 快递状态
        public String context;
    }
}
```

#####附3：类型常量的定义
可以通过NERType类里面定义的NER类别常量来进行NER类别的比较。
```
public class NERType extends BaseModel {
    public static final String OTHER = "O";

    public static final String ADDR = "ADDR";
    public static final String ADMIN = "ADMIN";
    public static final String SCENE = "SCENE";
    public static final String STATION = "STATION";
    public static final String SCHOOL = "SCHOOL";

    public static final String CATER = "CATER";
    public static final String HOTEL = "HOTEL";


    public static final String FILM = "FILM";
    public static final String TV = "TV";
    public static final String TV_SHOW = "TV_SHOW";

    public static final String PERSON_NAME = "PERSON_NAME";

    public static final String TAOBAO_PROD_ID = "TAOBAO_PROD_ID";

    public static final String FLIGHT_NUM = "FLIGHT_NUM";
    public static final String TRAIN_NUM = "TRAIN_NUM";

    public static final String URL = "URL";

    public static final String DATE = "DATE";
    public static final String DAY = "DAY";
    public static final String CLOCK = "CLOCK";

    public static final String PHONE_NUM = "PHONE_NUM";
    public static final String STOCK_NAME = "STOCK_NAME";

    public static final String EXPRESS_CODE = "EXPRESS_CODE";
    public static final String APP_NAME = "APP_NAME";
}
```
#####附4：使用Intent打开App的方式
```
Intent intent = new Intent();
intent.setAction("android.intent.action.VIEW");
intent.addCategory("android.intent.category.DEFAULT");
intent.setData(Uri.parse(UriString));

startActivity(intent);
```
