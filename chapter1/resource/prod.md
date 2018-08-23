>#商品信息卡片

####1.测试 Demo
{%fbq%}
term:##商品名称##
ner:##PROD##
{%endfbq%}
####2.返回 Json 示例
```json
{
    "id": "5089253",
    "name": "Apple iPhone X (A1865) 64GB 深空灰色 移动联通电信4G手机",
    "shopId": "1000000127",
    "point": "99",
    "imageUrl": "https://img30.360buyimg.com/jgsq-productsoa/jfs/t10675/253/1344769770/66891/92d54ca4/59df2e7fN86c99a27.jpg",
    "url": "http://phoneapi.sanjiaoshou.net/nlp/q?key:kmS5XyPnNzxUhzYS8jDbm3bU67IPqRzpGxmVA7h_5lfuaFK2Z4uZHBRMAfhGnd8YLeF9aCMS-08Es7x9JUfdNiqeyZT29UDbOQNeEf2LZ3RpwLkxmflQ0h8Xtxh9eFuWToGkLq_j8bk=",
    "intent": "openapp.jdmobile://virtual?params={\"category\":\"jump\",\"des\":\"productDetail\",\"skuId\":\"5089253\",\"sourceType\":\"unknown\",\"sourceValue\":\"unknown\",\"M_sourceFrom\":\"sxtop\",\"msf_type\":\"click\",\"m_param\":{\"m_source\":\"0\",\"event_series\":{},\"jda\":\"122270672.15127185830131661088761.1512718583.1512718583.1512718583.1\",\"usc\":\"baidu-pinzhuan\",\"ucp\":\"t_288551095_baidupinzhuan\",\"umd\":\"cpc\",\"utr\":\"36e78a1acce545f59c3461c890d009a9_0_4d3505762a844dbabcc13d4dedf87db4\",\"jdv\":\"122270672%7Cbaidu-pinzhuan%7Ct_288551095_baidupinzhuan%7Ccpc%7C36e78a1acce545f59c3461c890d009a9_0_4d3505762a844dbabcc13d4dedf87db4%7C1512718583038\",\"ref\":\"https%3A%2F%2Fitem.m.jd.com%2Fproduct%2F2397497.html\",\"psn\":\"15127185830131661088761|1\",\"psq\":4,\"unpl\":\"\",\"pc_source\":\"\",\"mba_muid\":\"15127185830131661088761\",\"mba_sid\":\"15127185830524599070494097937\",\"mt_xid\":\"\",\"mt_subsite\":\"\"},\"SE\":{\"mt_subsite\":\"\",\"__jdv\":\"122270672%7Cbaidu-pinzhuan%7Ct_288551095_baidupinzhuan%7Ccpc%7C36e78a1acce545f59c3461c890d009a9_0_4d3505762a844dbabcc13d4dedf87db4%7C1512718583038\",\"unpl\":\"\",\"__jda\":\"122270672.15127185830131661088761.1512718583.1512718583.1512718583.1\"}}",
    "source": "JD"
}
```

####3.返回字段说明

>卡片字段名称：jd_ware_list

|名称|说明|类型|示例|
|:---|:---|:---|:---|
|id|商品id|string|5089253|
|name|商品名称|string|Apple iPhone X (A1865) 64GB 深空灰色 移动联通电信4G手机|
|imageUrl|商品缩略图|string|https://img30.360buyimg.com/jgsq-productsoa/jfs/t10675/253/1344769770/66891/92d54ca4/59df2e7fN86c99a27.jpg|
|point|商品评分|string|99|
|~~price~~|~~商品价格~~|string|7299.00|
|shopId|商品店铺id|string|1000000127|
|url|商品H5跳转链接|string|http://phoneapi.sanjiaoshou.net/nlp/q?key:kmS5XyPnNzxUhzYS8jDbm3bU67IPqRzpGxmVA7h_5lfuaFK2Z4uZHBRMAfhGnd8YLeF9aCMS-08Es7x9JUfdNiqeyZT29UDbOQNeEf2LZ3RpwLkxmflQ0h8Xtxh9eFuWToGkLq_j8bk=|
|intent|商品app跳转链接|string|openapp.jdmobile://virtual?params={\"category\":\"jump\",\"des\":\"productDetail\",\"skuId\":\"5089253\",\"sourceType\":\"unknown\",\"sourceValue\":\"unknown\",\"M_sourceFrom\":\"sxtop\",\"msf_type\":\"click\",\"m_param\":{\"m_source\":\"0\",\"event_series\":{},\"jda\":\"122270672.15127185830131661088761.1512718583.1512718583.1512718583.1\",\"usc\":\"baidu-pinzhuan\",\"ucp\":\"t_288551095_baidupinzhuan\",\"umd\":\"cpc\",\"utr\":\"36e78a1acce545f59c3461c890d009a9_0_4d3505762a844dbabcc13d4dedf87db4\",\"jdv\":\"122270672%7Cbaidu-pinzhuan%7Ct_288551095_baidupinzhuan%7Ccpc%7C36e78a1acce545f59c3461c890d009a9_0_4d3505762a844dbabcc13d4dedf87db4%7C1512718583038\",\"ref\":\"https%3A%2F%2Fitem.m.jd.com%2Fproduct%2F2397497.html\",\"psn\":\"15127185830131661088761|1\",\"psq\":4,\"unpl\":\"\",\"pc_source\":\"\",\"mba_muid\":\"15127185830131661088761\",\"mba_sid\":\"15127185830524599070494097937\",\"mt_xid\":\"\",\"mt_subsite\":\"\"},\"SE\":{\"mt_subsite\":\"\",\"__jdv\":\"122270672%7Cbaidu-pinzhuan%7Ct_288551095_baidupinzhuan%7Ccpc%7C36e78a1acce545f59c3461c890d009a9_0_4d3505762a844dbabcc13d4dedf87db4%7C1512718583038\",\"unpl\":\"\",\"__jda\":\"122270672.15127185830131661088761.1512718583.1512718583.1512718583.1\"}}| 
|source|商品来源，目前支持京东(source=JD)|string|JD|

** ~~删除线部分为暂时缺失的字段~~ **

####4.UI 效果展示
>商品资源卡片展示


<div align="center">
<img src="/assets/chapter1/jingdong.png" align="center" alt="电影资源卡片实例">
</div>

























