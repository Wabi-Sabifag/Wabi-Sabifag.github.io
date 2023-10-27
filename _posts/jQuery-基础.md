---
layout: _posts
title: jQuery 基础
date: 2023-01-05 23:36:04
description:  # 副标题
sticky:             #置顶
toc:                #显示文章TOC（默认为设置中toc的enable配置）
toc_number:         #显示toc_number（默认为设置中toc的number配置）
abbrlink: 997804fe
updated:                #页面更新日期
type: JavaScript   #【必需】标签、分类和友情链接三个页面需要配置
tags: 
- JavaScript
- jQuery
- 基础
categories: 
- JavaScript       #文章分类
- jQuery
- 基础
keywords:   #页面关键词
cover:   'img/26.png'    #文章缩略图（如果没有设置top_img，文章页顶部将显示缩略图，可设为false/图片地址/留空）

comments:         #显示页面评论模块 默认 true
top_img: 'img/26.png'        #页面顶部图片
mathjax:            #显示mathjax（当设置mathjax的per_page： false时，才需要配置，默认 false）
katex:              #显示katex（当设置katex的per_page： false时，才需要配置，默认 false）
aside:              #显示侧边栏 （默认 true）
aplayer:            #在需要的页面加载aplayer的js和css，请参考文章下面的
highlight_shrink:       #配置代码框是否展开（true/false）

copyright: false                      #显示文章版权模块
copyright_author: Wabi-Sabifag          #文章版权模块的文章作者
copyright_author_href:                  #文章版权模块的链接
copyright_url: 'https://Wabi-Sabifag.github.io'
copyright_info: 此文章版权归Wabi-Sabifag所有。如有转载，请注明来自原作者(但万物开源)  #文章版权模块的文字

---

# jQuery

###### 需要引入本地文件 或  https://code.jquery.com 下载文件

## 1.jQuery获取BOM对象

```
javascript
$(document).ready(function(){

// 页面BOM加载完成后执行的代码

})
```

##### 获取对象

```
$("div")[0];
$("div")[0].style.display="none";
```

## 2.jQuery选择器

### 1.基本选择器

```
1.标签选择器    element        $("h2")

2.类选择器    .class        $(".title")

3.ID选择器    #id        $("#title")

4.并集选择器    name1,name2....        $("div,p, .title")

5.交集选择器    element.class(element#id)        $("h2.title")

6.全局选择器    *        $("*")
```

### 2.层次选择器

```
1.后代选择器        ancestor descendant        $("#menu span")

2.子选择器        parent>child        $("#menu>span")

3.相邻元素选择器        prev+next        $("h2+dl")

4.同辈选择器        prev~sibings        $("h2~dl")
```

### 3.属性选择器

```
1.[attribute]        $("[id]")        所有含有 id 属性的

2.[attribute^=value]        $("[href^='en']")        选取href属性 en{% label  开头  pink %} 的元素

3.[attribute$=value]        $("[href$='.jpg']")        选取href属性 .jpg {% label  结尾 pink %}的元素

4.[attribute*=value]        $("[href\*='txt']")        选取href属性{% label  中 pink %}含有 txt 的元素

5.\[selector 1][selector 2]         $("li[id]\[title]=新闻要点")        选取含有id属性和title熟悉为新闻要点的li

6.[alttribute=value]        $("div[class='current']")        获取class等于current的所有div

7.[alttribute!=value]     $("div[class='current']")        获取class不等于current的所有div

8.[alttribute_=value]        $("div[class_='box']")            获取class属性等于或含有box的字符串
```

### 4.基本过滤选择器

#### 1.基本过滤选择器

```
1. :first        $("li:first")
2. :last          $("li:last")
3. :even        $("li:even")              索引为偶数的 li
4. :odd         $("li:odd")                索引为奇数的 li
5. :not          $("li:not(li:eq(3))")   索引不是3的所有 li
6. :focus      $("input:focus")        匹配当前获取焦点的 input 元素
7. :animated       $("div:animated")       匹配当前执行动画的
8. :target      $("div:target")         获取<div id="foo"\>元素
9. :contains(text)     $("li:contains('js')")       获取当前内容中包含 js 的 li
10. :empty     $("li:empty")         获取内容为空的 li
11. :has(selector)        $("li:has('a')")     获取内容中包含 <a> 元素的 所有 <li> 元素
12. :parent     $("li:parent")          选取所有带子元素或文本的 li 元素
13. :hidden    $("li:hidden")         获取所有隐藏的 li 元素
14. :visible     $("li:visible")           获取所有可见的 li 元素
```

#### 2.索引值选择元素的基本过滤选择器

```
1.:eq(index)        $("li:eq(1)")         索引等于1的 li

2.:gt(index)         $("li: gt(1)")         索引大于1的 li

3.:lt(index)          $("li: lt(1)")          索引小于1的 li
```

### 5.子元素选择器

```
1.:nth-child( index / even /odd / 公式 )                索引index默认(1)，子元素显示(公式: 2n  (n默认(0) )

2.:first-child            

3.:last-child

4.:only-child                    当前唯有一个子元素时匹配

5.:nth-last-child()            选择父元素的第n个子元素，计数从最后一个开始到第一个

6.:nth-of-type()                选择同属于同一个父元素下，标签名相同的第n个子元素

7.:first-of-type

8.:last-of-type

9.:only-of-type

10.:nth-last-of-type()     选择同属于同一个父元素下，标签名相同的第n个子元素,计数从最后一个元素到第一个
```

### 6.表单选择器

```
1.:input

2.:text

3.:password

4.:radio

5.:checkbox

6.:submit

7.:reset

8.:image

9.:button

10.:file

11.:hidden

12.:enabled

13.:disabled

14.:checked

15.:selected


注意的地方:   ${"input"}仅能获取表单标签，${":input"}获取页面的所有表单控件，包括 select，textarea 控件。
```

## 3.jQuery 样式操作

### 1.修改样式

#### 1.获取样式

```
<style>
    div{
        width:100px;
        heigth:200px;
        background-color: 'pink';
    }
</style>
<div><a> this div</a></div>
<script>
    console.log($("div).css("width"));  // 100px
</script>
```

#### 2.设置单个样式

```
$("div").css("width","300px");
```

#### 3.设置多个样式

```
$("div").css({
            width:40,
            heigth:2000,
            background:"pink"
        });
```

### 2.类操作

#### 1.准备HYML网页

```
<style>
        div{background-color: gainsboro;}/* //灰色 */
        .a{background-color: beige;}/* //米黄色 */
        .b{background-color: aquamarine;}/* //青色 */
        .c{background-color: pink; }/* //粉色 */

</style>

    <div>添加类名</div>
    <div class="a">删除类名</div>
    <div class="b">切换类名</div>

```

#### 2.addClass()添加类

```
// 添加类名
        $("div").click(function(){
            $(this).addClass("a");
        });
```

#### 3.removeClass()移除类

```
// 移除类
        $("div").click(function(){
            $(this).removeClass("a");
        });
```

#### 4.toggle Class()切换类

```
// 切换类    点赞功能实现
        $("div").click(function(){
            $(this).toggleClass("c")
        })
```

#### 5.功能实例

```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title></title>
        <script src="jquery-3.6.0.js"></script>
    </head>
    <style>
        .current{
            background-color: pink;
            width: 60px;
            height: 30px;
        }
    </style>
    <body>
        <div class="tab">
            <div class="tab_list">
                <ul>
                    <li class="current">商品介绍</li>
                    <li>规格包装</li>
                    <li>售后保障</li>
                    <li>商品评价</li>
                    <li>手机社区</li>
                </ul>
            </div>

            <div class="tab_con">
                <div class="item" style="display: block;">商品介绍模块内容</div>
                <div class="item">规模与包装模块内容</div>
                <div class="item">售后保障模块内容</div>
                <div class="item">商品评价(50000)模块内容</div>
                <div class="item">手机社区模块内容</div>
            </div>
        </div>

    <script>
        $(".tab_list li").click(function(){
            $(this).addClass("current").siblings().removeClass("current");
            var index = $(this).index();
            console.log(index);
            //让内容区域相应的索引号的item显示，其余的item隐藏
            $(".tab_con .item").eq(index).show().siblings().hide();
        });
    </script>

    </body>
</html>
```

#### 6.jQuery类操作 和 className的区别

JavaScript的className会替换掉元素原来的所有类名，可以比喻为串联。
jQuery类操作不影响原来的类名存在，可以理解为并联。

### 3.jQuery动画

#### 1.显示和隐藏效果

```
        元素：show hidde toggle

        <script src="jquery-3.6.0.js"></script>
        <style>
            div{
                width: 150px;height: 300px;background-color: pink;
            }
            p{
                text-align: center;
            }
            p:hover{
                color: red;
            }
        </style>

        <button>显示</button>
        <button>隐藏</button>
        <button>切换</button>
        <div>
            <p>写入导航栏信息</p>
        </div>
        <script>
            $("button").eq(0).click(function(){
                $("div").show(1000,function(){
                    alert("已在显示");
                });
            });

            $("button").eq(1).click(function(){
                $("div").hide(1000,function(){
                    alert("已经隐藏");
                });
            });

            $("button").eq(2).click(function(){
                $("div").toggle(1000);
            });

        </script>

```

#### 2.滑动效果  hover()替代鼠标移入、移出事件

```
        元素：slideDown slideUp slideToggle

        <script src="jquery-3.6.0.js"></script>
        <style>
            ul li{
                display: inline-block;
                width: 60px;
                height: 20px;
                float: left;
                text-align: center;
            }
            ul li:hover{
                background-color: #f3f5f7;
            }
            ul li a:hover{
                color: red;
            }
        </style>

        <ul class="nav">
            <li>
                <a href="#">Weibo</a>
                <ul hidden>
                    <li><a href="">私信</a></li>
                    <li><a href="">评论</a></li>
                    <li><a href="">@我</a></li>
                </ul>
            </li>

            <li>
                <a href="">QQ</a>
                <ul hidden>
                    <li><a href="">添加</a></li>
                    <li><a href="">回复</a></li>
                    <li><a href="">删除</a></li>
                </ul>
            </li>
        </ul>

        <script>
            // 下放
            // $(".nav > li").mouseover(function(){
            //     $(this).children("ul").slideDown(100);
            // });

            //上敛
            // $(".nav > li").mouseout(function(){
            //     $(this).children("ul").slideUp(1000);
            // });

            //可切换
            // $(".nav > li").mouseout(function(){
            //     $(this).children("ul").slideToggle(200);
            // });

            // hover方法
            // $(".nav > li").hover(function(){
            //     $(this).children("ul").slideDown(20);
            //     },function(){
            //         $(this).children("ul").slideUp(20);
            // });

            //简化版本
            $(".nav > li").hover(function(){
                $(this).children("ul").slideToggle(20);
            });
        </script>        

        //  鼠标经过时有抽动的问题  下面的文章可以优化问题
```

#### 3.停止动画

```
        元素： stop

        $("div").stop();    //停止当前动画，继续下一个动画

        $("div").stop(true);    //清楚div元素动画队列中的所有动画

        $("div").stop(true,true);    //停止当前动画，清楚动画队列中的所有动画

        $("div").stop(false,true);    //停止当前动画，继续执行下一个动画


        //优化
            $(".nav > li").hover(function(){
                $(this).children("ul").stop().slideToggle(20);
            });

```

#### 4.淡入淡出

```
        元素：fadeIn fadeOut fadeTo fadeToggle

        <script src="jquery-3.6.0.js"></script>
        <style>
            div{width: 100px;height: 100px;float: left;margin-left: 5px;background-color: pink;}
            .box{width: 425px;height: 105px;padding-top: 5px;border: 1px solid #ccc;}
            .red{background-color: red;}
            .green{background-color: green;}
            .yellow{background-color: yellow;}
            .orange{background-color: orange;}
        </style>

        <div class="box">
            <div class="red"></div>
            <div class="green"></div>
            <div class="yellow"></div>
            <div class="orange"></div>
        </div>

        <script>
            //淡入  显示匹配元素
            $(".box div").fadeIn(1,1);

            // 鼠标经过时灰  移出时恢复
            $(".box div").hover(
            function(){
                $(this).fadeTo(1,0.2);
                },
            function(){
                $(this).fadeTo(1,1);
            });
            </script>
```

#### 5.自定义动画

```
        元素：animate

        <script src="jquery-3.6.0.js"></script>
        <style>
            div{width: 100px;height: 100px;float: left;background-color: pink;position:absolute;}
        </style>

        <button>动起来</button>
        <div >
            <input type="reset" value="重置" hidden>
        </div>
        <script>
            $("button").click(function(){
                $("div").animate({left:500,top:300,opacity:.4,width:500},1000),
                $("input").show()//运行时间
                // $("div").animate({left:8,top:27,opacity:1,width:100},1);
            });        //回到之前位置

            $("input").click(function(){
                $("div").animate({left:8,top:27,opacity:1,width:100},1)
                $("input").hide()
            })
        </script>

```

#### 6.手风琴实列

```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title></title>
        <script src="jquery-3.6.0.js"></script>
        <style type="text/css">
            *{margin: 0;padding: 0;}
            .king{width: 852px;margin: 100px auto;
                    background-color: #f3f6f9;
                    overflow: hidden;padding: 10px;}
            .king ul{list-style: none;}        /* 取消列表样式 */

            .king li{position: relative;float: left;
                    width: 69px;height: 69px;margin-right: 10px;}/* 设置列表样式 */

            /* //设置初始状态 */
            .king li.current{width: 224px;}
            .king li.current .big{display: block;}
            .king li.current .small{display: none;}
            /* //设置大方块样式 */
            .big{
                width: 224px;height: 69px;
                display: none;border-radius: 5px;}
            /* //设置小方块 */
            .small{
                /* position: absolute;top: 0;left: 0; */
                width: 69px;height: 69px;border-radius: 5px;}
            /* //大小方块颜色 */
            .red1{background-color: #ff3333;}
            .orange1{background-color: orange;}
            .yellow1{background-color: yellow;}
            .green1{background-color: green;}
            .blue1{background-color: blue;}
            .pink1{background-color: pink;}
            .purple{background-color: purple;}
            .silver{background-color: silver;}

            .red2{background-color: #ff3333;}
            .orange2{background-color: orange;}
            .yellow2{background-color: yellow;}
            .green2{background-color: green;}
            .blue2{background-color: blue;}
            .pink2{background-color: pink;}
        </style>
    </head>
    <body>
        <div class="king">
            <ul>
                <li class="current">
                    <div class="small  red1"></div>
                    <div class="big  red2"></div>
                </li>

                <li>
                    <div class="small  orange1"></div>
                    <div class="big  orange2"></div>
                </li>

                <li>
                    <div class="small  yellow1"></div>
                    <div class="big  yellow2"></div>
                </li>

                <li>
                    <div class="small  green1"></div>
                    <div class="big  green2"></div>
                </li>

                <li>
                    <div class="small  blue1"></div>
                    <div class="big  blue2"></div>
                </li>

                <li>
                    <div class="small  pink1"></div>
                    <div class="big  pink2"></div>
                </li>

                <li>
                    <div class="small  purple"></div>
                    <div class="big  purple"></div>
                </li>

                <li>
                    <div class="small  silver"></div>
                    <div class="big  silver"></div>
                </li>


            </ul>
        </div>

        <script>
            //鼠标经过
            $(".king li").mouseover(function(){
                $(this).stop().animate({
                    width:224
                }).find(".small").stop().fadeOut().siblings(".big").stop().fadeIn();

                $(this).siblings("li").stop().animate({
                    width:69
                }).find(".small").stop().fadeIn().siblings(".big").stop().fadeOut();
            })
        </script>

    </body>
</html>
```

### 4.jQuery属性操作

#### 1.prop()方法

##### 获取或设置元素固有属性

```
$().prop("")
    1.元素固有属性 (获取和设置)
        <a href="http://localhost" title="主页"></a>
        <script>
            $("a").prop("title"); /* 获取值 */
            $("a").prop("title","首页");     /* 设置值 */ 
        </script>
    2.表单checked属性 (获取)
        <input type="checkbox" checked>

        // 获取表单元素的checked值
            $("input").change(function(){
                console.log($(this).prop("checked"))
            })
```

#### 2.attr()方法

##### 获取或设置元素自定义属性

#### 3.data方法

##### 在指定的元素上存储数据，存储在内存中，不会修改DOM元素结构；页面刷新时存放的数据会移除。

```
$().attr("")
    1.数据获取和设置
  实列：<div>This is div</div>

        <script>
            $("div").data("uname","andy");  /* 设置数据 */
            console.log($("div").data("uname"));    /* 获取数据,设置结果 */
        </script>

  实列：<div index="1" data-index="2">This is div</div>

        <script>
            console.log($("div").data("index"));  //获取自定义的数值：2
        </script>

    2.全选功能
        prop()接受checked作为第一个参数，第二个参数通过 $(this).prop('checked')获取"全选"按钮的选中状态

        $(".checkall").change(function(){
                $(".j-checkbox, .checkall").prop("checked",$(this).prop("checked"));
            });

    3.checked: 选择器查找被选中的表单元素，判断选中数量是否达到所有商品的复选框个数
        $(".j-checkbox").change(function(){
                if($(".j-checkbox:checked").length === $("j-checkbox").length){
                    $(".checkall").prop("checked",true);
                }else{
                    $(".checkall").prop("checked",false);
                }
            });    
```

### 5.jQuery内容操作

#### 1.内容操作方法

    html()    //获取第一个匹配元素的html
    html(content)    //设置第一个匹配元素的html
    
    text()    //获取所有匹配元素包含的文本内容组合起来的文本
    text(content)    //设置所有匹配元素的文本内容
    
    val()    //获取表单元素的value值
    val(value)    //设置表单元素的value值

```
        <div>
            <span>内容</span>
        </div>
        <input type="text" value="请输入内容" name="" id="">

        <script>
            //1.获取设置元素内容 html()
            console.log($("div").html());
            $("div").html("<span>Hello</span>");
            //2.text()
            console.log($("div").text()); //Hello
            $("div").text("<a>12345</a>");
            //3.val()
            console.log($("input").val());
            $("input").val("123")
        </script>
```

### 6.jQuery元素操作

#### 1.遍历元素

```
$().each(function(index,domEle) { });

    1.遍历元素
    <div>1</div> <div>2</div> <div>3</div>
        <script>
            var arr = ["red","green","blue"];
            $("div").each(function(index,domEle){
                console.log(index);        // 
                console.log(domEle);    //整个 html 样式
                if($("div").text()[index]==='2'){
                    $(domEle).css("color",arr[index]);
                }
            });
        </script>


$.each(Object,function(index,element){});

    1.数组和对象的遍历
            // 便利数组
            var arr = ["red","green","blue"];
            $.each(arr,function(index,element){
                console.log(index);            //index
                console.log(element);        //数组值
            });

            //遍历对象
            var obj = {name:"andy",age:18};
            $.each(obj,function(index,element){
                console.log(index);            //key
                console.log(element);        //value
            })
```

#### 2.删除元素

```
        $(function(){
            var li = $("<li>我是后来创建的</li>")
        })
        //添加元素
            //内部元素
            var li = $("<li>后来创建</li>");
            $("ul").append(li);            //内部添加并且放到内部的最后面
            $("ul").prepend(li);        //内部添加并放到内部的最前面
            //外部添加
            var div = $("<div>创建一个 div </div>");
            $(".test").after(div);        //div放入到目标元素的后面
            $(".test").before(div);        //div放入到目标元素的前面

        //删除元素
            empty()                //清空元素内容，删除元素本身
            remove([expr])        //完全删除 ,[expr]用于筛选元素

            $("ul").remove();        //删除匹配的元素
            $("ul").empty();        //删除匹配元素的子节点

            PS: 利用html()元素可以修改元素的内容,如果参数传入空字符,也可以删除子节点元素效果
            $("ul").html("")
```

### 7.jQuery尺寸的位置操作

#### 1.尺寸方法

            width()                 
            height()                
            outerHeight(true)            padding,margin,border
            outerWidth(true)            padding,margin,border
            innerWidth()            padding
            innerHeight()            padding
            outerWidth()            padding border
            outerHeight()            padding border

#### 2.位置方法

```
        <style>
            *{padding: 0;margin: 0;}
            .father{width: 80px;width: 80px;background-color: pink;
                    margin: 10px;overflow: hidden;position: relative;}
            .son{width: 25px;height: 25px;background-color: palevioletred;
                    position: absolute;left: 10px;top: 10px;}
        </style>
        <div class="father">
            <div class="son"></div>
        </div>
```

1. offset()方法
    获取元素位置，返回的是对象，包含left，top表示相对于文档的偏移坐标，和父级元素没有关系。
   
   ```
    //获取元素距离文档顶部距离
    $().offset().top;
    //获取元素距离文档左侧距离
    $().offset().left;
    //设置元素偏移
    $().offset({top:200,left:200})
   ```

2. position()方法
    获取元素距离父级元素的位置
   
   ```
    console.log($(".son").position().top);
    console.log($(".son").position().left);
   ```

3. scrollTop() 和 scrollLeft()  方法

获取或设置元素被卷去的头部距离；  
    获取或设置元素被卷曲的左侧距离

```

 //获取元素距离页面右侧的距离
     $(".container").scrollLeft();

 //设置元素距离页面顶部的距离
     $(document).scrollTop(100);

 //返回顶部动画功能
     $("body,html").animate({scrollTop:0})

```

4. 案例

```

            *{padding: 0;margin: 0;}
            .back{
                position: fixed;width: 50px;height: 50px;background-color: pink;
                right: 30px;bottom: 100px;display: none;
            }
            .container{
                width: 900px;height: 500px;background-color: skyblue;
                margin: 400px auto;
            }

<div class="back">
 </div><div class="container"></div>
 <script>    
 //利用scroll()方法控制“返回顶部”按钮的显示，隐藏
     var boxTop = $(".container").offset().top;
     $(window).scroll(function(){
         if($(document).scrollTop()>=boxTop){
             $(".back").fadeIn();
         }else{
             $(".back").fadeOut();
         }
     });
 //“返回顶部”按钮绑定单击事件
     $(".back").click(function(){
         $("body,html").stop().animate({
             scrollTop:0
         });
     });
 </script>
```

### 8.jQuery事件

#### 1.事件绑定

##### 1.通过事件方法绑定事件

 相对于DOM事件相比省略 “on”。
     并且，jQuery的事件方法允许为一个事件绑定多个事件处理函数，只需要多次调用事件方法，传入不同的函数

###### 1.表单事件

 blur([data],[function])        当前失去焦点时触发

 focus()                        当元素获得焦点时触发

 change()                    当前元素值发生改变时触发

 focusin()                    在父元素上检测子元素获取焦点的情况

 focusout()                    在父元素上检测子元素失去焦点的情况

 select()                    当文本框中的文本被选中时触发

 submit()                    当表单提交时触发

###### 2.键盘事件

 keydown()                    键盘按键按下时触发

 keypress()                    键盘按键按下时触发（有的非基础键位没有）

 keyup()                        键盘按键弹起时触发

###### 3.鼠标事件

 mouseover()                    当鼠标指针移入对象时触发

 mouseout()                    当鼠标指针从元素上离开时触发

 click()                        当单机元素时触发

 dblclick()                    当双击元素时触发

 mousedown()                    当鼠标指针移到元素上方，并按下鼠标按键时触发

 mouseup()                    当在元素上放开鼠标按钮时，会触发

###### 4.浏览事件

 scroll()                    当滚动条发生变化时触发

 resize()                    当调整浏览器窗口大小时会被触发

###### 5.案例
```
<div>事件绑定</div>
     <script>    
         $("div").click(function(){
             $(this).css("background","hotpink");
         });
         $("div").mouseenter(function(){
             $(this).css("background-color","skyblue");
         });
     </script>
```
##### 2.通过on()方法绑定事件

On()方法在匹配元素上绑定多个事件处理函数：
 element.on(events,[selector],fn)
```
     <div class="current">事件绑定</div>
     <script>    
         //一次绑定一个事件
         $("div").on(
             "click",function(){
             $(this).css("background","red")}
         );
         //一次绑定多个事件
         $("div").on({
             mouseenter:function(){
                 $(this).css("background","deepskyblue");
             },
             click:function(){
                 $(this).css("background","yellow");
             },
             mouseleave:function(){
                 $(this).css("background","orange");
             }
         })
         //为不同事件绑定相同事件处理函数
         $("div").on("mouseenter mouseleave",function(){
             $(this).toggleClass("current");
         })
     </script>
```
#### 2.事件委派

        原本要给子元素绑定的事件绑定到父元素上。
            由于事件有冒泡机制，当一个元素出发时间时，可以分区发生事件是父元素还是子元素。

```
        <ul>
            <li>1</li>
            <li>2</li>
        </ul>
        <script>    
        $("ul").on("click","li:first-child",function(){
            alert("单击li")
        });
        </script>
```

##### 新创建的li也可以继承任务触发事件

```
        <ul>
            <li>1</li>
            <li>2</li>
        </ul>
        <script>    
        $("ul").on("click","li",function(){
            alert("单击li")
        });
        var li = $("<li>create a li </li>")
        $("ul").append(li);
        </script>

```

##### bind(),live(),delegate()也可以实现事件绑定和委派，但建议用新版本的 on()来代替

#### 5.事件解绑

```
    <ul>
            <li>1</li>
            <li>2</li>
        </ul>
        <script>    
        var sum=0;
            $("ul").on({
                click:function(){
                    console.log(sum++);},
                mouseover:function(){
                    console.log("鼠标经过我");}
            });
            //事件解绑
            $("div").off();
        </script>    
```

##### one()方法
  元素只触发一次

```
        $("p").one("click",function(){
                alert("被单击了");
            });
```

#### 6.触发事件

##### 1.调用事件方法

```
//绑定事件
$("div").click(function(){
    alert("hello");
});
//触发
$("div").click();
```

##### 2.通过 trigger()方法触发事件

```
//绑定事件
$("div").click(function(){
    alert("hello");
});
//触发
$("div").trigger("click");       //调用 trigger()方法，参数click单击事件
```

##### 3.通过 triggerHandler()方法触发事件 (不会执行元素的默认行为)

```
<input type="text">
<script>
    $("input").on("focus",function(){
        $(this).val("你好吗？");
    });
    $("input").triggerHandler("focus");      //触发事件   文本框不会聚焦选中
    $("input").focus();        // 文本框聚焦选中
</script>
```

#### 7.事件对象
    阻止事件冒泡和默认行为
```
        <a href="173/173.html">链接</a>
        <script>    
            $(document).on("click",function(){
                console.log("单击document");
            });
            $("a").on("click",function(event){
                event.preventDefault();        //阻止事件默认行为      不会跳转页面
                event.stopPropagation();      //阻止事件冒泡        只输出 “ 单击了a”
                console.log("单击了a");
            });
        </script>
```

#### 8.对象成员扩展

        $.extend([deep],target,Object1....)
            // deep  拷贝深度  false/true 
            // target 要拷贝的对象
            // 带拷贝的对象

##### 1.浅拷贝

        当一个对象包含复杂成分数据类型的成员时，引用地址会拷贝给目标对象。 类似于赋值 "="

```
    $.extend(targetObj,obj);
            console.log(targetObj);    //{id:1,msg:{age:18},name:"andy"}
            targetObj.msg.age = 20;
            console.log(obj.msg.age);  // 20
```

##### 2.深拷贝

```
    $.extend(true,targetObj,obj);
            console.log(targetObj);    //{id:1,msg:{age:18},name:"andy"}
            targetObj.msg.age = 20;            // targetObj.msg 和  obj.msg 对象不同
            console.log(obj.msg.age);  // 18
```

#### 9.获取服务器响应结果 ($.ajax())

```
    <script src="jquery-3.6.0.js"></script>
        <script>
            $.ajax({
                type: 'GET',            
                url: 'server.html',            //请求地址
                data: {id:2,name:'hello'},    
                success: function(msg){        //成功后执行的函数
                    console.log(msg);
                }
            });
        </script>
```

##### Ajax 使用

###### 1.高级应用

    $.get(URL[,data][,fn][,type])        
    
    $.post(URL[,data][,fn][,type])
    
    $.getJSON(URL[,data][,fn])                //通过 http get 载入 JSON 信息
    
    $.getScript(URL[,fn])                    // 载入并执行一个 javaScript文件
    
    对象.load(URL[,data][,fn])                //载入远程HTML文件代码并插入至DOM中

###### 2.底层应用

    $.ajax(URL[,Options])                    //通过HTTP 请求加载远程数据
    
    $.ajaxSetup(Options)                    //设置全局Ajax默认选项

### 9.正则表达式  (/^[a-zA-Z0-9_-]{n,m}$/)

#### 1.使用

```
var str = '123';
var reg2 = /abc/;                //字面量方式
var reg1 = new RegExp(/123/);    //RegExp构造函数方式

console.log(reg1.test(str));       //匹配结果  true
console.log(reg2.test(str));    //匹配结果  false

//通用正则表达式
var reg = /^[a-zA-Z0-9_-]{n,m}$/;
```

#### 2.模式修饰符

##### 语法格式： /表达式/[switch]
模式符            说明
    g                用于在目标字符串中实现全局匹配
    i                忽略大小写
    m                实现多行匹配
    u                以Unicode编码执行正则表达式
    y                黏性匹配，仅匹配目标字符中此正则表达式的lastIndex属性指示的索引


#### 3.特殊字符

        一个正则表达式有简单和特殊字符组合。如 /ab*c/  ,特殊字符被称为元字符，是具有特殊意义的专用符号。
            有 ^ , . , $ , * 等。

##### (1)边界符

    原来提示字符所处的位置

```
边界符
    ^        匹配行首文本
    $        匹配行尾文本
```

##### (2)预定义类  . \

###### 1.常见模式的简写方式

```
预定义字符            含义                                    其他写法
        .            匹配除 \n 之外的任何单位字符                
        \d            匹配 0-9 任意一个数字                        [0-9]
        \D            匹配 0-9 之外的字符                            [^0-9]
        \w            匹配 任意的字母，数字和下划线                 [a-zA-Z0-9_]
        \W            匹配 特殊字符                                [^a-zA-Z0-9_]
        \s            匹配 空格(换行，制表，空格)                     [\t\r\n\v\f]
        \S            匹配 非空格                                    [^\t\r\n\v\f]

        \f            匹配 换页符(form-feed)            
        \b            匹配 单词分界符    (例："\bg", "best grade",输出"g")     
        \B            匹配非单词分界符 (例： "\Bade", 输出"ade")
        \t            匹配 水平制表符(tab)
        \n            匹配 换行符(linefeed)
        \xhh        匹配 ISO-8859-1值为 hh (2个16进制数字)的字符 (例： "\x61"  表示 "a")
        \r            匹配 回车符 
        \v            匹配 垂直制表符(vertical tab)
        \uhhhh        匹配 Unicode 值为 hhhh (4个16进制数字)的字符 (例： "\u597d"  表示 "好")
```

###### 2.转译特殊字符

正则表达式中使用 "\" 转译特殊字符。
    选择符 "|" 为 "或" ， 多条件查询。
        str 的 "\"  需要 "\\" 去匹配。 

```
var str = '^abc\\1.23*edf$';
var reg = /\.|\$|\*|\^|\\/gi;
str.match(reg);                
        // 输出结果： (5)[ "^", "\" , "." , "*" , "$" ]
```

##### (3)字符类 []

当有字符匹配 字符类中的字符，则匹配成功。

```
pattern(模式)        含义
    [ab]                    匹配字符类中的任意一个字符
    [^ab]
    [A-Z]
    [^a-z]
    [a-zA-Z0-9]
    [\4e00-\u9fa5]            匹配任意一个中文字符

    例：
        var reg = /[abc]/;
        console.log(reg.test('red'));         // false
```

##### (4)取反符  ^[]

字符类和元字符一起使用，被称为 取反符

```
var reg = /^[^a-z]$/;
console.log(rg.test('a'));        //  false
console.log(rg.test('A'));        //  true
```

#### 4.量词符与括号字符

##### 1.量词符        ? 、+ 、* 、{}

    设置某个模式出现的次数，通过量词（ ? 、+ 、* 、{} ）

字符                说明                                示列                结果
    ?                    匹配 ? 前面的字符零次或一次            hi?t                可以匹配 ht 和 hit
    +                    匹配 + 前面的字符一次或多次            bre+ad                匹配范围 bread 到 bre...ad
    *                    匹配 * 前的字符零次或多次            ro*se                可以匹配 res 到 ro...se
    {n}                    匹配 {}    前面的字符n次                hit{2}er            匹配 hitter
    {n,}                匹配 {} 前面的字符最少n次            hit{2}er            
    {n,m}                匹配 {} 前面的字符最少n次，最多m次     fe{0,2}l


##### 2.括号字符    ()

###### 1.改变限定符的作用范围

```
//作用范围
    catch | er            catch er
//作用范围
    cat ( ch | er )        catch cater
```

###### 2.分组

当小括号后面有量词符，表示对整个组进行操作

```
//作用范围
    abc(2)                abcc
//作用范围
    a(bc){2}            abcbc
```

###### 3.捕获和非捕获

1. match()捕获
   
   ```
   var reg = '1234'.match(/(\d)(\d)(\d)(\d)/);
   console.log(reg);
   ```

2. replace()捕获  (String对象 利用$n 方式捕获)
   
   ```
       颠倒字符串顺序
       var str = 'Regular' Capture';
       var reg = /(\w+)\s(\w+)/gi;
       var newstr = str.replace(reg,'$2 $1');
       console.log(newstr);        //顺序调换
   ```

3. (?:x)非捕获    (不存入系统缓存)
   例：
   
   ```
       //非捕获
       var reg = /(?:J)(?:S)/;
       var res = 'JS'.replace(reg,'$2 $1');
           //res      输出为        '$2 $1'
   
       //捕获
       var reg = /(J)(S)/;
       var res = 'JS'.replaxe(reg,'$2 $1');
           //res     输出为        'S J'
   ```
   
###### 4.贪婪与懒惰匹配
   
   解释：当点字符(.)和量词符连用时，可匹配指定数量范围的任意字符。
```
var str = 'webWEBWebwEB';

var reg1 = /w.*b/gi;            //贪婪
console.log(reg1.exec(str));    // 结果 webWEBWebwEB

var reg2 = /w.*?b/gi;            //懒惰
console.log(reg2.exec(str));    // 结果 web
```
###### 5.反向应用
解释：在正则表达式中获取存放在缓存区内子表达式的捕获内容。
用法：用 "\n" 的方式引用。( "\1" 表示第1个子表达式的捕获内容)
```
var str = '13335 12345 56668';
var reg = /(\d)\1\1/gi;            // \d 匹配 一个0-9的数字，添加"()"可以反向引用获取捕获的内容。 
var match = str.match(reg);
console.log(match);              //结果  (2)["333","666"]
```
###### 6.零宽断言
解释：零宽度的子表达式匹配。
用途：查找子表达式匹配的内容之前或之后是否有特定的字符集。
用法：正向预查和反向预查。
        正向预查：匹配含有或不含有捕获内容之前的数据，匹配的结果中不含捕获内容。
        反向预查：略(暂时)
字符            说明                                    实例
    x(?=y)            仅当 x 后面紧跟着 y 时，才匹配 x        Countr(?=y|ies)  匹配 Country Countries Countr
    x(?!y)            仅当 x 后面不紧跟着 y 时，才匹配 x        Countr(?!y|ies)  仅匹配 Countr

#### 5.正则表达式优先级
符号                        说明
    \                            转义符
    (),(?:),(?=),[]                圆括号和中括号
    *,+,?,{n},{n,},{n,m}        限定符
    ^,$,\ (元字符和字符)         定位符
    |                            "或" 操作

#### 6.String类中的方法
1. match()方法
用途：
    1. 在字符串内检索指定的值
    2. 在目标字符串中根据正则匹配出所有符合要求的内容，匹配成功或将其保存到数组中，匹配失败返回null。
```
var str = "It`s is the shorthand of it is";
var reg1 = /it/gi;
str.match(reg1);        //匹配结果： (2)["It","it"]

var reg2 = /^it/gi;
str.match(reg2);        //匹配结果： ["It"]

var reg3 = /s/gi;
str.match(reg3);        //匹配结果： (4)["s","s","s","s"]

var reg4 = /s$/gi;
str.match(reg4);        //匹配结果： ["s"]
```
2. search()方法
用途：返回指定模式的子串在字符串首出现的位置。
```
var  str = '123*abc.456';
console.log(str.search('.*));        //输出：0
console.log(str.search(/[\.\*]/));  //输出：3
```

非正则表达
new EwgExp(参数)   返回任意字符在字符串str首次出现的位置

3. split()方法
用途：根据指定的分隔符将一个字符串分割成字符串数组，不包括分割符。当分隔符不止一个时，定义正则对象完成字符串的分割操作
1. 按照规则分割
```
"@"和"."两种分隔符进行分割操作
var str = 'test@123.com";
var reg = /[@\.]/;
var split_res = str.split(reg);
console.log(split_res);                // 输出结果：(3)["test","123","com"]
```
2. 指定分割次数 
```
var str = 'We  are a family';
var reg =/\s/;
var split_res = str.split(reg,2);
console.log(split_res);                //输出结果：(2)["We","are"]
    当指定的次数小于实际字符串的次数时，最后返回结果会忽略其他的分割结果
```
4. rplace()方法
用途：替换字符串
```
var str = 'Regular Capture';
var reg = /(\w+)\s(\w+)/gi;
var newstr = str.replace(reg,'$2 $1');
console.log(newstr);        //    Capture Regular
```

