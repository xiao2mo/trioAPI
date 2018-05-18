## WEB API 服务
    三角兽智慧识屏WEB API服务，为开发者提供http/https接口。
    开发者通过http/https的方式发送post请求，返回json格式的数据。
    目前提供的服务包括：基础nlp识别服务，以及基于意图的资源卡片服务。
## 服务类型
|接口名称|接口功能|请求示例|
|:---:|:---:|:---:|
|nlp+资源卡片二合一|输入query，实现基础nlp服务以及基于意图的资源卡片服务|http://phoneapi.sanjiaoshou.net/nlp|
|nlp服务|基础nlp的分词和实体识别服务|http://phoneapi.sanjiaoshou.net/nlp/segmentation|
|资源卡片服务|根据命名实体和意图获取资源卡片|http://phoneapi.sanjiaoshou.net/nlp/resource|

## 服务授权
     
#### 获取appKey
    阅读三角兽Web API服务条款后，发送邮件到 phoneapi@trio.ai 来申请appKey.
    我们收到邮件后，会人工审核和联系，在审批通过之后，会通过邮件发送appId和appKey.
#### 服务授权方式
    客户端使用appId, appKey, 请求服务的类型，以及当前的时间戳(utc时间）生成签名signature, 服务器端会根据
    传过来的appId, timestamp, signature 进行鉴权。
    下表为鉴权失败时的错误码列表
    
#### 客户端生成签名的代码示例
```java
requestTime = System.currentTimeMillis() / 1000;
timeStamp = String.valueOf(requestTime);
signature = genSignature(appKey, timeStamp, SERVICE_NLP);        
```

生成签名的函数demo，可以在以下位置下载
