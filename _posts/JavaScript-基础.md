---
layout: _posts
title: JavaScript 基础
date: 2023-01-02 16:12:58
description:  # 副标题
sticky:             #置顶
toc:                #显示文章TOC（默认为设置中toc的enable配置）
toc_number:         #显示toc_number（默认为设置中toc的number配置）
abbrlink: 997804fe
updated:                #页面更新日期
type: JavaScript   #【必需】标签、分类和友情链接三个页面需要配置
tags: 
- JavaScript
- 基础
# - Python      #文章标签  
# tags: Python
categories: 
- JavaScript       #文章分类
- 基础
keywords:   #页面关键词
cover:    'img/24.png'   #文章缩略图（如果没有设置top_img，文章页顶部将显示缩略图，可设为false/图片地址/留空）

comments:         #显示页面评论模块 默认 true
top_img: 'img/24.png'      #页面顶部图片
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
# 1.文字样式
## CSS文件样式编辑
```
.class #id {
	 font-size: ;/* //字体大小 */
	 font-family: ; /* //字体 */
	 font-weight: ;/* //字体粗细 */
	 font-style: ;/* /字体风格 */
	 font: ;/* 综合设置字体 */
} 

@font-face{
	font-family: ; /* 字体名称 */;
	src: ; /* 字体路径 */
}

/* CSS文本外观属性 */
*{
	color: ;/* 文本颜色 */
	letter-spacing:;/* 字间距 */
	word-spacing:;/* 单词间距 */
	line-height:;/* 行间距 */
	text-transform:;/* 文本转换 */ none 默认;capitalized 首字符大写;uppercase 全部字符转换为大写;lowercase 全部字母转换为小写;
	text-decoration:;/* 文本装饰 */none 默认;underline 下划线;overline 上划线;line-through 删除线;
	text-align:;/* 水平对齐方式 */left  right  center (仅适用于块级元素)
	text-indent:;/* 首行缩进 */
	white-space:;/* 空白符处理 */normal 空白无效化(仅一个空格); pre 预格式化; nowrap 空白无效化(一行,无视字数量);
	text-shadow:;/* 阴影效果 */h-shadow 水平阴影距离; v-shadow 垂直到阴影的距离; blur 模糊半径; color 阴影颜色;
	text-overflow:;/* 表示对象内溢出文本 */ clip 修剪溢出文本,不显示省略标签; ellipsis 用省略标签"..."替代;
	word-wrap:;/* 实现长单词或者URL地址(统一资源定位器)的自动换行 */break-word 内部换行(保持文本在ui设计面板内部);
}

/* CSS复合选择器 */
一,以标签为选择的
1 标签选择器
p{}

2 后代选择器
p strong{}

3 并集选择器(较特殊,各种都可以并集)
h2 h3 p .class{}
```
## 链接伪类控制超链接

```
a:link{
    /* 默认格式 */
}
a:visited{
    /* 被访问之后的样式 */
}
a:hover{
    /* 鼠标指针经过，悬停时超链接的样式 */
}
a:active{
    /* 鼠标点击不放时的样式 */

}
```

# 2.选择器关系

### 一、属性选择器

	1.只要 P 元素 id 属性以 "one" 开头就会被选中
	p[id^="one"]{ }

	2.匹配包含 id 属性,且 id 属性值是 "section" 结尾的 div 元素
	div[id$="section"]{ }

	3.匹配包含 id 属性,且 id 属性值包含 "section" 字符串的任意 div 元素
	div[id*="section"]{ }

### 二、关系选择器

	1.子选择器      /* 当子元素只做某个父元素的子类时生效 */
	h1>strong{ }

	2.兄弟选择器
	/* 在某个元素选择器后触发 */
		(1)临近选择器       /*  在位于同一父级元素; 第二个元素 紧跟着 第一个元素 */
		p+h2{ }

		(2)普通兄弟选择器    /*  在位于同一父级元素; 第二个元素 不必跟着 第一个元素 */
		p~h2{ }
	
### 三、结构化伪类选择器
	
	1.:root选择器     /* 用于匹配文档根标签 ，全局设定 */
	:root{ } == *{ }

	2.:not选择器    /* 排除 父结构元素 下 子结构元素 该功能的继承效果 */
	body *:not(h2){ }

	3.:only-child选择器      /* 用于匹配 父元素 有且仅有一个 子元素 才生效的 */
	strong:only-child{ }

	4.:first-child 和 :last-child 选择器      /* 和 :only-child选择器 条件类似 */
	p:first-child{ } / p:last-child{ } 
	
	5.:nth-child(n) 和 :nth-last-child(n) 选择器    /* 两者的关系是 顺数 或 倒数 */
	  
	6.:nth-of-type(n) 和 :nth-last-of-type(n) 选择器     /* 匹配 标签本身 的顺序 */
	h2:nth-of-type(odd){ }   匹配 h2 的奇数行
	h2:nth-of-type(even){ }  匹配 h2 的偶数行
	p:nth-last-of-type(2){ } 匹配 p 倒数的第二数行
	
	7.:empty选择器     /* 匹配 没有 子元素 或 文本内容为空 所有元素 */
	:empty{ }
	
### 四、伪元素选择器     /* 这对已经定义好的伪元素使用的选择器 */
	1.:before伪元素选择器
	  必须配合 content 属性指定要插入的内容
	p:before{content: " ";}

	2.:after为元素选择器
	p:after{content: " ";}


# 3.表格 表单


### 网页底部信息版本
```
<caption> </caption>    定义表格的标题
<table border="" (表格边框)> 
    <tr>
        <td>
        </td>
    </tr>
</table>
```

### 创建表格：
#### 一、table标签属性
    1.border：表格边框  
        border-collapse：collapse;  边框合并。 
            1.HTML设置cellspacing属性无效 2.tr 无border属性

    2.cellspacing：单元格间距离
    3.cellpadding：单元格内容与单元格边缘距离
    4.withd：宽
    5.height：高
    6.align：left，center，right 表格在网页的对齐方式
    7.bgcolor：背景颜色
    8.background：url（）设置表格背景图像

#### 二、tr标签属性
    1.height：高
    2.align：left，center，right  一行内容水平对齐方向
    3.valign： 一行内容的垂直对齐方向
    4.bgcolor：背景行颜色
    5.background：url() 设置行背景图片

#### 三、td标签属性
    1.height：高
    2.align：left，center，right  一行内容水平对齐方向
    3.valign： 一行内容的垂直对齐方向
    4.bgcolor：背景行颜色
    5.background：url() 设置行背景图片
    6.colspan：单元格横跨列数
    7.rowspan：单元格纵跨列数

#### 四、th 和 td 相同
    但用于定义表头单元格，默认加粗，居中显示

#### 五、表格结构
    1.thead：定义表格头部，包含网页logo和导航头部信息
    2.tfoot：定义表格页脚，位于 thead 标签后，包含网页底部的企业信息
    3.tbody：定义表格的主体，位于 tfoot 标签后，包含其他内容

```
        <form action="url地址" method="提交方式" name="调单名称"></form>
```
### 创建表单：
#### 一、action属性
    1.当提交表单时，数据会传送到 名为 ” “的页面
    2.可以是相对路径或者绝对路径。
      列如： action=mailto：htmlcss@163.com

#### 二、method属性
    <form action="form_action.asp" method="get / post" name="调单名称">
    用于指明表单处理服务器数据的方法
    1.get：保密差，数据量有限制
    2.post：保密好，数据量无限制

#### 三、name属性
    用于指定表单名称，表单控件中具有name属性的元素会将用户填写的内容交给服务器

#### 四、autocomplete属性
    指定表单是否有自动完成功，将表单控件输入的内容记录下来
    1.on
    2.off

#### 五、novalidate属性
    指定在提交表单时取消对表单进行有效的检查
    1.novalidate="novalidate”

### < input >表单控件
 
#### 一、input控件
  (1)type属性
    1.text
    2.password
    3.radio：单选按钮
    4.checkbox：复选框
    5.button：普通按钮
    6.submit：提交按钮
    7.reset：重置按钮
    8.image：图像形式的提交按钮
    9.hidden：隐藏域
    10.file：文件域
  (2)name属性：控件名称
  (3)value属性:默认文本值
  (4)size属性：input控件在页面的显示宽度
  (5)readonly属性：只读无法修改
  (6)disabled属性：禁用该控件
  (7)checked属性：定义选择控件默认被选中
  (8)maxlength属性：控件允许输入的最多字符

  (9)email类型
  ```
        <input type="email"/>
            专门用于验证Email输入框的内容的邮件格式
  ```
  (10)url类型
  ```
        <input type="url"/>
            专门用于验证输入框的内容是url地址格式的文本
  ```
  (11)tel类型 
  ```
        <input type="tel"/>
            专门用于提供输入电话号码的文本框，配合 pattern 属性使用
  ```
  (12)search类型
  ```
        <input type="search"/>
            专门用于输入搜素关键词的文本框，在用户输入内容后，右侧会附带一个删除图标
  ```
  (13)color类型
  ```
        <input type="color"/>
            用于设置颜色的文本框，通过 value属性值 改变默认颜色
  ``` 
  (14)number类型
  ```   
    < input type="number"/>
        专门用于验证文本框内容是否是数字或在限定范围内
        1.value：
        2.max：
        3.min：
        4.step：输入域合法的间隔的升降值，默认值1
  ```
  (15)range类型
  ```
        <input type="range"/>
        用于提供一定范围内的输入范围
  ```
  (16)Date pickers类型
  ```
       <input type=Date，month，week />
        1.Date
        2.month
        3.week
        4.time
        5.datetime
        6.datetime-local
  ```
  (17)autofocus属性
        用于指定页面加载后是否自动获取焦点
        1.true
        2.off
  (18)form属性
        1.可以在form表外进行操作
        2.在指定form属性为表单的id，所以该输入框任然属于表单的一部分
  (19)list属性
     ```
        例如：
            <from action="#" method="post">
            请输入网址：<input  type="url" list="url_list" name="weburl" />
            <datalist id="url_list">
                <option lable="百度" value="htpp://www.baidu.com"></option>
            </datalist>
            <input type="submit" value="提交" />
            </form>
    ```
  (20)multiple属性
        适用Email类型和file类型，可以多个内容段
  (21)placeholder属性
        输入框提供相关提示
  (22)required属性
        用于判断用户是否在表单输入框中输入内容，表单内容为空时，不允许用户提交表单
    ```
        <input required="required"/>  
    ```
        

### 二、textarea控件
    （1）name属性
    （2）readonly属性：只读无法修改
    （3）disabled属性：禁用该控件

### 三、select控件
#### （1）select属性
        1.size：下拉菜单可见选项数
        2.multiple：定义 multiple="multiple" 具有多选择功能

#### （2）option属性
        1.selected：定义 selected="selected" 默认选定

####   （3）optgroup属性  
 / 选项分组的方法和效果 /
例如：
```
            <from action="#" method="post">
                <select>
                    <optgroup lable="北京">
                        <option> </option>
                        <option> </option>
                    </optgroup>
                     <optgroup lable="上海">
                        <option> </option>
                        <option> </option>
                    </optgroup>
                </select>
            </form>
```
#### （4）keygen

####   （5）datalist属性
        1.自行输入内容，指定输入框绑定的datalist元素
例如：
```
            <from action="#" method="post">
            请输入用户名：<input  type="text" list="namelist" />
            <datalist id="namelist">
                <option>admin</option>
            </datalist>
            <input type="submit" value="提交" />
            </form>
```


# 4.布局


### 一、浮动
    选择器{float：left，right，none}

### 二、清除浮动
    选择器{clear:left,right，none，both}
    选择器{overflow：hidden}    消除子标签对父标签的影响
    选择器:after{必须设置 height:0 样式；必须设置 content:"".}

### 三、定位属性
#### (1)定位模式
        选择器{position:属性值}
        1.static:自动定位
        2.relative:相对定位，相对于自身在同级文档流的移动
        3.absolute：绝对定位，相对于父标签进行定位
        4，fixed：固定定位，相对于浏览器进行定位
#### (2)边偏移
        1.top
        2.bottom
        3.left
        4.right 
    
### 四、文本内容溢出
    选择器{overflow：属性值}
    1.visible：内容不会剪切，会呈现在标签框外
    2.hidden：溢出内容被剪切，且不可见
    3.auto：在需要时产生滚动条，自适应
    4.scroll：溢出内容会被修剪，浏览器会始终显示滚动条

### 五、标签顺序
    选择器{z-index：0}  数字越大优先级越高



# 5.过度、变形和动画


### 一、过度
####    1、transition-property属性
        功能:渐隐，渐显，速度变化（设置应用过度的CSS属性）
        (1)none
        (2)all
        (3)property：定义应用过渡效果  // transition-property:background-color;

        版本私有前缀：
        -webkit-transition-property： 谷歌
        -moz-transition-property：  火狐
        -o-transition-property：    IE
        -ms-transition-property：   欧朋

####    2、transition-duration属性
        定义过渡效果持续时间
        transition-duration：5s；

####    3、transition-timing-function属性
        规定过渡效果的速度曲线
        (1)liner:相同速度开始至结束的过渡效果，等同于 cubic-bezier(0,0,1,1);
        (2)ease:以慢速开始，然后加快，最后慢慢结束的过渡效果，等同于 cubic-bezier(0。25,0.1,0.25,1);
        (3)ease-in:以慢速开始，然后逐渐加快的过渡效果，等同于 cubic-bezier(0.42,0,1,1);
        (4)ease-out:以慢速结束的过渡效果，等同于 cubic-bezier(0,0,0.58,1);
        (5)ease-in-out:以慢速开始和结束的过渡效果，等同于 cubic-bezier(0.42,0,0.58,1);
        (6)cubic-bezier(n,n,n,n):用于定义加速或者减速的贝塞尔曲线的形状（0~1值）。

####    4、transition-delay属性
        规定过渡效果的开始时间
        (1)transition-delay: time;

####    5、transition属性
        复合属性
        transition：border-radius 5s ease-in-out 2s,
                    border-radius 5s ease-in-out 2s

### 二、变形
####    1、transform属性
        功能:平移、缩放、倾斜、旋转
        (1)translate(): 移动元素，基于X，Y重新定位元素
        (2)scale(): 缩放元素对象，使元素对象尺寸变化
        (3)skew(): 倾斜元素对象，取值为度数值
        (4)rotate(): 旋转元素对象，取值为度数值 

####    2、2D变形
        (1)平移
            transform:translate(X,Y);
        (2)缩放
            transform:scale(X,Y);
            第一值:负数(翻转)，0~1(缩小)，1(增大)
            第二值:可以省略
        (3)倾斜
            transform:skew(X,Y);
            单位值:deg，取值正负值，
            第二值:默认0
        (4)旋转
            transform:rotate(angle);
            单位值:deg，取值正值(顺时)，负值(逆时)
        (5)更爱变换的中心
            transform:X,Y,Z

####    3、3D变形
        (1)transform:rotateX(a);
        (2)transform:rotateY(a);
        (3)transform:rotated3d(1,1,0,45deg);

####    4、perspective属性
        为呈现良好视距，3D视距旋转

        (1)transform-style: 用于保存元素的3D空间
            flat：子元素将不保留3D位置
            preserve-3d：子元素将保留3D位置
        (2)backface-visibility: 定义元素在屏幕时是否可见
            visible:背面是可见
            hidden:背面是不可见的

### 三、动画
####    1、@keyframes 规则
        (1)animationname: 表示当前动画的名称，他将作为引用的唯一标识，不为空
        (2)keyframes-selector: 关键帧选择器，值可以是百分比，from（0%）或to（100%）
        (3)css-styles: 定义执行到当前关键帧时对应的动画状态，有css样式属性进行定义，可多个属性，不能为空
        
        语法格式:
        ```
            @keyframes animationname {
                keyframes-selector {
                    css-styles;
                }
            }
        ```
        例如：
        ```
            淡出动画
            @keyframes appear {
                0%{ opacity:0; }
                100%{ opacity:1; }
            }

            @keyframes appear {
                from{ opacity:0; }
                to{ opacity:1; }
            }

            @keyframes appear {
                from to{ opacity:0; }
                20% 80%{ opacity:1; }
            }
        ```
####    2、animation-name属性
        定义应用的动画名称
        animationname-name: name;

####    3、animation-duration属性
        定义整个动画效果完成效果所需要的时间
        animation-duration:time;

####    4、animation-timing-function属性
        规定动画的速度曲线

####   5、animation-delay属性
        定义执行动画效果延迟的时间

####    6、animation-iteration-count属性
        定义动画的播放次数

####    7、animation-deraction属性
        定义当前动画播放的方向
        (1)normal
        (2)alternate:奇数正常，偶数逆向播放
    
####    8、animation属性
         复合属性
            animation: mymove 5s linear 2s 3 alternate;


# 6.少见的标签功能



####    1.nav标签
        定义导航链接
####    2.footer标签
        定义一个页面或者区域的底部
####   3.article标签
        定义一篇日志，一条新闻或用户评论（代表文档、页面或者应用程序中与上下文不相关的独立部分）
####    4.section标签
        小标题，
####   5.aside标签
        定义当前页面或者文章的附属信息部分

####    6.video  //可以使用网站资源
```
      <video src="video.mp4" controls="controls"></video>
```
        1.autoplay:页面加载完后自动播放视频
        2.loop：视频结束时重现开始播放
        3.preload：  // 在页面加载时进行加载
            (1)auto:
            (2)meta:
            (3)none:
        4.poster：
            (1)URL:当视频缓冲不足时，该属性值链接一个图像，并将图像按一定比例显示出来
        5.muted：嵌入的视频静音播放

    例如：
```
        <video controls="controls">
            <source src="video.mp4" type="video/mp4">
            <source src="video.ogg" type="video/ogg">
            <source src="video.webm" type="video/webm">
        </video>
```
####    7.audio
```
     <audio src="audio.mp3" controls="controls"></audio>
```
        1.autoplay:页面加载完后自动播放音频
        2.loop：音频结束时重现开始播放
        3.preload：  // 在页面加载时进行加载
            (1)auto:
            (2)meta:
            (3)none:

    例如：
```
        <audio controls="controls">
            <source src="audio.mp3" type="audio/mp3">
            <source src="audio.ogg" type="audio/ogg">
            <source src="audio.wav" type="audio/wav">
        </audio>
```


# 7.画布


### 一、画布使用
####    1.创建画布
```
        < canvas id="cavs" width=" " height=" "> </canvas>
```
####    2.获取画布
```
        var canvas = ducument.getElementById('cavs');
```
####    3.准备画笔
```
        canvas.getContext('2d'); 
        // 如果三维画制造图片--webgl
```

### 二、绘制线
####    1.初始位置
```
        var cas = ducument.getElementById('cas');
        var context cas.getContext('2d');
        context.moveTo(100,100);
```
####    2.连接端点
```
        context.lineTo(100,100);
```
####    3.描边
```
        context.stroke();
        连接初始位置和连线端点
```
####    4.绘制圆
```
        arc(X,Y,Z,开始角度,结束角度,方向)
```        
        例如:
```
            context.arc(150,25,100,0.05*Math.PI,0.95*Math.PI);
```        
####    5.线的样式
        (1)宽度:context.lineWidth='10';
        (2)描边颜色:context.strokeStyle='red / #f00';
        (3)断电形状:lineCap='属性值'
            [1]butt:默认直线方形边缘
            [2]round:显示圆形端点
            [3]square:显示方形端点

### 三、线的路径
####    1.重置路径
```
        context.beginPath();
```
####    2.闭合路径
```
        context.colsePath();    
```    
####    3.填充路径
```
        context.fill();
```


# 8.DOM文档对象模型


### 一、
####    (1)获取元素
        1. ducument.getElementById('自定义名')
        2. ducument.getElementsByTagName('标签名') //集合 不能用push()等方法
        3. element.getElementsByTagName('标签名')  
        4.document.getElementsByName('Name名')
        5.document.getElementsByClassName('ClassName名')
        6.document.querySelector('.box / #box / li')
    
####    (2)document 对象属性
        1.document.body
        2.document.title
        3.document.documentElement
        4.document.forms
        5.document.images

####    (3)操作元素内容
        1.element.innerHTML
        2.element.innerText
        3,element.textContent

####    (4)操作元素属性
        1.img元素
            img.src / img.title 
        2.表单input元素
        ```
            <button>按钮</button>
            <input type="text" value="输出内容">
                <script>
                    var btn = document.querySelector('button');
                    var input = document.querySelector('input');

                    btn.onclick = function(){
                        input.value = '被点击了！';
                        this.disabled = true;
                    };
                </script>
        ```
####    (5)操作元素样式
        1.style属性
            background
            backgroundColor
            display
            fontSize
            height
            left
            listStyleType
            overflow
            textAlign
            textDecoration
            textIndent
            transform

####    (6)操作className属性

####    (7)获取焦点 onfocus 失去焦点 onblur

####    (8)排他思想
        两层循环

####    (9)鼠标指针经过时背景变色
        table / thead tr th / tbody tr td 

####    (10)
        1.获取属性：div.getAttribute('id');
        2.设置属性：div.setAttribute('index',2);
        3.移除属性：div.removeAttribute('id');

####    (11)节点层级
        1.父节点
            先建立document.querySelector('.child');
                  child.parentNode;
        2.子节点
            childNodes
            console.log(ul.childNodes[0].nodeType);



# 9.常用命令规则

{% tabs html文件 %}
<!-- tab html文件 -->
```
头  header
导航    nav
侧栏    siderbar
左，右，中间    left，right，center
标志    logo
页面主体    main
新闻    news
子导航  subnav
子菜单  submenu
内容    content / container
尾  footer
栏目    column
登录条  loinbar
广告    banner
热点    hot
下载    download
菜单    menu
搜索    search
友情链接    friedlink
滚动    scroll
文章列表    list
小技巧  tips
加入    joinus
服务    service
状态    status
合作伙伴    partner
版权    copyright
标签页  tab
提示信息    msg
栏目标题    title
指南    guild
注册    register
投票    vote
```
<!-- endtab -->

<!-- tab CSS文件 -->
```
主要样式    master
模块样式    module
基本样式    base
版本样式    layout
专栏    columns
表单    forms 
主题    themes
文字    font
打印    print
```
<!-- endtab -->
{% endtabs %}

# 10. AJAX
 Asynchronous JavaScript and XML（异步的 JavaScript 和 XML）不是新的编程语言，而是一种使用现有标准的新方法。

AJAX 是与服务器交换数据并更新部分网页的技术，在不重新加载整个页面的情况下。
用于创建快速动态网页的技术（通过在后台与服务器进行少量数据交换，AJAX 可以使网页实现异步更新）。

- 传统的网页（不使用 AJAX）如果需要更新内容，必需重载整个网页面。

- 有很多使用 AJAX 的应用程序案例：新浪微博、Google 地图、开心网等等。

## 1. AJAX 应用

### 1. AJAX 基于 Internet 标准
- 运用 XHTML+CSS 来表达资讯；
- 运用 JavaScript 操作 DOM（Document Object Model）来执行动态效果；
- 运用 XML 和 XSLT 操作资料;
- 运用 XMLHttpRequest 或新的 Fetch API 与网页服务器进行异步资料交换；
注意：AJAX 与 Flash、Silverlight 和 Java Applet 等 RIA 技术是有区分的。


AJAX是基于现有的Internet标准，并且联合使用它们：

- XMLHttpRequest 对象 (异步的与服务器交换数据)
- JavaScript/DOM (信息显示/交互)
- CSS (给数据定义样式)
- XML (作为转换数据的格式)


### 2. AJAX 工作原理
![AJAX 原理](https://www.runoob.com/wp-content/uploads/2013/09/ajax-yl.png)

#### 1. 实例
```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">

<script>
function loadXMLDoc(){

    // 1. 创建 XMLHttpRequest 对象
	var xmlhttp;
	if (window.XMLHttpRequest)
	{   //  IE7+, Firefox, Chrome, Opera, Safari 浏览器执行代码
		xmlhttp=new XMLHttpRequest();}
	else
	{   // IE6, IE5 浏览器执行代码
		xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
    }

    // 2. 向服务器发送请求 和 服务器交换数据
	xmlhttp.onreadystatechange=function(){
		if (xmlhttp.readyState==4 && xmlhttp.status==200)
		{
			document.getElementById("myDiv").innerHTML=xmlhttp.responseText;
		}
	}
	xmlhttp.open("GET","/try/ajax/ajax_info.txt",true);
	xmlhttp.send();
}
</script>

</head>
<body>

<div id="myDiv"><h2>使用 AJAX 修改该文本内容</h2></div>
<button type="button" onclick="loadXMLDoc()">修改内容</button>

</body>
</html>
```

#### 1. AJAX - 创建 XMLHttpRequest 对象
- XMLHttpRequest 是 AJAX 的基础。

- 所有现代浏览器均支持 XMLHttpRequest 对象（IE5 和 IE6 使用 ActiveXObject）。XMLHttpRequest 用于在后台与服务器交换数据。这意味着可以在不重新加载整个网页的情况下，对网页的某部分进行更新。

创建 XMLHttpRequest 对象的语法：
```
variable=new XMLHttpRequest();
```
老版本的 Internet Explorer （IE5 和 IE6）使用 ActiveX 对象：
```
variable=new ActiveXObject("Microsoft.XMLHTTP");
```
#### 2. AJAX - 向服务器发送请求
- XMLHttpRequest 对象用于和服务器交换数据。
向服务器发送请求
如需将请求发送到服务器，我们使用 XMLHttpRequest 对象的 open() 和 send() 方法：
```
xmlhttp.open("GET","ajax_info.txt",true);
xmlhttp.send();
```

方法	                 描述
open(method,url,async)	 规定请求的类型、URL 以及是否异步处理请求。
                        -  method：请求的类型；GET 或 POST
                        -  url：文件在服务器上的位置
                        -  async：true（异步）或 false（同步）
                        -  send(string)	

string：                仅用于 POST 请求        
                        -  将请求发送到服务器。

setRequestHeader(header,value)      向请求添加 HTTP 头。
                                    -  header: 规定头的名称
                                    -  value: 规定头的值
                        

与 POST 相比，GET 更简单也更快，并且在大部分情况下都能用。

然而，在以下情况中，请[使用 POST 请求](https://www.runoob.com/ajax/ajax-xmlhttprequest-send.html)：
- 不愿使用缓存文件（更新服务器上的文件或数据库）
- 向服务器发送大量数据（POST 没有数据量限制）
- 发送包含未知字符的用户输入时，POST 比 GET 更稳定也更可靠           

##### 1. Post
如果需要像 HTML 表单那样 POST 数据，请使用 setRequestHeader() 来添加 HTTP 头。然后在 send() 方法中规定您希望发送的数据：
```
xmlhttp.open("POST","/try/ajax/demo_post2.php",true);
xmlhttp.setRequestHeader("Content-type","application/x-www-form-urlencoded");
xmlhttp.send("fname=Henry&lname=Ford");
```

##### 2. Async
1. 当使用 async=true 时，请规定在响应处于 onreadystatechange 事件中的就绪状态时执行的函数：
```
xmlhttp.onreadystatechange=function()
{
    if (xmlhttp.readyState==4 && xmlhttp.status==200)
    {
        document.getElementById("myDiv").innerHTML=xmlhttp.responseText;
    }
}
xmlhttp.open("GET","/try/ajax/ajax_info.txt",true);
xmlhttp.send();
```

2. 如需使用 async=false，请将 open() 方法中的第三个参数改为 false：
我们不推荐使用 async=false，但是对于一些小型的请求，也是可以的。

请记住，JavaScript 会等到服务器响应就绪才继续执行。如果服务器繁忙或缓慢，应用程序会挂起或停止。

注意：当您使用 async=false 时，请不要编写 onreadystatechange 函数 - 把代码放到 send() 语句后面即可：
```
xmlhttp.open("GET","/try/ajax/ajax_info.txt",false);
xmlhttp.send();
document.getElementById("myDiv").innerHTML=xmlhttp.responseText;
```
#### 3. AJAX - 服务器响应
如需获得来自服务器的响应，请使用 XMLHttpRequest 对象的 responseText 或 responseXML 属性。

属性	        描述
responseText	获得字符串形式的响应数据。
responseXML	    获得 XML 形式的响应数据。

##### 1. responseText 属性
如果来自服务器的响应并非 XML，请使用 responseText 属性
responseText 属性返回字符串形式的响应
```
document.getElementById("myDiv").innerHTML=xmlhttp.responseText;
```

##### 2. responseXML 属性
如果来自服务器的响应是 XML，而且需要作为 XML 对象进行解析
```
xmlDoc=xmlhttp.responseXML;
txt="";
x=xmlDoc.getElementsByTagName("ARTIST");
for (i=0;i<x.length;i++)
{
    txt=txt + x[i].childNodes[0].nodeValue + "<br>";
}
document.getElementById("myDiv").innerHTML=txt;
```

#### 4.  AJAX - onreadystatechange 事件
当请求被发送到服务器时，我们需要执行一些基于响应的任务。

每当 readyState 改变时，就会触发 onreadystatechange 事件。

readyState 属性存有 XMLHttpRequest 的状态信息。

下面是 XMLHttpRequest 对象的三个重要的属性：

属性	                 描述
onreadystatechange	    存储函数（或函数名）
                        每当 readyState 属性改变时，就会调用该函数。

readyState              存有 XMLHttpRequest 的状态。从 0 到 4 发生变化。
                        - 0: 请求未初始化
                        - 1: 服务器连接已建立
                        - 2: 请求已接收
                        - 3: 请求处理中
                        - 4: 请求已完成，且响应已就绪                 

status                  200: "OK"
                        404: 未找到页面


在 onreadystatechange 事件中，我们规定当服务器响应已做好被处理的准备时所执行的任务。
当 readyState 等于 4 且状态为 200 时，表示响应已就绪：
```
xmlhttp.onreadystatechange=function()
{
    if (xmlhttp.readyState==4 && xmlhttp.status==200)
    {
        document.getElementById("myDiv").innerHTML=xmlhttp.responseText;
    }
}
```

##### 1. 使用回调函数
回调函数是一种以参数形式传递给另一个函数的函数。

如果您的网站上存在多个 AJAX 任务，那么您应该为创建 XMLHttpRequest 对象编写一个标准的函数，并为每个 AJAX 任务调用该函数。

该函数调用应该包含 URL 以及发生 onreadystatechange 事件时执行的任务（每次调用可能不尽相同）：
```
function myFunction()
{
    loadXMLDoc("/try/ajax/ajax_info.txt",function()
    {
        if (xmlhttp.readyState==4 && xmlhttp.status==200)
        {
            document.getElementById("myDiv").innerHTML=xmlhttp.responseText;
        }
    });
}
```

#### 5. AJAX XML 实例
当用户点击上面的"获取我收藏的 CD"这个按钮，就会执行 loadXMLDoc() 函数。

loadXMLDoc() 函数创建 XMLHttpRequest 对象，添加当服务器响应就绪时执行的函数，并将请求发送到服务器。

当服务器响应就绪时，会构建一个 HTML 表格，从 XML 文件中提取节点（元素），最后使用 XML 数据的 填充 id="demo" 的表格元素：

```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<style>
table,th,td {
  border : 1px solid black;
  border-collapse: collapse;
}
th,td {
  padding: 5px;
}
</style>
</head>
<body>

<h1>XMLHttpRequest 对象</h1>

<button type="button" onclick="loadXMLDoc()">获取我收藏的 CD</button>
<br><br>
<table id="demo"></table>

<script>
function loadXMLDoc() {
  var xhttp = new XMLHttpRequest();
  xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
      myFunction(this);
    }
  };
  xhttp.open("GET", "cd_catalog.xml", true);
  xhttp.send();
}
function myFunction(xml) {
  var i;
  var xmlDoc = xml.responseXML;
  var table="<tr><th>Artist</th><th>Title</th></tr>";
  var x = xmlDoc.getElementsByTagName("CD");
  for (i = 0; i <x.length; i++) {
    table += "<tr><td>" +
    x[i].getElementsByTagName("ARTIST")[0].childNodes[0].nodeValue +
    "</td><td>" +
    x[i].getElementsByTagName("TITLE")[0].childNodes[0].nodeValue +
    "</td></tr>";
  }
  document.getElementById("demo").innerHTML = table;
}
</script>

</body>
</html>
```


#### 6. AJAX JSON
1. loadXMLDoc() 函数
当用户点击上面的"获取课程数据"这个按钮，就会执行 loadXMLDoc() 函数。
loadXMLDoc() 函数创建 XMLHttpRequest 对象，添加当服务器响应就绪时执行的函数，并将请求发送到服务器。
```
function loadXMLDoc()
{
  var xmlhttp;
  if (window.XMLHttpRequest)
  {
    // IE7+, Firefox, Chrome, Opera, Safari 浏览器执行代码
    xmlhttp=new XMLHttpRequest();
  }
  else
  {
    // IE6, IE5 浏览器执行代码
    xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
  }
  xmlhttp.onreadystatechange=function()
  {
    if (xmlhttp.readyState==4 && xmlhttp.status==200)
    {
      var myArr = JSON.parse(this.responseText);
      myFunction(myArr)
    }
  }
  xmlhttp.open("GET","/try/ajax/json_ajax.json",true);
  xmlhttp.setRequestHeader("Content-Type", "application/json;charset=UTF-8");
  xmlhttp.send();
}
function myFunction(arr) {
  var out = "";
  var i;
  for(i = 0; i < arr.length; i++) {
    out += '<a href="' + arr[i].url + '">' + 
    arr[i].title + '</a><br>';
  }
 document.getElementById("myDiv").innerHTML=out;
}
```

当服务器响应就绪时，我们就使用 JSON.parse() 方法将数据转换为 JavaScript 对象。：


2. AJAX 服务器页面
上面这个例子中使用的服务器页面实际上是一个名为 "json_ajax.json" JSON 文件。

JSON 数据如下：
```
[
  {
    "title": "JavaScript 教程",
    "url": "https://www.runoob.com/js/"
  },
  {
    "title": "HTML 教程",
    "url": "https://www.runoob.com/html/"
  },
  {
    "title": "CSS 教程",
    "url": "https://www.runoob.com/css/"
  }
]
```
发送 JSON 数据：
```
xmlhttp.send(JSON.stringify({ "email": "admin@runoob.com", "response": { "name": "runoob" } }));
```

##### 1. 源代码
```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<script>
function loadXMLDoc()
{
  var xmlhttp;
  if (window.XMLHttpRequest)
  {
    // IE7+, Firefox, Chrome, Opera, Safari 浏览器执行代码
    xmlhttp=new XMLHttpRequest();
  }
  else
  {
    // IE6, IE5 浏览器执行代码
    xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
  }
  xmlhttp.onreadystatechange=function()
  {
    if (xmlhttp.readyState==4 && xmlhttp.status==200)
    {
	  var myArr = JSON.parse(this.responseText);
      myFunction(myArr)
    }
  }
  xmlhttp.open("GET","/try/ajax/json_ajax.json",true);
  xmlhttp.setRequestHeader("Content-Type", "application/json;charset=UTF-8");
  xmlhttp.send();
}
function myFunction(arr) {
  var out = "";
  var i;
  for(i = 0; i < arr.length; i++) {
    out += '<a href="' + arr[i].url + '">' + 
    arr[i].title + '</a><br>';
  }
 document.getElementById("myDiv").innerHTML=out;
}
</script>
</head>
<body>

<h2>AJAX JSON</h2>
<button type="button" onclick="loadXMLDoc()">请求 JSON 数据</button>
<div id="myDiv"></div>
 
</body>
</html>
```
