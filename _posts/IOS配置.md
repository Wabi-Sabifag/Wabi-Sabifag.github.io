---
title: IOS配置
date: 2023-01-02 19:28:15
description:  # 副标题
sticky:             #置顶
toc:                #显示文章TOC（默认为设置中toc的enable配置）
toc_number:         #显示toc_number（默认为设置中toc的number配置）
abbrlink: 997804fe
updated:                #页面更新日期
type: JavaScript   #【必需】标签、分类和友情链接三个页面需要配置
tags: 
- 网络运维
- 基础
categories: 
- 网络运维      #文章分类
- 基础
keywords:   #页面关键词
cover:  'img/5.jpg'     #文章缩略图（如果没有设置top_img，文章页顶部将显示缩略图，可设为false/图片地址/留空）

comments:         #显示页面评论模块 默认 true
top_img: 'img/5.jpg'       #页面顶部图片
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
##  一、路由器配置
### 客户机配置  
#### R1配置
```
no
enable 
conf ter 
hostname R1
inter g0/0
no shutdown 
ip add 192.168.10.1 255.255.255.0
inter g0/1
ip add 192.168.30.1 255.255.255.0
no shutdown 
exit
route rip
version 2
network 192.168.10.0
network 192.168.30.0
```
#### R2配置
```
no
enable 
conf ter 
hostname R2
inter g0/0
no shutdown 
ip add 192.168.20.1 255.255.255.0
inter g0/1
ip add 192.168.30.1 255.255.255.0
no shutdown 
exit
route rip
version 2
network 192.168.20.0
network 192.168.30.0 
```
## 二、交换机初始化
### 配置虚拟终端登录（全局配置）
```
enable secret PASSWORD
line vty 0 4
password 123
login 
enable secret PASSWORD
```

### 1.MS1配置
```
enable 
conf ter 
hostname MS1
vlan 10
name test10
exit
vlan 20
name test20
exit
interface vlan 10
ip add IP_ADDR
interface vlan 20 
ip add IP_ADD
inter fa0/1
switchport mode access
switchport access vlan 10
inter fa0/2
switchport mode access
switchport access vlan 20
exit
ip routing 
```

### 2.设置主机IP地址及网关地址（涉及到多个网络即多个不同的局域网）

### 3.路由器设备

#### R1配置
```
enbale
conf ter 
hostname R1
inter g0/0
no shutdown
ip add 192.168.3.1 255.255.255.0
inter g0/1
no shutdown
ip add 192.168.1.1 255.255.255.0
exit
route rip
version 2
network 192.168.1.0
network 192.168.3.0
```
#### R2配置
```
enbale
conf ter 
hostname R2
inter g0/0
no shutdown
ip add 192.168.3.2 255.255.255.0
inter g0/1
no shutdown
ip add 192.168.2.1 255.255.255.0
exit
route rip
version 2
network 192.168.2.0
network 192.168.3.0 
```

## IP地址计算

### 给定IP地址: 192.55.12.120      子网掩码:255.255.255.240

### 第一题:求子网号

#### 第一步,将IP地址,子网掩码的十进制地址转换为二进制
        (PS: 网络地址 的 1 和 255 为特殊位被保留,所以有效计算的数为 254个)
                                                   
    最后8位分开,是因为C类网址(可以从子网掩码最后四位的 1111 0000 做理解)
    最后四位做主机号,以作区别.
```
192.55.12.120        11000000  00110111  00001100  0111 1000 
255.255.255.240      11111111  11111111  11111111  1111 0000
```
#### 第二步,进行二进制个个位数的逐步 比较( A=B?1:0 )
(PS:最后四位为主机号,不需要对比 因此为 0000)
```                                                    
                     11000000  00110111  00001100  0111 0000
                     192.55.12.112
```                      
### 第二题:求主机号

#### 由IP地址做十进制转换为二进制
```
192.55.12.120        11000000  00110111  00001100  0111 1000
```
将主机号分到的位数(子网掩码没有占用的段落 再转换为十进制 就是该主机在本地址的主机号)

可得主机号:0.0.0.8

### 第三题:直接广播地址

直接广播地址(解释:有效的网络号 + 全为1 的主机号)
 
因此,由题目做给的IP地址,结合第一题信息                        (主机号)
```
    192.55.12.120  ==>   11000000  00110111  00001100  0111 1000                                    
```                                                       
可得                                                      (主机号转变为) 
```
    192.55.12.127   <==   11000000  00110111  00001100  0111 1111
```
### 第四题:如果主机地址的头十位用于子网,那么184.231.138.239的子网屏蔽码是多少

由题可知
为B类网址(16+16)
```
                    转换
184.231.138.239     ==>    10111000  11100111  10001010  11 101111
```
因为 主机的头十位用于子网 (解释:主机号的16中,前十位被子网占用)
所以 子网掩码如下:
```
                    转换
255.255.255.192     <==    11111111  11111111  11111111  11 000000
```
### 第五题:如果子网屏蔽码是  255.255.192.0,

那么不需要经由路由器通信和主机129.23.144.16的是哪一类

网络号相同的主机可以直接相连,不同的主机通过路由器相连.
### 主机:
```
129.23.144.16         10000001  00010111  10010000  00010000
```
### 子网掩码:
```
255.255.192.0         11111111  11111111  11000000  00000000
```
从子网掩码可知,将主机号的前两位占用
 
所以在此将主机显示时,如下就可以明显的观察区别:
```
129.23.144.16         10000001  00010111  10 010000  00010000
```
### 可得信息:
当第三字节 前两位 被占用得主机号 
以 10 ~ 11 (范围在128`192,不包括192)开头的数值范围,可以相互通信.
 