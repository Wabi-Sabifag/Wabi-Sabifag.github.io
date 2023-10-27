---
title: BigData-词频统计编程
date: 2023-01-02 15:07:10
description: # 副标题
sticky:             #置顶
toc:                #显示文章TOC（默认为设置中toc的enable配置）
toc_number:         #显示toc_number（默认为设置中toc的number配置）
abbrlink: 997804fe
updated:                #页面更新日期
type: Linux   #【必需】标签、分类和友情链接三个页面需要配置
tags: 
- Linux #文章标签  
- BigData
- 基础
categories: 
- Linux       #文章分类
- BigData
- 词频统计编程
keywords:   #页面关键词
cover: 'img/9.jpg'   #文章缩略图（如果没有设置top_img，文章页顶部将显示缩略图，可设为false/图片地址/留空）

comments:         #显示页面评论模块 默认 true
top_img:  'img/9.jpg'        #页面顶部图片
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
## BigData Hadoop 词频统计编程
#### 1.编译WordCount.java 程序,将程序在Hadoop 集中运行
#### 2.在HDFS中处理文件 进行上传
#### 3.运行 Word Count.java

1.文件上传到 /home/hadoop/data/wordcount 
2.切换到该目录下
3.Hadoop集群上运行 MapReduce的程序WordCount.java
```
	gedit WordCount.java
```
4.在本地创建 wordcount_classes :
```
	mkdir wordcount_classes
```
5.编译 WordCount.java. 输入下面的命令编译 WordCount.java 程序并设置正确的路径及输出目录.
	用 -d (directory,目录)选择指定编译结果的 .class文件的存放目录:
```
	javac -cp /home/hadoop/hadoop-2.9.0/share/hadoop/*   -d  wordcount_class WordCount.java
```
6.为编译的 wordcount目录创建一个.jar 文件.  因为需要将该 .jar 发送到集群的其他节点同时运行.
```
	jar -cvf WordCount.jar -C wordcount_classes/ .
```
7.创建Map Reduce 输入文件 /tmp/MR-WordCount,上传到 YouTube 数据集当作 WordCount程序的输入文件.
```
    Hadoop fs -mkdir /tmp/MR-WordCount
```
8.使用Hadoop的put命令把 YouTupe 数据集从本地系统的 /home/hadoop/data/wordcount 复制到HDFS 的 /tmp/MR-WrodCount目录:
```
	hadoop fs -put YoutubeDataSets.txt  /tmp/MR-WordCount/
```
9.查看文件是否上传成功,命令如下:
```
	hadoop fs -ls /tmp/MR-WordCount/
```
10.运行MapReduce
```
	hadoop jar WordCount.jar  cn.hust.book.bigdata.ch04.WordCount 
	/tmp/MR-WordCount/YoutubeDataSets.txt 
	/tmp/MR-WordCount/output  
```
### WordCount.java
```
import java.awt.JobAttributes;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;
import java.lang.module.Configuration;
import java.net.URI;
import java.nio.file.FileSystem;
import java.nio.file.LinkOption;
import java.nio.file.Path;
import java.nio.file.WatchKey;
import java.nio.file.WatchService;
import java.nio.file.WatchEvent.Kind;
import java.nio.file.WatchEvent.Modifier;
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;
import java.util.Scanner;
import java.util.StringTokenizer;

import javax.naming.Context;

import org.w3c.dom.Text;

public class WordCount {
	public static class MyMapper extends Mapper<Object,Text,Text,IntWritable>{
		private final static IntWritable one = new IntWritable(1);
		private Text word = new Text();
		public void map(Object key,Text value,Context context) throws IOException,InterruptedException{
			StringTokenizer itr = new
					StringTokenizer(value.toString(),"\t"); //以制表符分隔一行文本
				while(itr.hasMoreTokens()) {
					word.set(itr.hasMoreTokens());
					context.write(word,one);
				}
		}
	}
	
public static class MyReducer extends Reducer<Text,IntWritable,Text,IntWritable>{
	public void reduce(Text Key,Iterable<IntWritable>values,Context context) throws IOException,InterruptedException  {
		int sum = 0;
		for(IntWritable value: values) { // 相同Key累计计数
			sum += value.get();
		}
		countext.write(key,new IntWritable(sum));
	}
}
	
public static void main(String[] args) {
			Configuration conf = new Configuration();
			String[] otherArgs = new GenericOptionsParser(conf,args).getRemainingArgs();
			Job job = new Job(conf,"WordCount");
			job.setJarByClass(WordCount.class);
			job.setMapperClass(MyMapper.class);
			job.setReducerClass(MyReducer.class);
			job.setOutputKeyClass(Text.class);
			job.setOutputValueClass(InyWritable.class);
			FileInputStream.addInputPath(job,new Pathath(otherArgs[0]));
			FileOutputStream.setPutputPath(job,new Path(otherArgs[1]));
			System.out.println(job,waitForCompletion(true) ? 0:1 );
	}
}
```

