># 基础协议

####1.基础协议参数

|参数名|参数含义|类型|示例|是否必须|
|:---|:---|:---|:---|:---|
|appId|应用 ID|string|11000|y|
|signature|鉴权签名|string|b893e573bb320bd0ba2f51fe873cb5a897c9ef46|y|
|timestamp|UTC 时间戳|string|1526615661|y|
|longitude|GPS 经度|string|118.484954|y|
|latitude|GPS 维度|string|40.607182|y
|gpsType|gps编码类型，目前支持（GCJ02火星坐标系，WPS84，BD09百度地图坐标系）。默认为火星坐标系GCJ02|string|GCJ02|y|
|fromApp|智慧识屏用户操作的app|string|com.baidu.search|y|
|deviceId|设备 ID，用于标示用户|string|5a836eb568f2177f9c96e6aba4ea3abd|y|
|log_id|请求 ID。如果没有，服务器会生成uuid.|string|3589cee8-a2c6-45b2-936e-20fc6e3adc0e|y|


