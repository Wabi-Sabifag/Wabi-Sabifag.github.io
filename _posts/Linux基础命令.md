---
title: Linux基础命令
date: 2023-01-02 15:06:59
description: # 副标题
sticky:             #置顶
toc:                #显示文章TOC（默认为设置中toc的enable配置）
toc_number:         #显示toc_number（默认为设置中toc的number配置）
abbrlink: 997804fe
updated:                #页面更新日期
type: Linux   #【必需】标签、分类和友情链接三个页面需要配置
tags: 
- Linux #文章标签  
- 基础
categories: 
- Linux       #文章分类
- 基础命令
keywords:   #页面关键词
cover:   'img/47.jpg'    #文章缩略图（如果没有设置top_img，文章页顶部将显示缩略图，可设为false/图片地址/留空）

comments:         #显示页面评论模块 默认 true
top_img:  'img/47.jpg'        #页面顶部图片
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

## 1.1.1 用户和用户组

### 用户创建
1.useradd
2.passwd

### 1.创建用户组
1.groupadd testgroup

### 2.创建用户组同时增加用户组
1.useradd  -g testgroup test

### 3.已有用户增加用户组
1.usermod -G groupname username

### 4.永久删除用户和用户组
1.userdel test
2.userdel -r test
3.groupdel testgroup

## 1.1.2 文件与目录

### 1.切换
1.cd /home
2.cd 		%返回上级
3.cd ../..
4.pwd   %显示当前目录名称

### 2.查看目录文件信息
1.ls -a 	%所有文件
2.ls -al	%详细信息
3.ls -alrt	%按时间（l：详细列表 r:反向序列  t:按时间）

### 3.文件目录复制
1.cp file1
2.cp -a dir1	%目录
3.cp -a tem/dir1 .	%复制目录到当前目录

### 4.文件目录的创建、移动、删除
1.mkdir dir1 
2.mkdir -p /tmp/dir1/dir2
3.mv dir1  dir2		%重命名
4.rm -f file1		%删除文件名为file1 文件
5.rm -rf dir2 		%删除dir2 目录和子目录内容

### 5.查看文件内容
1.cat file
2.tac file 
3.more file	%查看长文件内容

### 6.文本内容处理
1.grep str /tmp/test		 
2.grep ^str /tmp/test		%str 开始的文件
3.grep [0-9] /tmp/test		%包含数字的
4.grep str -r /tmp/*		%在目录 tmp以及子目录查找
5.diff file1 file2		%文本间不同的
6.sdiff file1 file2		%一对比的方式显示不同

### 7.Vim文件编辑器
1.vim test.txt
2.按 i 键 进入

### 8.查询
1.find / -name file1  
2.find / -user user1
3.find /home/user1 -name *.bin 	%查询扩展名 .bin 文件

### 9.压缩、解压
1.tar -cvf archive.tar file 	%文件file压缩成archive.tar	
	（C:建立压缩文档 V：显示所有过程  F显示档案名称）
2.tar -tf archive.tar		%显示一个包的内容
3.tar -xvf archive.tar		%解压一个包
4.tar -xavf archive.tar.gz	%解压.tar.gz压缩包
	（X:解压  tar.gz:压缩/解压的为tar.gz 文件）
5.tar -xjvf archive.tar.bz2 -C /tmp
				%把压缩包解压到 /tmp 目录下

### 10.修改文件目录权限
1.chmod 777 test 		%test文件修改为EveryOne可用
2.chmod a+rwx test		%同上
	（a：所有用户 g:同组用户 o:其他用户r:读w:写x：执行 ）
3.chgrp student /opt/book	%把/opt/book用户组修改为				 student
4.chown zhangsan /opt/book	% /opt/book文件所有者修改为				  zhangsan

2.1.3 主机名

### 11.查找主机名
1.hostname 

### 12.永久修改主机名
1.hostnamectl set-hostname hadoop
  cat /etc/hostname  
2.vim /etc/hosts
  cat /etc/hosts

## 1.1.4分区管理

### 1.查看硬盘使用状况
1.df -h 	%-h:显示为易读格式

### 2.硬盘分区
1.fdisk -l		%查看分区
2.fdisk /dev/sda3	%使用fdisk管理分区

### 3.挂载硬盘
1.mkdir /mnt/vcdrom
2.mount

## 1.1.5文件目录访问权限
	
###	1.查看文件和目录访问权限
		ls  -l /boot
###	2.修改文件和目录访问权限
		chown [选项] 属主[.属主] <文件名>
		-c		文件更改后显示动作信息（历史） 
		-R 		对目录以及子目录，文件递归设置
		-v		输出详细内容
		
		chgrp [选项] 属主[.属主] <文件名>
		-c 		
		-R
	
		chmod [选项] 属主[.属主] <文件名>
		-c
		-R
		-v
		-help
			u
			g
			o
			a
			操作模式：+,-,=
			权限组合：r,w,x
			例题：增加文件/root/first.sh的属性可执行权限，
			      增加文件/root/file1.txt的属组可写权限
				chmod u+x /root/first.sh
				chmod g+w /root/file1.txt	 
			例题：用数字赋予/root/student1.txt仅有属主可读写权限
				chmod 600 /root/test.sh

## 1.1.6用户命令管理用户
	
###	1.创建用户
		useradd [选项] <用户>
		-c comment	注释信息 
		-g group	主群组
		-G group	附加组
		-d home		主目录路径
		-s shell	登录Shell环境/bin/bash
		-u UID		用户ID
		-e expire	过期日期，默认null xxxx-xx-xx
		-f inactive	过期后可用天数
	
###	2.删除用户
		userdel [选项] <用户>
		-r		删除时是否删除主目录
		rm -r userA
###	3.密码设置与修改
		passwd [选项] <用户>
		-l name		锁住普通用户
		-u name 	解锁普通用户
		-x day		Max使用时间
		-n day		Min使用时间
		-d 		删除用户密码
###	4.用户属性修改
		usermod [选项] <用户>
		-c comment	修改用户注释
		-g group	修改用户主组
		-G group	修改用户附加组
		-l name		修改用户账号名
		-L 		锁定用户
		-U		解锁用户
		-u UID		修改用户ID值
		-d home		修改用户主目录路径
		-p passwd	修改用户密码
###	5.显示当前用户
		whoami
	6.显示用户信息
		id [选项] <用户>
		-u		显示id
		-g		显示主群组id
		-G		显示附加群组id	
		
## 1.1.7使用命令管理用户组

###	1.创建用户组
		groupadd [选项] <用户>
		-g gid 		用户组id
		-r 		建立系统组
###	2.删除用户组
		groupdel <用户组名>	需要删除所有在内用户

###	3.修改用户组
		groupmod [选项] <用户>
		-g id 		修改用户组中添加用户
		-n name		用户组中删除用户
###	4.用户组成员添加/删除 
		gpasswd [选项] <用户>
		-a name		向用户组添加用户
		-d name		从用户组删除用户
###	5.用户组查询
		groups [用户名]
		groups userA	第一个为主组
## 1.1.8使用fdisk命令分区
	fdisk [选项] [磁盘设备文件]
	fdisk -l

	例题：
	在磁盘/dev/sdb 创建3分区，1扩展分区。（1区10GB，2,3分区8GB，其余为扩展分区）
###	1.执行分区命令
		fdisk /dev/sdb
###	2.查询帮助信息
		m
###	3.创建第1个主分区
		n
		p
		Enter
###	4.创建扩展分区
		n
		e
		Enter
###	5.显示分区信息
		p
###	6.结束创建分区
		w

```
	1.例题
	在扩展分区建立2逻辑分区，第1个逻辑分区8G，其余为第2个逻辑分区
	（1）执行分区命令
		fdisk /dev/sdb
	（2）创建第1个逻辑分区
		n
		Enter
	（3）创建第2个逻辑分区
		n
		Enter
	（4）显示分区结果
		p		
	（5）结束创建分区
		w
	2.例题
	删除第2逻辑分区
	（1）对指定磁盘/dev/sdb执行分区命令
		fdisk /dev/sdb
	（2）输入d 进入删除分区子命令
		d
	（3）输入要删除的分区代码
		6
	（4）显示分区信息
		p
	（5）保存当前分区信息并退出分区命令
		w
```