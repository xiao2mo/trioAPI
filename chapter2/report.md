## 应用打点协议
使用http post协议进行打点，
服务器地址为

|环境|服务器地址|说明|
|:---:|:---:|:---:|
|测试环境|http://triophone.sanjiaoshou.net/nlp/click||
|正式环境|http://phoneapi.sanjiaoshou.net/nlp/click||

## 请求参数
基础请求参数同[WEB API服务的基础请求参数](../chapter2/proto.md)，此外，还包括跟打点协议相关的参数

### 参数说明

|参数名|参数含义|类型|示例|是否必须|
|:---:|:---:|:---:|:---:|:---:|
|term|卡片点击的文本|string|头号玩家|否|
|ner|卡片点击对应的[实体类型](../chapter1/nlp_ner.md)|string|FILM|否|
|position|<p>长按位置（屏幕横纵坐标，使用距离左边和底部的百分比，使用逗号隔开，依次为x,y) <p>点击位置（卡片list中的index|string|<p>0.2,0.8 <p>0|否|
|operation|点击操作名称|string|DETAIL_URL|是|
|source|三角兽的资源为TRIO，非三角兽的资源为OTHER|string|TRIO|否，默认为TRIO|
|url|点击跳转的目标url（H5或deeplink）|string|https://movie.douban.com/subject/4920389/|否|


按照智慧识屏的产品逻辑，点击的操作 可分为用户状态，卡片展示，卡片点击 三种类型，
每种点击操作，对应的**operation**有一个确定的列表。客户需要根据当前点击的类型，修改对应的operation字段。

我们列举了一些常用的操作逻辑，如果需要的操作逻辑不在列表中，可以通过邮件发送给 **phoneapi@trio.ai**, 我们会添加该操作逻辑进列表。

### 展示打点
卡片展示逻辑的设计建议参见 [卡片展示设计建议](../chapter1/card_ui/display_suggest.md)
#### 展示操作列表
||操作类型|operation|含义|示例|notes|
|---|:---:|:---:|:---:|:---:|:---:|
|<td rowspan=4>卡片展示 | DISPLAY_FAIL|请求三角兽服务器，如果展示失败（服务器超时，服务器返回错误的错误码）|{<p>"appId":"put_your_appId_here",<p>"log_id": "put_previouse_reponse_log_id_here",<p>"operation": "DISPLAY_FAIL"<p>}|
||CARD_UNFOLD|弹出卡片展开|{<p>"appId":"put_your_appId_here",<p>"log_id": "put_previouse_reponse_log_id_here",<p>"operation": "CARD_UNFOLD"<p>}|
||CARD_FOLD|弹出卡片收起|{<p>"appId":"put_your_appId_here",<p>"log_id": "put_previouse_reponse_log_id_here",<p>"operation": "CARD_FOLD"<p>}|
||CARD_SCROLL|卡片滑动|{<p>"appId":"put_your_appId_here",<p>"log_id": "put_previouse_reponse_log_id_here",<p>"operation": "CARD_SCROLL"<p>}|
#### 示例json

```
{ "appId": "10015", "log_id": "d78aead0-c24d-4f5a-bc0e-ce93dd076968", "operation": "DISPLAY_FAIL"}
```
### 点击打点
#### 点击操作列表
||操作类型|operation|含义|示例|notes|
|---|:---:|:---:|:---:|:---:|:---:|
|<td rowspan=8>普通卡片操作区按钮 | DETAIL|点击卡片的主要跳转url，均使用DETAIL，点击进入详情页H5或deeplink|{<p>"appId":"put_your_appId_here",<p>"term":"头号玩家",<p>"ner":"FILM",<p>"url":"https://movie.douban.com/subject/4920389/",<p>"log_id": "put_previouse_reponse_log_id_here",<p>"operation": "DETAIL"<p>}|
||PHONE|弹出卡片展开||
||COLLECTION|弹出卡片收起||
||NAV|卡片滑动||
||PLAY|卡片滑动||
||REL|卡片滑动||
||BUY|卡片滑动||
||READ|卡片滑动||
|<td rowspan=5>切词卡片操作按钮 | SELECT_ALL|全选||
||COPY|复制|{<p>"appId":"put_your_appId_here",<p>"term":"头号玩家票房",<p>"log_id": "put_previouse_reponse_log_id_here",<p>"operation": "COPY"<p>}|
|| SEARCH |检索|{<p>"appId":"put_your_appId_here",<p>"term":"头号玩家票房",<p>"url":"https://baidu.com/s=头号玩家票房",<p>"log_id": "put_previouse_reponse_log_id_here",<p>"operation": "SEARCH"<p>}|
||SHARE|分享||
||TRANSLATE|翻译||
|<td rowspan=1>其他点击操作|OTHER|如果不在上述按钮定义范围内，统一用OTHER||

#### 示例json

```
{ "appId": "10015", "term": "头号玩家票房", "url": "https://baidu.com/s=头号玩家票房" "log_id": "d78aead0-c24d-4f5a-bc0e-ce93dd076968", "operation": "SEARCH"}
```

### 用户状态打点
#### 状态操作列表
||操作类型|operation|含义|示例|notes|
|---|:---:|:---:|:---:|:---:|:---:|
|<td rowspan=6>开关状态 | FUNC_OPEN|智慧识屏主功能打开|{<p>"appId":"put_your_appId_here",<p>"operation": "FUNC_OPEN"<p>}|
|| FUNC_CLOSE |智慧识屏主功能关闭||
|| FUNC_1_OPEN |智慧识屏副功能打开||
|| FUNC_1_CLOSE |智慧识屏副功能关闭||
|| FUNC_APP_OPEN |智慧识屏对应app功能开启|{<p>"appId":"put_your_appId_here",<p>"operation": "FUNC_APP_OPEN",<p>"url":"com.tencent.mm",<p>}|<p>智慧识屏可以让用户配置，在哪些app上，可以触发智慧识屏. <p>在url字段，放入app的packagename|
|| FUNC_APP_CLOSE |智慧识屏对应app功能关闭||



#### 示例json

```
{ "appId": "10015", "deviceId": "2b3eb1cd7e97dc35c260ac1d982c43e6", "url": "com.tencent.mm", "log_id": "d78aead0-c24d-4f5a-bc0e-ce93dd076968", "operation": "FUNC_APP_OPEN"}
```

## 返回参数
返回参数与[WEB API基础协议](../chapter2/proto.md)的返回参数一致。