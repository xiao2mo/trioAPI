># 在线识别

####1.在线识别增量参数

|参数名|参数含义|类型|示例|是否必须|
|:---:|:---:|:---:|:---:|:---:|
|appId|应用id|string|11000|y|
|signature|鉴权签名|string|b893e573bb320bd0ba2f51fe873cb5a897c9ef46|y|
|timestamp|utc 时间戳|string|1526615661|y|
|appId|应用 id|string|11000|y|

|appId|应用 id|string|11000|y
|appId|应用 id|string|11000|y|
|appId|应用 id|string|11000|y|
|appId|应用 id|string|11000|y|

####2.请求 json 示例
```json
{"userId": "trio","city_name":"北京", "longitude":"113.937862","latitude":"22.521726","query": "肯德基"}
```
####3.返回 json 结构
|字段名称|子字段|字段含义|字段类型|
|:---:|:---:|:---:|:---:|
|error_code|------|返回状态码|int|



####4.返回 json 示例
```json
{
    "error_code": 0,
    "error_msg": "success",
    "query": "肯德基",
    "result_list": [
        {
            "divided_list": [
                "肯德基"
            ],
            "domain_list": [
                {
                    "name": "美食",
                    "value": 0.948304295539856
                },
                {
                    "name": "其它",
                    "value": 0.01913728192448616
                },
                {
                    "name": "地图",
                    "value": 0.010585445910692215
                }
            ],
            "term_list": [
                {
                    "token": "肯德基",
                    "ner": "CATER"
                }
            ]
        }
    ],
    "log_id": "d3ee71fb-6c69-4f76-a366-2508287c5f78"
}
```