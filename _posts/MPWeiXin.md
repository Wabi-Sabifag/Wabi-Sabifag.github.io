---
title: MPWeiXin
date: 2023-02-19 12:22:38

description: # 副标题
sticky:             #置顶
toc:                #显示文章TOC（默认为设置中toc的enable配置）
toc_number:         #显示toc_number（默认为设置中toc的number配置）
abbrlink: 997804fe
updated:                #页面更新日期
type: 微信小程序   #【必需】标签、分类和友情链接三个页面需要配置
tags: 
- 微信小程序 #文章标签  
categories: 
- 微信小程序       #文章分类
- 基础
keywords:   #页面关键词
cover:  'img/11.jpg'   #文章缩略图（如果没有设置top_img，文章页顶部将显示缩略图，可设为false/图片地址/留空）
comments:         #显示页面评论模块 默认 true
top_img:  'img/11.jpg'         #页面顶部图片
mathjax:            #显示mathjax（当设置mathjax的per_page： false时，才需要配置，默认 false）
katex:              #显示katex（当设置katex的per_page： false时，才需要配置，默认 false）
aside:              #显示侧边栏 （默认 true）
aplayer:            #在需要的页面加载aplayer的js和css，请参考文章下面的
highlight_shrink:       #配置代码框是否展开（true/false）

copyright: false                          #显示文章版权模块
copyright_author: Wabi-Sabifag          #文章版权模块的文章作者
copyright_author_href:                  #文章版权模块的链接
copyright_url: 'https://Wabi-Sabifag.github.io'
copyright_info: 此文章版权归Wabi-Sabifag所有。如有转载，请注明来自原作者(但万物开源)  #文章版权模块的文字

---
# 1.1 开发工具

## 1.程序调试

### 1.模拟器

客服端真实逻辑表现

### 2.编辑器

对项目进行代码编写和文件的添加，删除及重命名

#### 1.文件的编辑

##### 1.wxml

帮助开发者直接写出相关的标签和标签的属性

##### 2.wxss

##### 3.js

帮助开发者补全所有API和相关的注释解释，并提供代码模板支持

##### 4.json

帮助开发者补全相关的配置，并实时给出提示

##### 5.wxs

### 3.调试器

#### 1.功能模块

##### 1.Console

###### 1.开发者输入

###### 2.调式代码

###### 3.微信小程序的错误输出

##### 2.Sources

用于显示当前项目的脚本文件，同浏览器开发不同，微信小程序框架会对脚本文件进行编译开发者看到的文件是处理之后的脚本文件，开发者的代码都会包裹在define函数中

##### 3.NetWork

用于观察和显示request和socket的请求情况

##### 4.Security

安全认证

##### 5.Mock

数据模拟

##### 6.AppDate

用于显示当前appdata的具体数据，实时的反馈项目数据情况用户可在此编辑数据，数据结果将及时反馈到界面上

##### 7.Audits

性能监控

##### 8.Sensor

###### 1.模拟地理位置

###### 2.模拟移动设备表现(调试重力感应API)

##### 9.Storage

用于显示当前项目使用wx.setStorage 或 wx.setSrorageSync 后的数据存储情况

##### 10.Trace

体验评分

##### 11.Wxml

帮助开发者开发Wxml转化后的界面。可以看到页面结构及结构对应的WXSS属性，可以修改对应的WXSS属性

### 4.云开发

#### 1.云开发控制台

##### 1.运营分析

##### 2.数据库

##### 3.存储

##### 4.云函数

# 1.2 技术框架

## 1.运行机制

马上应用在新版本，使用 wx.getUpdatemannagerAPI 进行处理

### 1.热加载

前台切换到后台

### 2.冷加载

重新加载

## 2.启动配置

### 1.通过全局文件app.json设置启动页面

在app.json，pages数组中的第一个页面就是默认启动页面，只需要调整当前开打的页面在pages数组的顺序

### 2.通过添加编译模式设置启动页面

## 3.目录结构

### 1.page文件夹

1. index.js
2. index.json
3. index.wxml
4. index.wxssPS: 1.小程序每个页面必须有wxml和js 2.文件名称和页面文件夹的名称相同
  
  ### 2.utils文件夹
  
  用于存放全局的js文件例： 公用的方法，对时间的处理
  
      module.exports={
      formatTime:formatTime
      }
  
  对允许外部调用的方法，在用module。exports语句进行声明，才能在其他js文件中用下代码引入
  
      var util = require('../../utils/util.js')
  
  然后可以调用方法。 如： 定义一个ulit函数
  
      function util(){
          console.log('模块被调用')
         }
       module.exports.util = util
  
  然后在 index.js文件中调用这个 util 函数
  
      var common = require('../../util.js')
  
  ### 3.app.js文件夹，app.json文件夹，app.wxss文件夹
  
5. app.js文件用于存放系统方法处理的全局文件
6. app.json文件用于存放系统全局配置文件。 该文件可设置页面路径，网络，调试模式，导航条颜色，字体大小，是否有tabbar。

# 1.3 逻辑层





# 4.1 视图容器组件
## 1.view 视图容器
view 视图容器是 WXML 界面布局的基础组件，它的使用和 HTML 里的 DIV 类似，主要用于界
面的布局。view 视图容器也有自己的属性，如表所示。

属性                类型        默认值      说明

hover               Boolean     false       是否启用单击态

hover-class         String      none        指定按下去的样式类。当 hover-class="none"时，
                                            没有单击态效果

hover-start-time    Number      50          按住后多久出现单击态，单位毫秒

hover-stay-time     Number      400         手指松开后单击态保留时间，单位毫秒

## 2.scroll-view 可滚动视图区域
scroll-view 可滚动视图区域允许视图区域内容横向滚动或者纵向滚动，类似于浏览器的横向滚
动条和垂直滚动条，scroll-view 拥有自己的属性和事件，如表所示。

属性                类型        默认值      说明

scroll-x            boolean     False       允许横向滚动

scroll-y            boolean     False       允许纵向滚动

upper-threshold     number      50          距顶部/左边多远时（单位为 px）,
                                            触发 scrolltoupper 事件

lower-threshold     number      50          距底部/右边多远时（单位为 px）,
                                            触发 scrolltolower 事件

scroll-top          number                  设置竖向滚动条位置

scroll-left         number                  设置横向滚动条位置

scroll-into-view    string                  值应为某子元素 id，则滚动到该元素，
                                            元素顶部对齐滚动区域顶部

scroll-with-anim    atio        boolean     在设置滚动条位置时使用动画过渡

enable-back-to-top  boolean     False       iOS 系统点击顶部状态栏、安卓系统
                                            双击标题栏时，滚动条返回顶部。只支持竖向

enable-flex         boolean      False      启用 flexbox 布局。开启后，如果当前
                                            节点声明了display：flex 就会成为
                                            flex container，并作用于其孩子节点

scroll-anchoring    boolean     False       开启 scroll anchoring 特性，即控制滚动位置
                                            不随内容变化而抖动。仅在 iOS 系统下生效，安
                                            卓系统下可参考 CSS 的 overflow-anchor 属性

refresher-enabled   boolean     False       开启自定义下拉刷新

refresher-threshold number      45          设置自定义下拉刷新阈值

refresher-default-style string  black       设置自定义下拉刷新默认样式，支持设置为black、
                                            white、none。none 表示不使用默认样式

refresher-background    string  #FFF        设置自定义下拉刷新区域背景颜色

refresher-triggered     boolean False       设置当前下拉刷新状态，true 表示下拉刷新已经
                                            被触发，false 表示下拉刷新未被触发

bindscrolltoupper       eventhandle         滚动到顶部/左边会触发 scrolltoupper 事件

bindscrolltolower       eventhandle         滚动到底部/右边会触发 scrolltolower 事件

bindscroll              eventhandle         滚动时触发。event.detail = {scrollLeft,
                                            scrollTop, scrollHeight, scrollWidth, deltaX,
                                            deltaY}

bindrefresherpulling    eventhandle         自定义下拉刷新控件被下拉

bindrefresherrefresh    eventhandle         自定义下拉刷新控件被触发

bindrefresherrestore    eventhandle         自定义下拉刷新控件被复位

bindrefresherabort      eventhandle         自定义下拉刷新控件被中止

### (1) 纵向滑动
允许内容纵向滚动，需要给\<\scroll-view/>一个固定高度
可以绑定滚动到顶部/左边（bindscrolltoupper）
滚动到底部/右边（bindscrolltolower）
滚动时（bindscroll）触发的事件.
也可以滚动到指定的 id 区域（scroll- into-view）。
下面实现纵向滚动，如图所示。
（1）在 wxml 文件里使用 scroll-view 进行布局，设置 scroll-y="true"纵向滚动.
绑定bindscrolltoupper、bindscrolltolower、bindscroll、scroll-into-view、scroll-top 事件，具体代
码如下.
```
<!--index.wxml-->
<view class="section">

  <view class="section_title">scroll-view纵向滚动</view>
  //需要给\<\scroll-view/>一个固定高度
  <scroll-view scroll-y="true" style="height: 200px;" bindscrolltoupper="upper"
    bindscrolltolower="lower"  bindscrolltolower="scroll"
    scroll-into-view="{{toView}}" scroll-top="{{scroll-top}}">
        <view id="green" style="width: 100%;height: 100px;background-color: green;"></view>

        <view id="red" style="width: 100%;height: 100px;background-color: red;"></view>

        <view id="yellow" style="width: 100%;height: 100px;background-color: yellow;"></view>

        <view id="blue" style="width: 100%;height: 100px;background-color: blue;"></view>
    </scroll-view>

    <view class="btn-area">
      <button type="default" style="margin: 10px;" bindtap="tap">
        click me to scroll into view</button>

      <button type="default" style="margin: 10px;" bindtap="tapMove">
        click me to scroll
      </button>
    </view>

</view>

```
（2）在 js 文件里设置颜色的数组，绑定 to View 和 scroll Top 数据值，提供 bindscrolltoupper、
bindscrolltolower、bindscroll、scroll-into-view、scroll-top 事件函数，具体代码如下。
```
// index.js
var order=["red","yellow","blue","green","red"]
Page({
  data:{
    toView: 'red',
    scrollTop: 100
  },
  upper:function(e){
    console.log(e)
  },
  lower:function(e){
    console.log(e)
  },
  scroll:function(e){
    console.log(e)
  },
  tap:function(e){
    for(var i=0;i<order.length;++i){
      if(order[i] === this.data.toView){
        this.setData({
          toView:order[i+1]
        })
        break
      }
    }
  },tapMove:function(e){
    this.setData({
      scrollTop:this.data.scrollTop+10
    })
  }
})

```
这样就可以实现纵向滚动了，可以滚动到指定区域，也可以滚动到指定的位置，同时滚动到顶
部或底部会触发相应的事件，在滚动过程中也可以触发相应的事件。

### (2) 横向滑动
在新闻列表的上方都会有新闻频道供我们选择，可以
向左滑动和向右滑动来查看相应类别的新闻，可以采用 scroll-view 来实现这些新闻频道的横向滚动

在 wxml 文件里使用 scroll-view 进行布局，设置 scroll-x="true"横向滚动，具体代码如下。

## 3.swiper 滑块视图容器
swiper 滑块视图容器用来在指定区域内切换显示内容，常用来制作海报轮播效果和页签内容切
换效果，它的属性如表所示。

属性                      类型              默认值          说明

indicator-dots            boolean           False           是否显示面板指示点

indicator-color           color             rgba(0,0,0,.3)  指示点颜色

indicator-active-color    color             #000000         当前选中的指示点颜色

autoplay                  boolean           False           是否自动切换

current                   number             0              当前所在页面的 index

interval                  number            5000            自动切换时间间隔

duration                  number            500             滑动动画时长

circular                  boolean           False           是否采用衔接滑动

vertical                  boolean           False           滑动方向是否为纵向

previous-margin           string            "0px"           前边距，可用于露出前一项的一小部分，
                                                            有 px 和 rpx 两种单位

next-margin               string            "0px"           后边距，可用于露出后一项的一小部分，
                                                            有 px 和 rpx 两种单位

display-multiple-items    number            1               同时显示的滑块数量

skip-hidden-item-layout   boolean           False           是否跳过未显示的滑块布局。
                                                            设为True 可优化复杂情况下的滑动性能，
                                                            但会丢失隐藏状态的滑块的布局信息

easing-function           string            default         指定 swiper 切换缓动动画类型。
                                                            Default为默认缓动函数、linear为线性动画、
                                                            easeInCubic为缓入动画 、easeOutCubic 为缓出动画、
                                                            easeInOutCubic 为缓入缓出动画

bindchange                eventhandle                       current改变时会触发change事件。event.detail={current: current}

bindtransition            eventhandle                       swiper-item 的位置发生改变时会触发transition事件。
                                                            event. detail = {dx: dx, dy: dy}

bindanimationfinish       eventhandle                       动画结束时会触发 animationfinish 事件。
                                                            event.detail ={dx: dx, dy: dy}

### 1.海报轮播效果                                                          
(1)在 wxml 文件里，采用 swiper 滑块视图容器组件进行海报轮播区域的布局，具体代码如
下：  
```
<view class="haibao">
  <swiper indicator-dots="{{indicatorDots}}" autoplay="{{autoplay}}"
  interval="{{interval}}" duration="{{duration}}">
      <block wx:for="{{imgUrls}}">
        <swiper-item>
          <image src="{{item}}" class="silde-image" style="width: 100%;"/>
        </swiper-item>
      </block>
  </swiper>  
</view>
```
在 js 文件里，提供海报轮播的图片，设置是否自动播放，提供轮播的时长等数据，通过数据绑定的
方式渲染到页面上，具体代码如下。
```
Page({
  indicatorDots:true,
  autoplay:true,
  interval:5000,
  duration:1000,
  imgUrls:[
    "https://api.mofun365.com:8888/images/goods/1555851154057.jpg",
    "https://api.mofun365.com:8888/images/goods/1555851345937.jpg",
    "https://api.mofun365.com:8888/images/goods/1555850845474.jpg",
  ]
})
```
设置 autoplay 等于 true 时就可以自动进行海报轮播，设置 indicatorDots 等于 true，代表显
示面板指示点，同时可以设置 interval 自动切换时长、duration 滑动动画时长

### 2.页签内容切换效果
swiper 滑块视图容器除了可以用来实现海报轮播效果，还可以实现页签切换效果。页签切换效
果常用于多种方式的登录或者多种类别的切换，如图所示

## 4.movable-view 可移动视图容器
movable-view 是一个可移动视图容器，在页面中可以做拖曳滑动。在使用这个组件的时候，
需要先定义可移动区域 movable-area，然后定义直接子节点 movable-view，否则不能移动。
movable-area 必须设置 width 和 height 属性，不设置默认为 10px；movable-view 必须设置
width 和 height 属性，不设置默认为 10px， movable-view 默认为绝对定位，top 和 left 属性.
为 0px。movable-view 可移动视图容器的属性如表所示.

属性                    类型            默认值          说明

direction               string          none            movable-view 的移动方向。属性值有
                                                        all、vertical、horizontal、none

inertia                 boolean         False           movable-view 是否带有惯性

out-of-bounds           boolean         False           超过可移动区域后，movable-view 是否还可以移动

x                       number/string                   定义 x 轴方向的偏移。如果 x 的值不在可移动范围
                                                        内，会自动移动到可移动范围；改变 x 的值会触发动画

y                       number/string                   定义 y 轴方向的偏移。如果 y 的值不在可移动范围内，
                                                        会自动移动到可移动范围；改变 y 的值会触发动画

damping                 number          20              阻尼系数，用于控制 x 或 y 改变时的动画和过界回弹的
                                                        动画，值越大移动越快

friction                number          2               摩擦系数，用于控制惯性滑动的动画，值越大摩擦力越大，滑动
                                                        越快停止；必须大于 0，否则会被设置成默认值

disabled                boolean         False           是否禁用

scale                   boolean         False           是否支持双指缩放，默认缩放手势生效区域是在movable-view内

scale-min               number          0.5             定义缩放倍数最小值

scale-max               number          10              定义缩放倍数最大值

scale-value             number          1               定义缩放倍数，取值范围为 0.5～10

animation               boolean         True            是否使用动画

bindchange              eventhandle                     拖动过程中触发的事件，event.detail = {x: x, y: y, source:
                                                        source}。其中 source 表示产生移动的原因，值可为 touch（拖
                                                        动）、touch-out-of-bounds（超出移动范围）、out-of-bounds
                                                        （超出移动范围后的回弹）、friction（惯性）和空字符串（setData）

movable-view 提供了两个特殊事件：
    htouchmove 事件，指初次手指触摸后的移动为横向移动，
      如果 catch 此事件，则意味着 touchmove 事件也被 catch；
    vtouchmove 事件，指初次手指
      触摸后的移动为纵向移动，如果 catch 此事件，则意味着 touchmove 事件也被 catch。  

（1）在 wxml 文件里，使用 movable-area 和 movable-view 视图容器组件进行布局，具体代码如下。                                                     
```
<!--index.wxml-->
<view class="section">
  <movable-area style="height: 200px;width: 100%;background-color: yellow;">              
                                                                                            // movable-view 的移动方向。
    <movable-view style="height: 50px;width: 50px;background-color: red;" x="{{x}}" y="{{y}}" direction="all"></movable-view>
  </movable-area>
</view>

```
（2）在 js 文件里，提供拖动函数、缩放函数，通过数据绑定的方式渲染到页面上，具体代码如下。
```
<--index.js-->
Page({
  data:{
    x:0,
    y:0
  },
  tap:function(e){
    this.setData({
      x:30,
      y:30
    });
  },
  onChange:function(e){
    console.log(e.detail)
  }
})
```

## 5.cover-view 、cover-image 覆盖原生组件的视图容器
cover-view、cover-image 这两个是覆盖原生组件的视图容器。
比如在使用地图组件时，地图组件本身的功能很有局限，但是想放置一些特殊的内容或图片，这时就需要使用覆盖地图组件的视
图容器。
  (1)cover-view 是指覆盖在原生组件之上的文本视图，可覆盖的原生组件包括 map、video、canvas、
camera，只支持嵌套 cover-view、cover-image。
  (2)cover-image 是指覆盖在原生组件之上的图片视图，可覆盖的原生组件同 cover-view 一样，
支持嵌套 cover-view。

下面使用 cover-view、cover-image 覆盖原生组件的视图容器组件，在 video 视频播放组件上
放置播放、暂停两个图片，同时放置一个时间内容显示区域，如图所示。


（1）在 wxml 文件里使用 cover-view、cover-image 覆盖原生组件的视图容器组件进行布局，
具体代码如下。在线视频地址从图片素材中复制
```
<!--pages/coverViewDemo/coverViewDemo.wxml.wxml-->
<video id="myideo" src="http://wxsnsdy.tc.qq.com/105/20210/snsdyvideodownload?filekey=30280201010421301f0201690402534804102ca905ce620b1241b726bc41dcff44e00204012882540400&bizid=1023&hy=SH&fileparam=302c020101042530230204136ffd93020457e3c4ff02024ef202031e8d7f02030f42400204045a320a0201000400" controls="{{false}}"  event-model="bubble" style="width: 100%;">
  <cover-view class="controls">
    <cover-view class="play" bindtap="play">
      <cover-image class="img" src="/pages/images/play.png"></cover-image>
    </cover-view>

    <cover-view class="pause" bindtap="pause">
      <cover-image class="img" src="/pages/images/pause.png"></cover-image>
    </cover-view>

    <cover-view class="time">00:00</cover-view>

  </cover-view>    
</video>

```

（2）在 wxss 文件里添加样式
```
.controls{
  position: relative;
  top: 50%;
  height: 50px;
  margin-top: -25px;
  display: flex;
}
.play,.pause,.time{
  flex:1;
  height: 100%;
}
.time{
  text-align: center;
  background-color: rgba(0,0,0,.1);
  color: white;
  line-height: 50px;
}
.img{
  width: 40px;
  height: 40px;
  margin: 5px auto;
}
```

（3）在 js 文件里，提供视频播放、暂停函数，初始化视频播放组件，
```
Page({
  onReady(){
    this.videoCtx=wx.createVideoContext('myVideo')
  },
  play(){
    this.videoCtx.play()
  },
  pause(){
    this.videoCtx.pause()
  }
})
```