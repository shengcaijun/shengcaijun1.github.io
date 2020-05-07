---
layout: post
title: 一份不完美的疫情地图
tags: [singleton,pattern]
---
#### 说明

大部分东西都能调库，还有接口爬虫组合接口之类的都是现成的，不是我写的，我做的就是把这些东西组合起来而已。

确实不算做的，只能算二次开发。

#### 问题

时间很紧迫，大半部分的软件和语言也基本没学过。所以做这个项目的时候压力非常大。因为一开始的错误决定：先做项目再找人，导致根本找不到人做视频。因此中间耽误了一段时间去自学视频了，进度如此之缓慢最终还只是做了个半成品。
<!--more-->
现在完成了一个世界地图，还需要将中国地图的页面拼接起来。(大概率是放弃了）

-Mapbox的崩溃频率可以以秒计了，需要换个稳定的软体。

-有些软件不支持中文，需要找语言包。

-部分国家数据找不到，无法细化感染地区。

-感谢家里的垃圾WiFi，之前还愁流量用不完会过期，昨天刚充了200话费。

#### 技术栈

vue 全家桶

python3

javascript

nj

flask

pyecharts

requests

mapv

Openlayers

leaflet

Mapbox

Echarts

#### 后期采用
Cesium

AE
#### 开发环境

node-10

win-10

ruby-devkit-2.5.1-2

#### 运行

 ```bash
$ pip install -r requirements.txt  -i https://pypi.tuna.tsinghua.edu.cn/simple
$ python app.py
```

 1. 功能开发
都在 `src/views/` 目录下。

 2. 前端接口
都统一在 `src/api/` 目录下管理，建议一个功能模块里的接口都放在同一个接口文件里。
使用方式参考 `situation` 模块。

 3. 状态管理
都统一在 `src/store/` 目录下，建议一个功能模块的状态放在 `src/store/modules/` 的独立文件里。然后在 `src/store/index.js` 里引入。




#### Docker 运行

```bash
$ docker build -t crawler .
# 后台自动重启运行
$ docker run -it -d --restart=always --name my-crawler crawler
```

#### 区域部署

1. 所有省份地图在`/static/vendor/map/`目录下,按需在index.html中的末尾找到相应位置引入相应地图

2. 修改 templates/index.html文件
适当位置复制以下模板内容,修改下面4个`id`中的`xxx`,以省份的小写拼音命名如 ` shenyang `

```html
 <!-- body xxx --> 
<div class="card-body">
    <div class="row">
        <div class="col-xl-3">
            <ul class="list-unstyled mt-1" id="xxx_overview">
            </ul>

            <ul class="list-unstyled base-timeline" id="xxx_news">
            </ul>
        </div>
        <div class="col-xl-4">
            <div id="xxx_map" class="chart-container" style="width:360px; height:640px;">
            </div>
        </div>
        <div class="col-xl-5">
            <div id="xxx_bar" class="chart-container" style="width:355px; height:640px;" >
            </div>
        </div>
    </div>
</div>
<div>
    <hr />
</div>

```

3. 修改 static/js/update.js 文件

适当位置增加以下模板内容,仿写,`xxx` 为 上一步设置的名称,同样也建议按照省份拼音命名如 `hubei`

```javascript
$(
    function () {
        
        update_china("中国","china");
        update_province("辽宁省","liaoning");
   
        update_province("xxx省","xxx");
         
    }
);

```

#### 开发模板

![vu](https://github.com/Albert-Lucif4/world-map/blob/master/docs/images/reference.jpeg?raw=true "vu")

#### Demo[W版]


 [新冠病毒感染状态统计.world dlc][1]  



#### 总结
 等完全搞完再写吧，现在心力憔悴完全没想法
