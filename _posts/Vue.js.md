---
title: Vue.js
date: 2023-02-23 12:14:11
description: # 副标题
sticky:             #置顶
toc:                #显示文章TOC（默认为设置中toc的enable配置）
toc_number:         #显示toc_number（默认为设置中toc的number配置）
abbrlink: 997804fe
updated:                #页面更新日期
type: Vue   #【必需】标签、分类和友情链接三个页面需要配置
tags: 
- JavaScript #文章标签  
- Vue
categories: 
- JavaScript #文章标签  
- Vue
keywords:   #页面关键词
cover: 'img/15.png'       #文章缩略图（如果没有设置top_img，文章页顶部将显示缩略图，可设为false/图片地址/留空）

comments:         #显示页面评论模块 默认 true
top_img:  'img/15.png'        #页面顶部图片
mathjax:            #显示mathjax（当设置mathjax的per_page： false时，才需要配置，默认 false）
katex:              #显示katex（当设置katex的per_page： false时，才需要配置，默认 false）
aside:              #显示侧边栏 （默认 true）
aplayer:            #在需要的页面加载aplayer的js和css，请参考文章下面的
highlight_shrink:       #配置代码框是否展开（true/false）
---

# Vue.js
## 1.Vue实列
### 1.挂载元素
### 2.数据
### 3.初始值
```
name:'',
count:0,
price:[],
flag:true
```
#### 1.创建Vue实列
```
		实列：
		<script src="./vue.js"></script>   //1.导入vue.js
		<div class="box">    				//2.1挂载数据
			<h3>NetWeb:{{name}}</h3>
			<h3>NetWebURl:{{url}}</h3>
		</div>
		<script type="text/javascript">
			var demo = new Vue({
				el:'.box',
								//2.2挂载数据代入
				data:{			// 3.数据
					name:'Neoction School',	
					url:'www.NeoctionSchool'
					
				}
			})
		</script>
```
#### 2.重新设置Vue实列
-----data属性传入Vue实列
```
			//设定的data数据
			var data={name:'Holle,Java',url:'www.java.org.com'}; 
			//创建数据 Vue实列，自动代理 data对象
			var demo=new Vue({
				el:'.box',
				// 导入已存在的数据data
				data:data 
			});
			//锚定对象  
			//将自定义数据data的url属性赋值给Vue实列的name
			demo.name=data.name;
			 //重新设置属性
			demo.url='httpa://www.java.org.com';
```
#### 3.$ 区分符
------vue实列对象与用户定义属性的区分
```
demo.$data=data;
```


### 4.方法(methods)
```
			<div class="box">    				
				<h3>{{showInfo()}}</h3>    
			</div>

			//设定的data数据
			var data={name:'Holle,Java',url:'www.java.org.com'}; 
			//创建数据 Vue实列，自动代理 data对象
			var demo=new Vue({
				el:'.box',
				// 导入已存在的数据data
				data:data,
					// {name:'Holle,Java',url:'www.java.org.com'},
				methods:{
					showInfo:function(){
						return this.name+":"+this.url 
					}
				}
			});
			
			demo.$data=data;
```
注意：
	1.调用方法带()
	2.methods方法放入{}内部
	3.该方法有异常问题

### 5.生命周期钩子函数
每一个Vue实列创建都有一系列的初始化步骤，通过这些钩子函数可以定义业务逻辑
1. beforeCreate：在Vue实列开始初始化时调用
2. created：在实列创建之后进行调用，此时尚未开始DOM编译
3. mounted：在DOM文件渲染后进行调用（类似window.onload() )
4. beforeDestroy：在销毁实列前调用，此后实列任然有效
5. destroyed：在实列销毁后进行调用
```
钩子函数:function(){ },
```

## 2.数据绑定
Vue.js 最核心的特性之一。建立数据绑定之后数据和视图会相互关联，当数据发生变换时，视图会自行进行更新。
### 1.插值
#### 1. 文本插值
##### 1.插值
文本插值是最基本的形式
##### 2.v-once
单词插值，当数据对象的属性值发生变换时，插入的文本将不会更新
注意：
1. v-once在标签内，不需要挂载属性
2. 需要 插值 传入引用数据

#### 2.插入HTML
因为 插值 会将值作为普通文本处理，输出HTML内容需要v-html
```
		实列：
		<div class="box">
			<p v-html="message"></p>
		</div>
		<script type="text/javascript">
			var demo=new Vue({
				el:".box",
				data:{
					message:'<h1>Java,the best language in the world.</h1>'
				}
			})
		</script>
```
注意：
	1.v-html在标签内，挂载data数据的属性
	2.不需要 插值  来引用数据
#### 3.属性
因为 插值 不能应用在html属性中。
要为html元素绑定属性，不能直接使用文本插值的方式，而需要v-bind指令对属性进行绑定。
##### 1.为html属性绑定 class
为html元素绑定class属性(css)
###### 1.实列一
将标签的class属性和数据对象的value属性进行绑定
```
		// html 显示
		<div class="box">   
			 // 声明 v-bind  调用js文件的class的value值。			
			<span v-bind:class="value">Dream fall in truly。</span>
		</div>

		// js 实现
		<script type="text/javascript">
			var demo=new Vue({
				el:".box",
				data:{
					// 实现的css样式，在css池中定义
					value:'title'
				}
			});
		</script>	

		//  css 样式池
		<style type="text/css">
			.title{
				color: #ff0000;
				border: 1px solid #FF00FF;
				display: inline-block;
				padding: 5px;
			}
		</style>
```
###### 2.实列二
应用v-bind指令将<\span>标签的class属性与数据对象中的value属性进行绑定，并判断title的值，如果title的值为true，则使用title；否则不适用该类
```
		//html显示
		<div class="box">    				
			<span v-bind:class="{'title':value}">Dream fall in truly。</span>
		</div>

		//js 实现
		<script type="text/javascript">
			var demo=new Vue({
				el:".box",
				data:{
					value:true
				}
			});
		</script>

		//css样式池
		<style type="text/css">
			.title{
				color: #ff0000;
				border: 1px solid #FF00FF;
				display: inline-block;
				padding: 5px;
			}
		</style>
```
注意：
	1.v-bind:class="{ 'title':value} ”  需要 {} 和实列一不同点
	
#### 4.表达式
给数据提供简写方式：
```
列：
	<a v-bind:href="url">明日学院</a>
	<!-- 简写 -->
	<a :href="url">明日学院</a>

列：
		<div id="box">
			QQ:{{email.substr(0,email.indexOf('@'))}}
			<br />
			e-mail:{{email}}
		</div>
		<script type="text/javascript">
			var demo=new Vue({
				el:'#box',
				data:{
					email:'4006751066@qq.com'
					}
				});
		</script>	
```
### 2.过滤器
	对于一些需要经复杂计算的数据绑定，简单的表达式无法实现。
vue.js的过滤器进行处理，可通过自定义的过滤器对文本进行格式化。
	过滤器可以在 插值 和 v-bind 指令中，过滤器需要被添加在JavaScript表达式的尾部，由管道符号  "|" 表示。
格式：
```
		<!-- 在 插值 中 -->
		{{message | myfilter}} 
		<!-- 在v-bind指令中 -->
		<div v-bind:id="rawId | formatId"></div>
``` 
定义过滤器的两种方式：
1. 第一种：
	应用Vue.js全局变量 Vue.filter()
```
Vue.filter( ID,function(){ } )

```
2. 第二种：
	选项定义本地过滤器 filter:{}
```
<a id="A">{{title | subStr}}</a>

<script>
	new Vue({
		 el:"A",
		 data:{
			title:"这个String的长度"
		 },
		 filter:{
			subStr:function(value){
				if(value.length > 10){
					return value.subStr(0,10)+"...";
				}else{
					return value;
				}
		 	}
		}
	});
</script>
```
注意：
1.多个过滤器可以串联使用，在filter:{} 中的本地方法可以通过写在插值后 用|隔开。
2.过滤器实质是一个方法，可以将参数传入设定的方法

### 3.指令
解释：
v-bind: 、v-on: 等为指令
1. 参数
解释： 
在指令和表达式之间，用冒号分隔开的
```
<img v-bind:src="imgsrc">         			 # img标签的 src 属性
<button v-on:click="login">登录</button>	 # 监听的事件名称 click
```
2. 修饰符
解释：
在参数后面，以半角句点符号指明的特殊后缀。
列：
```
	#  .prevent 修饰符用于调用 event.preventDefault() 方法。
<form v-on:submit.prevent="onSubmit"></form>
```
解释：
当提交表单时会调用event.preventDefault()方法 用于阻止浏览器的默认行为。


## 3.列表渲染
### 1.数组更新
Vue.js 有包含检测数组变化的变异方法，调用时可以改变原始数据，并触发试图更新。

方法名      说明

push()		像数据的末尾添加一个或多个元素

pop()		将数组的最后一个元素从数组中删除

shift()		将数组的第一个元素从数组中删除

unshift()	向数组的开头添加一个或多个元素

splice()	添加或删除数组中的元素

sort()		对数组的元素进行排序

reverse()	颠倒数组中元素的顺序

filter()	

concat()	

slice()		获取数组该索引开始的元素



```
列：
var demo = new Vue({
	el: '#box',
	data: {
		items:[ //定义人物名称数组
			{name:'张三'},
			{name:'李四'}
		]
	}
})
// 向数组末尾添加数组元素
demo.items.push({name:'赵六'});

```

### 2. 添加对象属性
#### Vue.set()  vuedemo.$set() Object.assign()
##### 1.单列属性
```
Vue.set(demo.items, 1, {name:'李三'});
或
vuedemo.$set(demo.items, 1, {name:'李三'});
```
##### 2.多列属性  
```
vuedemo.items = Object.assign(
	{}, 
	vuedemo.items, 
	{
		interest: "Sing",
		address: "BeiJing"
	}
);
```
