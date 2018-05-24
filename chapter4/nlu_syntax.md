# 三角兽NLU语法体系
三角兽NLU体系共包括如下几个层次

|name|type|说明|示例|
|:---|:---|:---|:---|
|基础NLP处理|||
| |segmentation|分词|导航 到 五道口 地铁 站|
| |postag|词性标注|导航:v|
| |ner|命名实体识别|五道口地铁站:n:LOC|
| |dependency parser|依存句法分析|五道口地铁站:n:LOC-->MOD-->商场:n:O|
|NLU抽取||||
| |domain抽取|领域分类|domain=LBS|
| |intent抽取|意图分类|intent=导航POI|
| |slot抽取|槽位抽取|central_poi=五道口地铁站:n:LOC, poi=商场:n:O|




以query

`导航到距离五道口地铁站100米的商场`

为例, 解析的NLU结果如下

<div align="center">
<img src="/assets/nlu/nlu_single_round.jpg" align="center" alt="三角兽nlu体系">
</div>


** 测试graph **

{% graph %}
{
    "title": "1/x * cos(1/x)",
    "grid": true,
    "xAxis": {
        "domain": [0.01, 1]
    },
    "yAxis": {
        "domain": [-100, 100]
    },
    "data": [{
        "fn": "1/x * cos(1/x)",
        "closed": true
    }]
}
{% endgraph %}

** 测试graph **

{% chart %}
{
    "data": {
        "type": "bar",
        "columns": [
            ["data1", 30, 200, 100, 400, 150, 250],
            ["data2", 50, 20, 10, 40, 15, 25]
        ],
        "axes": {
            "data2": "y2"
        }
    },
    "axis": {
        "y2": {
            "show": true
        }
    }
}
{% endchart %}



** 测试视频 **
{% raw %}
<video id="my-video" class="video-js" controls preload="auto" width="100%"
poster="https://zhangjikai.com/resource/poster.jpg" data-setup='{"aspectRatio":"16:9"}'>
  <source src="https://zhangjikai.com/resource/demo.mp4" type='video/mp4' >
  <p class="vjs-no-js">
    To view this video please enable JavaScript, and consider upgrading to a web browser that
    <a href="http://videojs.com/html5-video-support/" target="_blank">supports HTML5 video</a>
  </p>
</video>
{% endraw %}