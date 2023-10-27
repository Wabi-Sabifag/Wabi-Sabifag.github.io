---
title: Linux基础命令
date: 2023-01-02 15:07:00
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
- HDFS基础命令
keywords:   #页面关键词
cover:  'img/10.jpg'     #文章缩略图（如果没有设置top_img，文章页顶部将显示缩略图，可设为false/图片地址/留空）

comments:         #显示页面评论模块 默认 true
top_img:  'img/10.jpg'        #页面顶部图片
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

### 启动Hadoop
```
cd / -name hadoop
sbin/start-all.sh
jps
bin/hadoop dfsadmin -report

初始化：bin/hadoop namenod -format
集群启动：sbin/start-all.sh
集群停止：sbin/stop-all.sh
查看日志：ll logs/
	  cat logs/hadoop-hadoop-namenode-master.log
```



### 查看HDFS的命令：hadoop fs
```
Hadoop fs -ls
	  -mkdir
	  -copyFromLocal newtest  /home/user
	  -put /home/user  /user/hadoop
	  -copyToLocal /user/hadoop /home/hadoop
	  -get /user/hadoop /home/user
	  -chmod 777 /user/hadoop
	  -rm  -r text
```
### 负载均衡：hdfs balancer
```
hdfs balancer -threshold 
```	  

### HDFS API使用方法
1.get（）方法实现
	static FileSystem get(Configuration conf);
2.获取具体的封装
 	opertor(){
		获取Configuration对象
		获取FileSystem对象
		对文件进行相应操作
	}
###	1.上传本地文件：
		具体实现：CopyFile.jar
```	
		package com.hafs;
		import org.apache.hadoop.conf.Configuration;
		import org.apache.hadoop.fs.FileStatus;
		import org.apache.hadoop.fs.FileSystem;
		impory org.apache.hadoop.fs.Path;
		public class CopyFile{
			public static void main(String[] args) throws Excerion{
				Configuration conf = new Configuration();
				FileSystemhdfs = FileSystem.get(conf);
				//本地文件
				Path src = new Path("/home/hadoop/CopyFile.text");
				//HDFS的指定位置
				Path dst = new Path("/");
				hdfs.copyFromLocalFile(src,dst);
				System.out.print("Upload to"+conf.get("fs.default.name"));
				FileStatus files[] = hdfs.listStatus(dst);
				for(FileStstus file:files){
					System.out.print(file.getPath());
				}
			}
		}
```
		导出为CopyFile.jar文件，上传到集群中并文件所在位置执行命令：
```		
			Hadoop jar CopyFile.jar com.hdfs.CopyFile
```	
###	 2.创建HDFS文件
		
		Public FSDateOutputStream create (Path f)
	
		具体实现：CreateFile.jar
```
		Package com.hdfs;
		import org.apache.hadoop.conf.Configuration;
		import org.apache.hadoop.fs.FSDataOutputStream;
		import org.apache.hadoop.fs.FileSysteam;
		import org.apache.hadoop.fs.Path;
		public class CreateFile{
			public static void main (String[] args) throws Exception{
				Configuration conf = new Configuration();
				FileSysteamhdfs = FileSyteam.get(conf);
				 byte[] buff = "hello hadoop world!\n".getByets();
				 Path dfs = new Path("/test");
				 FSDataOutputStream outputStream = hdfs.create(dfs);//调用create（）方法，创建文件
				 outputStream.write(buff,0,buff.length);
				}
			}
```

		导出为CreatFile.jar文件，上传到集群中并文件所在位置执行命令：
```
			hadoop jar CreateFile.jar comhdfs.CreateFile
```

###	3.创建HDFS目录
		
		public boolean mkdirs(Path f)

		具体实现：CreateDir.jar
```
			package com.hdfs;
			import org.apache.hadoop.conf.Configuration;
			improt org.apache.hadoop.fs.FileSysteam;
			import org.apache.hadoop.fs.Path;
			public class CreateDir{
				public static void main (String[] args) throws Exception{
					Configuration conf = new Configuration();
					FileSyateamhdfs = FileSyateam.get(conf);
					Path dfs = new Path("/TestDir");
					//调用mkdir（）方法，创建目录
					hdfs.mkdirs(dfs);
				}
			}
```

        导出CreateDir.jar文件，上传到集群中并文件所在位置执行命令：

```
hadoop jar CreateDir.jar com.hdfs.CreateDir;
```