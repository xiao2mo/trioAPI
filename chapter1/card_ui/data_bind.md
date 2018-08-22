### 返回字段说明

|名称|说明|类型|示例|
|:---|:---|:---|:---|
|viewId|卡片UI|string|ui_tpl_13|
|type| 卡片种类 |string  |AD或GENERAL  |
|header|卡片头部|string|---|
|header.logoPicUrl|头部图标|string|http://a1.att.hudong.com/26/36/20200000013920144735363576977_s.jpg|
|header.name|头部名称|string|影片信息|
|data|卡片数据|---|---|
|data.title|标题|string[]|---|
|data.title.content| 标题文本| string|一出好戏 |
|data.subTitles| 副标题|string[] |--- |
|data.subTitles.content|副标题文本|string|喜剧|
|data.descs|描述|string[]|---|
|data.descs.content| 描述文本|string |导演：黄渤 |
|data.descs.attr|特殊元素|string[]|---|
|data.descs.attr.key|元素名称|string|star|
|data.descs.attr.value|元素值|string|4.5|
|data.pics| 图片|string[] |--- |
|data.pics.url|图片地址|string|http://game.stargame.com/data/attachments/2018/04/18/1524040667499024.jpg|
|data.iconUrls|小图标url|string[]|---|
|data.iconUrls.url|小图标地址|string|http://a1.att.hudong.com/26/36/20200000013920144735363576977_s.jpg|
|data.urls| 跳转url|string[] | ---|
|data.urls.url|跳转url|string|https://movie.douban.com/subject/26985127/|
|data.buttons|按钮|string[]|---|
|data.buttons.content|按钮文本|string|获取|
|data.footer|卡片备注|string[]|该卡片由三角兽提供|


### 数据与卡片绑定
#### 示例Json1
```
{
    "viewId": "ui_tpl_13",
    "type": "GENERAL",
    "data": {
        "title": {
            "content": "一出好戏"
        },
        "subTitles": [
            {
                "content": "剧情"
            },
            {
                "content": "喜剧"
            },
            {
                "content": "巨幕"
            },
            {
                "content": "杜比音效"
            }
        ],
        "descs": [
            {
                "content": "导演：黄渤"
            },
            {
                "content": "演员：黄渤，舒淇，王宝强"
            },
            {
                "content": "简介：马进欠下债务，与远房表弟小兴在底层社会摸爬滚打，习惯性的买彩票，企图一夜爆富，并迎娶自己的同事姗姗。一日，公司全体员工出海团建，途中，马进收到了彩票中头奖的信息，六千万！就在马进狂喜自己翻身的日子终于到来之际，一场突如其来的滔天巨浪打破了一切。苏醒过来的众人发现身处荒岛，丧失了一切与外界的联系……"
            }
        ],
        "pics": [
            {
                "url": "https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1534398953477&di=30bde30f736c4123c897728e4c996d55&imgtype=0&src=http%3A%2F%2Fimg5.mtime.cn%2Fmg%2F2018%2F07%2F29%2F131402.92915661.jpg"
            }
        ],
        "urls": [
            {
                "url": "https://movie.douban.com/subject/26985127/"
            }
        ]
    },
    "ref": {
        "text": "秒拍app,一出好戏",
        "ner": "O",
        "attrMap": {
            "position": "-1"
        }
    }
}
```

#### 对应卡片1：ui样式为ui_tpl_13
![avatar](/chapter1/card_ui/sample/ui_tpl_13_bind.jpg)


#### 示例Json2
```
{
    "viewId": "ui_tpl_1",
    "type": "AD",
    "data": {
        "title": {
            "content": "秒拍"
        },
        "subTitles": [],
        "descs": [
            {
                "attr": [
                    {
                        "key": "star",
                        "value": "4.5"
                    },
                    {
                        "key": "size",
                        "value": "12.0M"
                    }
                ]
            }
        ],
        "pics": [
            {
                "url": "http://game.stargame.com/data/attachments/2018/04/18/1524040667499024.jpg"
            }
        ],
        "urls": [
            {
                "url": "https://www.miaopai.com"
            }
        ],
        "buttons": [
            {
                "content": "获取"
            }
        ],
        "iconUrls": [
            {
                "url": "http://a1.att.hudong.com/26/36/20200000013920144735363576977_s.jpg"
            }
        ]
    },
    "header": {
        "logoPicUrl": "https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1534242060206&di=5bb27f4ac1e0fbf244cc622dd0b25f6c&imgtype=0&src=http%3A%2F%2Fpic.qiantucdn.com%2F58pic%2F15%2F83%2F30%2F11v58PICf9Q_1024.jpg",
        "name": "应用信息"
    },
    "ref": {
        "text": "秒拍app,一出好戏",
        "ner": "O",
        "attrMap": {
            "position": "-1"
        }
    }
}
```

#### 对应卡片2：ui样式为ui_tpl_1
![avatar](/chapter1/card_ui/sample/ui_tpl_1_bind.jpg)