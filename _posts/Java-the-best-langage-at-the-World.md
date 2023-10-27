---
title: Java, the world's best programming language #【必需】页面标题
description: 栈的添加删除 # 副标题
sticky:             #置顶
toc:                #显示文章TOC（默认为设置中toc的enable配置）
toc_number:         #显示toc_number（默认为设置中toc的number配置）
abbrlink: 997804fe
date: 2022-12-25 22:10:52  #【必需】页面创建日期
updated:                #页面更新日期
type: Java   #【必需】标签、分类和友情链接三个页面需要配置
tags: 
- Java
- 数据结构
- 策略模式
# - Python      #文章标签  
# tags: Python
categories: 
- Java       #文章分类
- 数据结构
- 策略模式
keywords:   #页面关键词
cover:    'img/23.png'   #文章缩略图（如果没有设置top_img，文章页顶部将显示缩略图，可设为false/图片地址/留空）

comments:         #显示页面评论模块 默认 true
top_img:    'img/23.png'        #页面顶部图片
mathjax:            #显示mathjax（当设置mathjax的per_page： false时，才需要配置，默认 false）
katex:              #显示katex（当设置katex的per_page： false时，才需要配置，默认 false）
aside:              #显示侧边栏 （默认 true）
aplayer:            #在需要的页面加载aplayer的js和css，请参考文章下面的
highlight_shrink:       #配置代码框是否展开（true/false）

copyright:                              #显示文章版权模块
copyright_author: Wabi-Sabifag          #文章版权模块的文章作者
copyright_author_href:                  #文章版权模块的链接
copyright_url: 'https://Wabi-Sabifag.github.io'
copyright_info: 此文章版权归Wabi-Sabifag所有。如有转载，请注明来自原作者(但万物开源)  #文章版权模块的文字
---

## 1.Java基础
### 1.关键词
#### 1.return
Java中return 用法小结
```
package test;
return：必须放在方法中
//return的主要作用有两点：
//1.返回方法指定类型值
//2.用于方法结束的标志,return 后面的语句不会被执行
public class Test001 {
   public static void main(String[] args) {
       int i;
       System.out.println("return语句之前"+getInfo());
       for (i = 0; i < 5; i++) {
           if(i==3){
               return;//无返回类型，用于方法的结束
           }
           System.out.println(String.format("i=%d",i));
       }
       //return 之后的语句将不会被执行
       System.out.println("return语句之后"+getInfo());
   }
   public static int getInfo(){
       return 1;//有返回类型，返回方法指定类型的返回值
   }
```
#### 2.进制转换
```
10进制转化其他进制	对应的方法,参数:n(原10进制数据),r(进制),	返回值
10进制转2进制	Integer.toBinaryString(n);	一个二进制字符串.
10进制转8进制	Integer.toOctalString(n);	一个八进制字符串
10进制转16进制	Integer.toHexString(n);	一个16进制字符串
10进制转 r 进制	Integer.toString(100, 16);	一个r进制字符串
```


### 2.数组
#### 1.List
##### 1.List数据的指定修改
```
package ArrayForiter;
import java.util.*;
import java.util.stream.*;

import org.junit.jupiter.api.Test;
public class ListItemRemoveTests {
	public List<String> initList = Arrays.asList("360","aliyun","baidu","bilibili","amazon","bytedance","Tencent");
	/*
	 * 增强for循环删除 ConcurrentModificationException
	 */
	public void test1() {
		List<String> list = new ArrayList<String>(initList);
		for(String element : list) {
			if(element.startsWith("b")) {
				list.remove(element);
			}
		}
		System.out.println(list);
	}
	@Test
	public void test1_1() {
		List<String> list = new ArrayList<String>(initList);
		list.forEach ((e) -> {
			if(e.startsWith("b")) {
				list.remove(e);
			}
		});
		System.out.println(list);
		
	}
	
	/* 低级for size, 删除不全。（功能不完善的 bug */
	public void test2() {
		List<String> list = new ArrayList<String>(initList);
		for (int i = 0; i < list.size(); i++) {
			String str = list.get(i);
			if(str.startsWith("b")) {
				list.remove(i);
			}
		}
		System.out.println(list);
	}
	
	/* 
	 * 角标越界
	 * 无法阻止 for的i增大 
	*/
	public void test3() {
		List<String> list = new ArrayList<String>(initList);
		int size = list.size();
		for (int i = 0; i < size; i++) {
			String str = list.get(i);
			if(str.startsWith("b")) {
				list.remove(i);
			}
		}
		System.out.println(list);
	}

	/*
	 * 逆序删除 
	 * 从后面开始，可以改变 for 增大导致的角标越界
	 */
	public void test4() {
		List<String> list = new ArrayList<String>(initList);
		for(int i=list.size()-1;i>0;i--) {
			String str = list.get(i);
			if(str.startsWith("b")) {
				list.remove(i);
			}
		}
		System.out.println(list);
	}

	/*
	 * 调用 iteration 提供的方法
	 */
	public void test5() {
		List<String> list = new ArrayList<String>(initList);
		for(Iterator<String> iterator = list.iterator();iterator.hasNext();) {
			String str = iterator.next();
			if(str.startsWith("b")) {
				iterator.remove();
			}
		}
		System.out.println(list);
	}
	
	public void test5_1() {
		List<String> list = new ArrayList<String>(initList);
		for(Iterator<String> iterator = list.iterator();iterator.hasNext();) {
			String str = iterator.next();
			if(str.startsWith("b")) {
				list.remove(str);  // 用的 iterat 方法 但没在关键点用iterator.remove();
			}
		}
		System.out.println(list);
	}

	/*
	 * filter 过滤 
	 * 得到一定量的反向元素
	 */
	public void test6() {
		List<String> list = new ArrayList<String>(initList);
		list = list.stream().filter(e -> !e.startsWith("b")).collect(Collectors.toList());
		System.out.println(list);
	}
	
	
	public static void main(String[] s) {
		ListItemRemoveTests a = new ListItemRemoveTests();
		
		/*
		 * 原因： Iterator迭代时不能remove。 
		 * 	是同步操作问题  两者修改次数不一致
		 */
		//a.test1();
		//a.test1_1();
		
		//a.test2();
		//a.test3();
		
		a.test4();
		a.test5();
		
		/*
		 * 用的 iterat 方法 但没在关键点用iterator.remove();
		 */
		//a.test5_1();
		
		a.test6();
	}
}

```
## 2.Java策略模式
IStack.java
```
public interface IStack<T> {
	
	/**
	 * 初始化栈
	 * @param maxSize: 数组的最大长度。栈的最大长度。
	 */
	public void initStack(int maxSize);
	
	/**
	 * 销毁栈
	 */
	public void destroyStack();
	
	/**
	 * 添加数据，进栈。
	 * @param data 要被添加的数据.类型不确定，所以用泛型。
	 */
	public void push(T data);
	
	/**
	 * 删除栈顶元素
	 */
	public void pop();

	/**
	 * 判断栈是否为空
	 * @return true or false.
	 */
	public boolean isEmpty();
	
	/**
	 * 获取栈顶元素
	 * @return 栈顶数据元素。数据元素的类型不确定，所以是泛型。
	 */
	public T getTop();	
}

```
Stack.java
```
public class Stack<T> implements IStack<T> {

	private int length;// 元素个数。栈的长度。
	private T arr[];// 用于存放数据的数组。因为是顺序栈，所以用数组。数组取值是用角标 arr[0] arr[1] ...
	private int maxSize;

	/**
	 * 构造函数
	 * 
	 * @param maxSize
	 *            数组的最大长度
	 */
	public Stack(int maxSize) {
		this.maxSize = maxSize;
		initStack(maxSize);
	}

	@Override
	public void initStack(int maxSize) {
		this.maxSize = maxSize;
		// 初始化数组。为什么要初始化数组，因为数组不初始化，就没有分配内存空间，是一个空对象，也就是空指针。
		arr = (T[]) new Object[maxSize];
	}

	@Override
	public void destroyStack() {
		// TODO Auto-generated method stub
	}

	// 添加值 1判断 原有数值长度 是否 已满于最大数组长
	// 2 数值 赋予 原有数组末，数组长增加
	@Override
	public void push(T data) {
		if(this.length >= this.maxSize){
			System.out.println("已满");
			return;
		}
		arr[this.length] = data;
		this.length++;
	}

	// 添加值 1判断 原有数值长度 是否 为零
	// 2 数值 赋予 原有数组 次末，数组长减少
	@Override
	public void pop() {
		if(this.length == 0){
			System.out.println("已经到底，无法pop");
			return;
		}
		arr[this.length-1] = null;
		this.length--;
	}

	// 指针 1判断长度 如果为零返回 否则 返回数组 次长度
	@Override
	public T getTop() {
		if(this.length == 0){
			return null;
			}
		return this.arr[this.length-1];
		
			}

	@Override
	public boolean isEmpty() {
		return this.length == 0;
	}

}
```
Test.java
```
public class Test {
	
	public static void main(String[] args) {
		Stack<Integer> s = new Stack<>(1024); // 指定栈的长度最大值是1024.
		
		
		s.push(1);
		s.push(2);
		s.push(3);
		
		s.pop();
		s.pop();
		
		Integer top = s.getTop();
		System.out.println(top);
	}

}
```

