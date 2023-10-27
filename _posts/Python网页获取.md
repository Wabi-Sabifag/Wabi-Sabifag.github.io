---
title: Python数据分析
date: 2023-01-24 19:21:06
description: # 副标题
sticky:             #置顶
toc:                #显示文章TOC（默认为设置中toc的enable配置）
toc_number:         #显示toc_number（默认为设置中toc的number配置）
abbrlink: 997804fe
updated:                #页面更新日期
type: Python   #【必需】标签、分类和友情链接三个页面需要配置
tags: 
- Python #文章标签  
- 数据分析
categories: 
- Python       #文章分类
- 数据分析
keywords:   #页面关键词
cover: 'img/14.jpg'       #文章缩略图（如果没有设置top_img，文章页顶部将显示缩略图，可设为false/图片地址/留空）

comments:         #显示页面评论模块 默认 true
top_img:  'img/14.jpg'        #页面顶部图片
mathjax:            #显示mathjax（当设置mathjax的per_page： false时，才需要配置，默认 false）
katex:              #显示katex（当设置katex的per_page： false时，才需要配置，默认 false）
aside:              #显示侧边栏 （默认 true）
aplayer:            #在需要的页面加载aplayer的js和css，请参考文章下面的
highlight_shrink:       #配置代码框是否展开（true/false）
---

# Python数据分析与应用
## 1.前置工作
### 1.部署环境
#### 1. python环境
#### 2. jupyter notebook编译器
        1. 在cmd命令行下载 jupyternotebook
            ```
                pip install jupyter -i https://pypi.tuna.tsinghua.edu.cn/simple
            ```
        2.进入jupyter notebook页面
            jupyter是Python自带的多语言编译工具。
            通过浏览器方式在本地进行编译工作。
            PS：在浏览器运行工作时，不能关闭cmd命令行。
                cmd命令行作为服务器功能支撑jupyternotebook实现运行。
#### 3.Markdown
    Markdown是一门使用普通文本编辑器编写的标记语言。
##### 1.标题
    '#' 可以控制标题字体大小，共 6 级。
##### 2.列表
    排序功能:
        1.有序排序
            1.
            2.
        2.无序排序
            -
            *
            -
##### 3.字体
    文档中文字突出部分内容，使用加粗或斜体格式，是的部分功能醒目。
    通常使用的符号：
        加粗：'*' 
        斜体：'_' 
##### 4.表格
    Markdown绘制表格。
    列：
        python | R | MATLAB |
        --------|--------|-----|
        接口统一 | 接口众多 | 自由度打 |

    解释：
        第一行为表头
        第二行分隔表头和主题部分
        第三部分开始，每一行代表一个表格。

        列与列间用 '|' 分隔开，每一行结尾也必须 '|'符号隔开。
##### 5.数学公式编辑
    LaTex 是写科研论文的必备工具之一，课题插入数学公式。
    1. 在文本中插入数学公式前，应使用 '$ ... $'。
    列：
        质能方程的LeTex表达式为: ‘SE = mc^2$' .
    
    2. 如果插入一个数学区块，应使用 '$$ ... $$'.
    列：
        $$z=\frac{x}{y}$$     ===>>       z = x / y

#### 导出功能
    在UI界面，可以导出多种格式文件。
### 2.Python数据分析常用库
#### 1.NumPy (维度称为轴）
NumPy是Numerical Python缩写，Python科学计算机的基础库。
主要内容：
    1. 快速高效的多维数组对象 —————— ndarray。
    2. 对数组进行元素级计算 和 直接对数组进行数学运算的函数。
    3. 读写硬盘上基于数组的数组的数据集的工具。
    4. 线性代数运算，傅里叶变换和随机数生成等功能。
    5. 将C，C++,Fortran代码集成到Python项目的工具。
除快速处理数组处理能力外，作为算法之间传递数据的容器。
在Python内部效率高于其他数据结构，在低级（其他）语言中可以直接操作数组中的数据。

##### Python提供的array和list不同，array直接保存数值，和C语言的一维数组类似，但不支持多维数组，也无各种运算函数，不适合数值运算。

#### 1.创建数组对象
    NumPy提供两种基本的对象：
        ndarray(N-dimensional Array):存储单一数据类型的多维数组。
        ufunc(Universal Function):对数组进行处理的函数。 
##### 1.数组属性
1. ndim: 返回int。 表示数组的维数。
2. shape: 返回tuple。  表示数组的形状，对于n行m列的矩阵，形状为（n,m)。
3. size: 返回int。  表示数组的元素的总数，等于数组的形状中个元素的积。
4. dtype： 返回date-type。  表示数组中元素的数据类型。
5. itemsize： 返回int。 
##### 2.数组创建
NumPy库
import numpy as np

1. arange()
    start
    stop
    step
    dtype


NumPy提供的array函数可以创建一维数组或多维数组。
格式：
```
numpy.array(object,dtype=None,*,copy=True,order='K',subok=False,ndmin=0,like=None)
```
说明表：
1. object 接受 array_like.  表示所需创建的数组对象。无默认值
2. dtype 接受data_type.  表示数组所需的数据类型，如果未给定，选择保存对象所需的最小的数据类型。默认为 None
3. ndmin 接受int。  用于指定生成数组应该具有的最小维数。默认 0 
###### 1. 创建数组并查看数组属性
```
import numpy as np #导入NumPy库
arr1 = np.array([[1,2,3,4],[2,3,4,5],[3,4,5,6]]) #创建一维数组 
print('创建的数组为:\n',arr1) 
```
创建的数组为:
 [[1 2 3 4]
 [2 3 4 5]
 [3 4 5 6]]

```
print('数组形状为：',arr1.shape) #查看数组形状
```
数组形状为： (3, 4)

```
print('数组元素类型为：',arr1.dtype) #查看数组元素类型
```
数组元素类型为： int32

```
print('数组元素个数：',arr1.size) #查看数组元素个数
```
数组元素个数： 12

```
print('数组每个元素存储空间为：',arr1.itemsize) #查看数组每一个元素的存储空间
```
数组每个元素存储空间为： 4

###### 2.重新设置数组的shape属性
```
arr1.shape = 4,3  #车厢内设置shape
print('重新设置shape后的arr1为：\n',arr1)
```
重新设置shape后的arr1为：
 [[1 2 3]
 [4 2 3]
 [4 5 3]
 [4 5 6]]
###### Arange
    除了array函数创建数组之外，还可以用arange函数创建数组。
    arange函数类似Python自带的range，通过指定通过指定开始值，终值和步长来创建一维数组，创建的数组不包含终值。
格式：
```
numpy.arange([start,]stop,[step,]dtype=None,*,like=Node)
```
说明表：
1. start int                表示数组的开始值，生成的数组包括该值
2. stop  int                表示数值的终值，生成的数组不包括该值。无默认
3. step  int                表示在数组中，值之间的步长。默认1
4. dtype 接受数据类型        表示输出数值的类型。默认为None
###### 3.使用arange函数创建数组     
```
print('使用arange函数创建的数组为：\n',np.arange(0,1,0.1))
```
使用arange函数创建的数组为：
 [0. 0.1 0.2 0.3 0.4 0.5 0.6 0.7 0.8 0.9]


2.linspace()      //等比数列
    start
    stop
    num
    dtype

    linspace函数通过指定开始值，终值和元素个数来创建一维数组，默认包括终值（和arange的区别）
格式:
```
numpy.linspace(start,stop,num=50,endpoint=True,retstep=False,dtype=None,axis=0)
```
说明表：
1. start 
2. stop
3. num    int                   表示生成的样本数。 默认为50
4. dtype  接受数据类型           表示输出数值的类型。默认为None
###### 4.使用linspace函数创建数组
```
print('使用linspace函数创建的数值为：\n',np.linspace(0,1,12))
```
使用linspace函数创建的数值为：
 [0.         0.09090909 0.18181818 0.27272727 0.36363636 0.45454545
 0.54545455 0.63636364 0.72727273 0.81818182 0.90909091 1]    
3.logspace(,,)

4.zeros((,))     // 二维 行列
5.ones()
6.eye()        //行列  对角 1
7.diag()       //二维 数组==>>行列
8.full( (,), )   //行列 填充
  full_like( array,3 )
  
##### 数组数据类型
bool
inti
int8
int16
int32
int64
uint8
uint16
uint32
uint64
float16
float32
float64/float
complex64          //复数
complex128/complex

##### 生成随机数
1.random
  np.random()
 1.seed
 2.permutation
 3.shuffle
 4.binomial
 5.normal
 6.beta
 7.chisquare
 8.gamma
 9.uniform
 10.sample
      用什么当为样本，生成类似的数据
  
2.rand        //生成服从均匀分布的随机数
     numpy.random.randint(low,high=None,size=None,dtype=int)
  列：
       np.random.rand(2,3) 
       array([[0.38786527, 0.22297469, 0.88171169],
       [0.75717494, 0.8715018 , 0.888392  ]])
    列：
        np.random.randint(10,size=(3,5))  //生成随机数  size规定行列
        array([[1, 8, 5, 6, 3],
            [8, 9, 1, 7, 7],
            [8, 9, 6, 0, 3]])
3.randn      //生成服从正态分布的随机数

##### 通过索引访问数组
1.np.repeat(b,1,axis=0)       //数组 维度 行列排序 

一维数组索引
    1.arange[3:5]
    2.arange[:5]
    3.arange[2:4]=100,101
    4.arr[1:-1:2]          // 第三个 步长
    5.arr[5;1：-1]         // 步长为负数时，开始索引大于结束
多维数组索引
    1.arr[0,3:5]
    2.arr[1:,2:]          // 第二组开始 的 每行第三数据遍历
    3.arr[:,2]           // 每组的第三数据
整数序列索引和布尔值索引访问多维数组
    1.arr[[(0,1,2),(1,2,3)]]  // n组的第n个数据
    2.arr[1:,(0,2,3)]       // 第二数组开始，地标数据
    3.   mask=np.array([1,0,1],dtype=np.bool)    
        // mask是一个布尔数组 用它索引第0，2行中第2列的元素
        arr[mask,2]         //  [3,9]
变换数组的形态
np.reshape(a,newsahpe,order='c')
    1.a        //需要变换形状的数组
    2.newshape   //变换后的形态
1.arr.reshape(3.4)
2.ravel        //展平
3.flatten/flatten('F')     // 横向展平 纵向展平
3.hstack/vstack(arr1,arr2)  // 矩阵横向贴合/纵向贴合
4.concatenate((arr1,arr2),axis=1/0)  // 矩阵横向贴合/纵向贴合
5.hsplit/vsplit
   列：
     arr=np.arrage(16).reshape(4,4)
     np.hsplit(arr,2)        //横向/纵向分割成 2 个数组在同一个集合
6.split(arr,2,axis=1/0)     //横向(整块)/纵向(多块)切割数据

##### Numpy矩阵和通用函数
###### 1.创建矩阵
import numpy as np

1.mat('1,2,3;4,5,6;7,8,9')
2.matrix([[1,2,3],[4,5,6],[7,8,9]])
3.bmat('arr1,arr2;arr1,arr2')        //数据贴合

###### 2.矩阵运算
1.矩阵和数相乘
2.矩阵相加
3.矩阵相减
4.矩阵相乘
    a矩阵的横数组与b矩阵的纵数组单位相乘的个个和为c矩阵的点数据
###### 3.查看矩阵属性
1.arr.T    //转置矩阵         每行的数据颠倒数据顺序
2.arr.H   //共轭转置矩阵       每行的同角标数据归置同行数据
3.arr.I   //逆矩阵           
4.arr.A   //二维数组的视图      
     

##### ufunc函数 （对所有元素进行操作的函数
###### 1.四则运算
    arr数据组
###### 2.比较运算

###### 3.逻辑运算
1. np.all(x==y)
	用于测试所有的数组元素是否为真
2. np.any(x==y)
	用于测试任何元素是否为真


###### 4.ufunc函数的广播机制
	计算前提：数组形状一致。
	四原则：
	1. 让所有的输入的数组向其中最长的shape数组看齐，如数组的shape不足，在前面加 1 补齐
	2.输出数组的shape是输入数组shape在各个轴上的最大值的组合。
	3.数组输入长度的某个轴的长度和输出的长度或输出数组的对应轴的长度相同，或输入数组的某个轴的长度为1，那么这个数组能够用于计算。
	4.当输入数组的某个长度为1，将使此轴上的第一组值进行运算。


###### 5.利用NumPy进行统计分析
1. 读/写文件
	numpy.save(file,arr,allow_pickle=true,fix_imports=true)

(1) 存入文件	
```
import numpy as np
arr=np.arange(100).reshape(10,10)  # 创建数组
np.save('../arr',arr) # 保存数组    可保存多个数组
arr
```
(2) 读取文件
```
# 单个文件读取
loaded_data=np.load('../arr.npy')
# 多个文件读取
loaded_data=np.load('../arr.npz')
loaded_data['arr_0']
```

2. 文本读取格式
(1) savetxt
	numpy.savetxt(fname,X,fmt='%.18e',delimiter='',newline='\n',header='',
footer='',commentd='#',encoding=None)

	fname:文件名，接受Str
	X：数据组，接受array_like
	delimiter;表示数据分割符，接受str
(2).loadtxt
	numpy.loadtxt(fname,dtype=<class 'float'>,comments='#',delimiter=None,converters=None,skiprows=0,usecols=None,unpack=Flase,ndimn=0,encoding='bytes',max_rows=None,*,like=None)

(3).genfromtxt
	类似于loadtxt,面向结构化数据和缺失数据。

######  6.使用函数进行简单的统计分析
除使用通用函数对数进行比较、逻辑等运算，还可以使用统计函数对数组进行排序、去重与重复、求最值、平均值等统计分析。
1. 排序
(1)直接排序(sort)
直接排序：arr.sort()
横轴排序：arr.sort(axis=1)
竖轴排序：arr.sort(axis=0)
解释：对数值直接排序
(2)简介排序(argsort、lexsort)
排序索引排序：arr.argsort()
多个键数组排序：np.lexsort((a,b,c))     # 多个键排序的顺序按照最后一个传入的键顺序排序数据
解释：对多个键数据集进行排序

2. 去重与重复
(1)去重
np.unique(array)
(2)重复
np.tile(A,reps)      # 输入的数组(array):A    数组重复的次数:reps
np.repeat(a,repeats,axis=None)         # 输入的数组:a  数组重复的次数:repeats  复制的方向: 0/1

3. 常用的统计函数
(1)聚合计算
解释：直接显示结果
计算数组的和：np.sum()
沿纵轴求和：np.sum(axis=0)
沿横轴求和：np.sum(axis=1)

计算数组均值：np.mean()
沿纵轴计算数组均值：np.mean(axis=0)
沿横轴计算数组均值：np.mean(axis=1)

计算数组标准差：np.std()
计算数组方差：np.var()

计算数组最小值：np.min()
计算数组最大值：np.max()
返回数组最小值索引：np.argmin()
返回数组最大值索引：np.argmax()
(2)非聚合计算
解释：产生一个中间结果组成的数组
计算元素的累计和：np.cumsum()
计算元素的累计积少：np.cumprod()

#### 2.SciPy
    SciPy是基于Python开源库，解决科学计算中各种标准问题的8个模板的集合。
    主要内容：
        1. scipy.integrate：数值积分和微方程求解器
        2. scipy.linalg：扩展了由numpy.linalg提供的线性代数求解和矩阵分解功能
        3. scipy.optimize：函数优化器（最小化器）以及跟查找算法
        4. scipy.signal：信号处理工具
        5. scipy.sparse：稀疏矩阵和稀疏性系统求解器
        6. scipy.special：SPECFUN[实现许多常用数字函数的Fortran库]的包装器
        7. scipy.stats：包含检验连续和离散概率分布(密度函数，采样器，连续分布函数等)的函数与方法，各种统计检验的函数与方法，以及各类描述性统计函数的函数方法，
#### 3.pandas
    pandas是Python的数据分析核心库。提供复杂精细的索引功能，以便完成重塑，切片，切块，聚合和选取数子集等操作。
    统计分析除了包含单一数值型特征的数据集中趋势、离散趋势和峰度与偏度统计知识外、还有包含多个特征间的比较计算等知识。
#### 4.Matplotlib
    Matplotlib是较为流行的绘制数据图表的Python库。
#### 5.seaborn
    seaborn是基于Matplotlib的数据可视化Python库，提供高度交互的界面。
    兼容NumPy，pandas的数据结构以及Scipy和stats models等统计模式。
#### 6.pyecharts
    Echarts是百度开源的数据可视化工具，凭借良好的交互性，精巧的图表设计。
#### 7.scikit-learn
    scikit-learn是简单有效的数据挖取和分析工具。
    主要内容(基本模块)：
        1.数据预处理
        2.模型选择
        3.分类
        4.聚类
        5.数据降维
        6.回归  

# Python 的网络资源获取

## 1.准备工作
编辑器：PyCharm  
库：requests BeautifulSoup4 
###
```
1.requests 网页下载库

    requests.get/post(url,params,data,headers,timeout,verify,allow_redirects,cookies)

url：下载的网页目标url
params：字典形式，设置URL后面的参数，比如？id=123&name=bilibili
data：字典或字符串，一般用于POST方法时提交数据
headers：设置user-agent，refer请求头
timeout：超时时间，s
verify:True/False，是否进行HTTPS证书验证
allow_redirects:True/False是否让requests做重定向处理
cookies:附带本地cookies数据

2.接收response响应

    r = requests.get/post(url)

    r.status_code       网页状态

    r.encoding      设置编码规则

    r.text      网页内容

    r.headers       

    r.url

    r.content       字节形式返回

    r.cookies       导入本地cookies

3.网页解析器 

 1.创建BeautifulSoup对象
    from bs4 import BeautifulSoup
    #根据HTML网页字符串创建 BeautifulSoup 对象
    soup = beautifulSoup(
        html_doc,                   
            #HTML文档字符串
        'html.parser',              
            #HTML解析器
        from_encoding='utf8         
            #HTML文档编码
    )
 2.搜索节点 (find_all,find)
    find_all(name,attrs,string)
    比如：
        soup.find_all('div',class_='abc,string'Python',href='/view/123.html')
            #查找所有为 div标签 ，class为abc，文字为Python，连接符合/view/123.html的节点
 3.访问节点信息
    node.name   #标签名字
    node['href']  # 元素属性
    node.get_text()     #查找到的节点的链接文字
```
## 2.网页
```
import requests
from bs4 import BeautifulSoup
import selectors
class UrlManager():
    '''
    Url管理器
    '''
    def __init__(self):
        self.new_urls = set()
        self.old_urls = set()

    def add_new_url(self,url):
        if url is None or len(url) == 0:
            return
        if url in self.new_urls or url in self.old_urls:
            return
        self.new_urls.add(url)

    def add_new_urls(self,urls):
        if urls is None or len(urls) == 0:
            return
        for url in urls:
            self.add_new_url(url)

    def get_url(self):
        if self.has_new_url():
            url = self.new_urls.pop()
            self.old_urls.add(url)
            return url
        else:
            return None

    def has_new_url(self):
        return len(self.new_urls) > 0

#---------------------------------------------

if __name__ == "__main__":
    url_manager = UrlManager()
    url_manager.add_new_url("url1")
    url_manager.add_new_url("url2")
    url_manager.add_new_url("url3")
    print(url_manager.new_urls,url_manager.old_urls)

    print("#"*30)

    new_url = url_manager.get_url()
    print(url_manager.new_urls, url_manager.old_urls)

    print("#" * 30)

    new_url = url_manager.get_url()
    print(url_manager.new_urls, url_manager.old_urls)

    print("-"*30)

    print(url_manager.has_new_url())
    print(new_url)

```

## 3.获取页面文本内容
```
import requests
from bs4 import BeautifulSoup
import selectors

url = "https://www.wabisabifag.top/"
r = requests.get(url)
print(f'{r.status_code}\n '
      # f'{r.headers}\n '
      f'{r.encoding}\n')
for (index,value) in enumerate(r.text):
    print(value,end='')
    if 0 == index%120: print()
```

## 4.获取网页标签内容
```
import  requests
from bs4 import  BeautifulSoup

def get_novel_chapters():
    root_url = "http://www.89wxw.cn/0_9/"      # 网页无效了
    r = requests.get(root_url)
    r.encoding="gbk"
    soup = BeautifulSoup(r.text,"html.parser")
    for dd in soup.find_all("dd"):
        link = dd.find("a")
        if not link:
            continue

        print(link)

get_novel_chapters()

```

## 5.正则表达式
```
url1 = "http://www.bilibili.com"
url2 = "http://www.bilibili.com/123.html#comments"
url3 = "http://www.baidu.com"
import  re
pattern = r'^http://www.bilibili.com$'
print(re.match(pattern,url1)) #ok
print(re.match(pattern,url2))
print(re.match(pattern,url3))
```

## 6.验证网页是否有效并导入本地
```
from utils import url_manager
from bs4 import BeautifulSoup
import requests
import re

root_url = "https://www.bilibili.com/"

urls = url_manager.UrlManager()
urls.add_new_url(root_url)

fout = open("craw_all_pages.txt", "w")
while urls.has_new_url():
    curr_url = urls.get_url()
    r = requests.get(curr_url, timeout=10)
    if r.status_code!= 200:
        print("error.retrun status_code is over 200", curr_url)
        continue
    soup = BeautifulSoup(r.text, "html.parser")
    title = soup.title.string

    fout.write("%s\t%s\n" % (curr_url, title))
    fout.flush()
    print("成功:%s,%s,%d" % (curr_url, title, len(urls.new_urls)))

    links = soup.find_all("a")
    for link in links:
        href = link["href"]
        pattern = r'^https://www.bilibili.com/\d+.html$'
        if re.match(pattern, href):
            urls.add_new_url()
fout.close()

```

## 7.获取豆瓣页面网址
```
from turtle import pd
import requests
from bs4 import BeautifulSoup
import pprint
import json
import pdb

# 构造分页数字列表
page_indexs = range(0, 250, 25)
list(page_indexs)


def download_all_htmls():  # 获取HTML的page信息
    htmls = []
    for idx in page_indexs:
        print(idx)
        url = f"https://movie.douban.com/top250?start={idx}&filter="
        print("craw html:", url)
        r = requests.get(url)
        # if r.status_code != 200:
        #     raise Exception("error")
        htmls.append(r.text)
    return htmls

htmls = download_all_htmls()

# 解析数据
def parse_single_html(html):
    soup = BeautifulSoup(html, "html.parser")
    article_items = (
        soup.find("div", class_="article")
        .find("ol", class_="grid_view")
        .find_all("div", class_="item")
    )
    datas = []
    for article_item in article_items:
        rank = article_item.find("div", class_="pic").find("em").get_text()
        info = article_item.find("div", class_="info")
        title = info.find("div", class_="hd").find("span", class_="title").get_text()
        # print(title)
        stars = (
            info.find("div", class_="bd")
            .find("div", class_="star")
            .find_all("span")
        )
        rating_star = stars[0]["class"][0]
        rating_num = stars[1].get_text()
        comments = stars[3].get_text()

        datas.append({
            "rank": rank,
            "title": title,
            "rating_star": rating_star.replace("rating", "").replace("-t", ""),
            "rating_num": rating_num,
            "comments": comments.replace("评价人数:", "")
        })
    return datas

pprint.pprint(parse_single_html(htmls[0]))

all_datas = []
for html in htmls:
    all_datas.extend(parse_single_html((html)))

print(all_datas)
print(len(all_datas))


#导入表格
df =pd.DataFrame(all_datas)
print(df)
df.to_eccel("豆瓣电影TOP250.xlsx")
```
    31，59有报错没有修改，可能是获取标签问题，也可能是代码自生的错误。
报错：Traceback (most recent call last):
  File "C:\Users\WabiSabifag\PycharmProjects\web_crawler\douban_test\goline.py", line 59, in <module>
    pprint.pprint(parse_single_html(htmls[0]))
  File "C:\Users\WabiSabifag\PycharmProjects\web_crawler\douban_test\goline.py", line 31, in parse_single_html
    soup.find("div", class_="article")
AttributeError: 'NoneType' object has no attribute 'find'

```
#封装
import requests
from bs4 import BeautifulSoup
import pprint
import json

from douban_test.goline import download_all_htmls,parse_single_html

htmls = download_all_htmls()
for i in  range(len(htmls[0])):
    print(i)

pprint.pprint(parse_single_html(htmls[0]))

all_datas = []
for html in htmls:
    all_datas.extend(parse_single_html((html)))

```

## 8.网页图片获取
```
coding = 'utf-8'
import requests
from bs4 import BeautifulSoup
import os
url = "https://pic.netbian.com/4kmeinv/"

def craw_html(url):
    resp = requests.get(url)
    resp.encoding = 'gbk'
    print(f"获取网页状态:{resp.status_code}")
    html = resp.text        #得到页面
    return  html

def parse_and_download(html):
    soup = BeautifulSoup(html, "html.parser")
    imgs = soup.find_all("img")
    for img in imgs:
        src = img['src']
        if '/uploads/' not in src:
            continue
        src = f"https://pic.netbian.com{src}"

        filename = os.path.basename(src)
        with open(f"img/{filename}", "wb") as f:
            resp_img = requests.get(src)
            f.write(resp_img.content)

# 如果页面有规律  循环获取页面
urls = ["https://pic.netbian.com/4kmeinv/"]+[
    f"https://pic.netbian.com/4kmeinv/index_{i}.html"
    for i in range(2,4)]
for url in urls:
    html = craw_html(url)
    parse_and_download(html)
```

# 本地图片文件的重命名
```
# coding=utf-8
import os
path_name = os.path.join(os.getcwd(), r'C:\Users\11111\Desktop\1')
'''
 获取图片所在文件夹的地址
 可修改为文件的相对路径，比如： 
 path_name = D:\Documents\GitHub\my_OpenCV\models-master\research\my_data\myimages)
'''
num = 3323 # 图片命名的序号（从num开始）
for item in os.listdir(path_name):#进入到文件夹内，对每个文件进行循环遍历
    #re_name=str(num)+'.jpg'
    re_name = '图片_'+str(num)+'.jpg' # 重命名图片文件的格式（从num开始）
    os.rename(os.path.join(path_name,item),os.path.join(path_name,re_name))
    num+=1
```

# Image库——图片字符化
```
# coding=utf-8
from PIL import Image

# 生成图像所要的字符集
codeLib = ''' `1234567890-=~!@#$%^&*()_+qwertyuiop[]\QWERTYUIOP{}|asdfghjkl;'ASDFGHJKL:"zxcvbnm,./ZXCVBNM<>?'''
count = len(codeLib)
print(count)
print(int(0.5))

# 将彩色图片转换为黑白图片， 然后像素点的灰度值和字符集建立映射
def transforml(image_file):
    # 转换为黑白图片，参数”L“表示黑白模式
    image_file=image_file.convert("L")
    codePic = ''
                    #  size 属性表示图片的分辨率，‘0’为横向大小，‘1’为纵向
    for h in range(0,image_file.size[1]):
        for v in range(0,image_file.size[0]):
                    # 返回指定位置的像素值，如果打开的图象是多层次的图片，那这个方
            gray = image_file.getpixel((v,h))
            print(gray)
            # 建立灰度和字符集的映射
            codePic = codePic + codeLib[int(((count-1)*gray)/256)]

        codePic = codePic+'\r\n'
    return codePic

# 打开图片
fp = open('1.jpg','rb')
image_file = Image.open(fp)
# 调整图片大小
image_file = image_file.resize((int(image_file.size[0]*0.5),int(image_file.size[1]*0.25)))

print(u'Info:',image_file.size[0],' ',image_file.size[1],' ',count)

# 打开 txt 文件写入字符
tmp = open('index.txt','v')
tmp.write(transforml((image_file)))
tmp.close()
```