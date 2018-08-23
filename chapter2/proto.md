## 请求参数
#### 基础请求参数
基础请求参数为接口共同共用的，请求参数如下

|参数名|参数含义|类型|示例|是否必须|
|:---:|:---:|:---:|:---:|:---:|
|appId|应用id|string|11000|y|
|signature|鉴权签名|string|b893e573bb320bd0ba2f51fe873cb5a897c9ef46|y|
|timestamp|客户端的utc时间戳(s)|string|1526615661|y|
|longitude|gps经度|string|118.484954|y|
|latitude|gps维度|string|40.607182|y|
|gpsType|gps编码类型，目前支持（GCJ02火星坐标系，WPS84，BD09百度地图坐标系）。默认为火星坐标系GCJ02|string|GCJ02|n|
|fromApp|智慧识屏用户操作的app|string|com.tencent.mm|n|
|deviceId|<p>设备id，用于标示用户。<p>为保护用户隐私，可以基于硬件设备的唯一id(imei,mac地址）进行不可逆的加密（MD5,HMAC)。|string|5a836eb568f2177f9c96e6aba4ea3abd|n|
|log_id|session id，一次智慧识屏请求在生存期内共享相同的log_id,由初次请求时服务器生成|string|3589cee8-a2c6-45b2-936e-20fc6e3adc0e|n|

### 基础返回参数

|参数名|参数含义|类型|示例|
|:---:|:---:|:---:|:---:|
|error_code|错误码|int|0|
|error_msg|错误信息|string|"succ"|
|log_id|session id，一次智慧识屏请求在生存期内共享相同的log_id, 由初次请求时服务器生成|string| 3589cee8-a2c6-45b2-936e-20fc6e3adc0e|
|elapse_time|服务器处理时间(ms)|int|200|

#### 错误码
|错误码|错误信息|定义|常见原因|
|:---:|:---:|:---:|:---:|
|0|succ|正常|服务请求正常返回|
|2|no appid|缺少参数appId|typo|
|2|no sig|缺少参数signature|typo|
|2|timestamp format error|参数timestamp格式错误|应当是utc的秒数|
|2|request time exceed system allowed time period|客户端时间戳与服务器时间戳相差时间过长（超过10分钟）|<p>观察客户端时间是否正常，<p>观察客户端时区设置是否为北京时间所在+8区|
|2|authorization failed|鉴权失败|与示例代码进行对比，观察json是否完全一致|