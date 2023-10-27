---
title: SoftWareTest
date: 2023-03-01 09:40:17
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
cover: 'img/15.jpg'       #文章缩略图（如果没有设置top_img，文章页顶部将显示缩略图，可设为false/图片地址/留空）

comments:         #显示页面评论模块 默认 true
top_img:  'img/15.jpg'        #页面顶部图片
mathjax:            #显示mathjax（当设置mathjax的per_page： false时，才需要配置，默认 false）
katex:              #显示katex（当设置katex的per_page： false时，才需要配置，默认 false）
aside:              #显示侧边栏 （默认 true）
aplayer:            #在需要的页面加载aplayer的js和css，请参考文章下面的
highlight_shrink:       #配置代码框是否展开（true/false）
---
# Selenium自动化测试

## 1.实例

### 1. 初步认识Selenium
```    
#1 导入webdriver
from selenium import webdriver          

from selenium.webdriver.chrome.options import Options

from selenium.webdriver.common.by import By

#  鼠标事件对象
from selenium.webdriver.common.action_chains import ActionChains
#   键盘事件对象
from selenium.webdriver.common.keys import Keys


options = Options()
options.add_experimental_option('detach',True)

#2. 打开谷歌
driver=webdriver.Chrome(options=options)      

#3. 谷歌.中打开链接
driver.get("https://www.baidu.com")     

#4. 向搜索框输入 java
driver.find_element(By.ID,"kw").send_keys("java")   
driver.implicitly_wait(1)

#5. 点击搜索按钮
driver.find_element(By.XPATH,'//input[@type="submit"]').click()     
driver.implicitly_wait(2)  


# 6. 将driver 对象绑定 鼠标执行事件
test = ActionChains(driver)

clearText = driver.find_element(By.XPATH,'//*[@id="form"]/span[1]/i[1]')
refullText = driver.find_element(By.ID,"kw")

#7.  perform()  执行代码
test.click(clearText).perform()
driver.implicitly_wait(2)

test.click(refullText).click().send_keys("Bilibili").perform()
driver.implicitly_wait(2)

 #8.  关闭。退出浏览器
 driver.quit()  
```
### 2. 适用Selenium 基础功能
```
from  time import sleep
from selenium import  webdriver
from selenium.webdriver.common.by import By
'''
TODO: Let`s driver stay work, didn`t auto colse
'''
from selenium.webdriver.chrome.options import Options
options = Options()
options.add_experimental_option('detach',True)
driver=webdriver.Chrome(options=options)

driver.get("https://www.baidu.com")

driver.find_element(By.ID,"kw").send_keys("i.chaoxing.com")
driver.implicitly_wait(1)

driver.find_element(By.XPATH,'//input[@type="submit"]').click()
driver.implicitly_wait(2)

'''
TODO: Useing JavaScript Language execute driver
'''
# let Webpage scroll down
# js = "window.scrollTo(600,300)"
# driver.execute_script(js)

driver.find_element(By.XPATH,'//*[@id="1"]/div/div[1]/h3/a').click()
driver.implicitly_wait(1)

# jump to a new webPage
handles = driver.window_handles
driver.switch_to.window(handles[-1])
driver.implicitly_wait(1)

# Now click in the Chaoxing Web
driver.find_element(By.ID,"phone").send_keys('123456')
driver.implicitly_wait(1)
driver.find_element(By.ID,"pwd").send_keys('123456')
driver.implicitly_wait(1)
driver.find_element(By.ID,'loginBtn').click()
driver.implicitly_wait(1)

driver.find_element(By.NAME,"笔记").click()
driver.implicitly_wait(1)

driver.back()
driver.implicitly_wait(1)

driver.forward()
driver.implicitly_wait(1)

driver.refresh()
driver.implicitly_wait(1)


'''
TODO: Update webpage place
'''
handles = driver.window_handles
driver.switch_to.window(handles[-1])
driver.implicitly_wait(1)


driver.maximize_window()
driver.implicitly_wait(1)

driver.find_element(By.NAME,"课程").click()
driver.implicitly_wait(1)

'''
TODO: iframe  框架   
    switch_to.frame("IDName")  to differ
'''
driver.switch_to.frame("frame_content")

driver.find_element(By.XPATH,"//*[@id='addCourse']").click()
sleep(2)

# Form js factory scrollTop and scrollDown
js = "var js = document.documentElement.scrollTotop=1000"
driver.execute_script(js)
sleep(2)

js = "var js = document.documentElement.scrollTotop=0"
driver.execute_script(js)
sleep(2)

driver.close()
```
### 3. 进阶Selenium 本地文件导入
```
import time
from selenium.webdriver.chrome.options import Options
from selenium import  webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.action_chains import ActionChains
from selenium.webdriver.common.keys import Keys
import unittest

class sendQQMail(unittest.TestCase):
    def setUp(self):
        options = Options()
        options.add_experimental_option('detach', True)
        driver = webdriver.Chrome(options=options)
        
        driver.get("https://mail.qq.com")
        test = ActionChains(driver)
        driver.implicitly_wait(25)

    def Test_sendQQMail(self):
        # 点击写信
        self.driver.find_element(By.ID, "composebtn").click()
        self.driver.implicitly_wait(2)

        # TODO:iframe  框架
        self.driver.switch_to.frame("mainFrame")
        self.driver.implicitly_wait(2)

        # input 按钮
        '''输入信息'''
        t = self.driver.find_element(By.XPATH, '//*[@id="toAreaCtrl"]/div[2]/input')
        self.driver.implicitly_wait(2)
        t.send_keys("1109388794@qq.com")
        self.driver.implicitly_wait(2)
        print("写入收信信息完成")

        # 导入本地文件
        tt = self.driver.find_element(By.XPATH, '//*[@id="AttachFrame"]/span/input')
        self.driver.implicitly_wait(2)
        
        ''' 
        通过Driver驱动的鼠标事件绑定,
        send_keys方法,
        r'': 导入本地文件路径，注意格式
        '''
        self.test.send_keys(r'D:\爱德华·艾力克.txt')
        print("写入本地文件完成")
        self.driver.implicitly_wait(2)

        self.driver.find_element(By.XPATH, '//*[@id="toolbar"]/div/a[1]').click()
        print("发生完成")
        time.sleep(10)

    def tearDown(self):
        self.driver.quit()
        print('========== End ==========')

# 该文件名称下，直接调用unittest下的test
if __name__ == '__test__':
    unittest.test()

```
### 4. 进阶Selenium 数据驱动:动态填入数据
```
import csv
import time
from selenium import webdriver
import unittest
from selenium.webdriver.common.by import By
from selenium.webdriver.chrome.options import Options

#  数据驱动
from ddt import ddt,data,unpack

#  方法: 获取文件 UserData.csv
def get_Data(file_Name):   # open the CSV
    rows = []
    data_file = open(file_Name,"r",encoding="utf-8")
    reader = csv.reader(data_file)
    next(reader,None)
    for row in reader:
        rows.append(row)
    return rows

#  方法: 实现页面自动化登录
def ActualResult(driver,username,password):
    # Now click in the Chaoxing Web
    driver.find_element(By.ID, "phone").send_keys(username)
    driver.implicitly_wait(1)
    driver.find_element(By.ID, "pwd").send_keys(password)
    driver.implicitly_wait(1)
    driver.find_element(By.ID, 'loginBtn').click()
    time.sleep(3)
    return driver.title

@ddt  
class testAdd(unittest.TestCase):
    def setUp(self):
        options = Options()
        options.add_experimental_option('detach', True)
        driver = webdriver.Chrome(options=options)
        driver.get("https://i.chaoxing.com")
        self.driver = driver

    def tearDown(self) -> None: self.driver.quit()

    @data(*get_Data("UserData.csv"))
    # @unittest.skip(u"无条件跳过")
    @unpack
    def test_add(self,username,password,expectedValue):  # TODO：searchValue,expectedValue值得方向
        # 获取 页面的 title
        title=ActualResult(self.driver,username,password)
        # 断言： 比较结果 True / False
        self.assertEqual(expectedValue,title,"断言结果：")


if __name__=="__main__":
    unittest.main()
```

### 5. 进阶Selenium PageObject:组件调用
```
# base.py
class Base:
    # 一、定义一个基类
    # 1.  # 定义一个初始化函数，初始化浏览器驱动
    def __init__(self,driver):
        self.driver=driver
    # 2.  # 定义一个open方法
    def open(self):
        self.driver.get("https://i.chaoxing.com/")
    # 3.  # 定义一个定位元素
    def elementfind(self,*value):
        return self.driver.find_element(*value)
    # 4.  # 定义一个关闭浏览器的方法
    def close(self):
        self.driver.quit()


# login.py
from time import sleep
from Base import Base
from selenium.webdriver.common.by import By
class login(Base):
    #  变量
    userName=(By.ID, "phone")
    userPasswd=(By.ID, "pwd")
    btn=(By.ID, "loginBtn")

    def input(self,value1,value2):
        self.elementfind(*value1).send_keys(value2)

    def btnClick(self,btn):
        self.elementfind(*btn).click()

    def Login(driver,username,userpwd):
        page=login(driver)
        page.open()
        sleep(1)
        page.input(page.userName,username)
        sleep(1)
        page.input(page.userPasswd,userpwd)
        sleep(3)
        page.btnClick(page.btn)

#getData
import csv
def getData(file_name):
    rows=[]
    file_data=open(file_name,'r',encoding='utf8')
    reader=csv.reader(file_data)
    next(reader)
    for row in reader:
        rows.append(row)
    return rows

#test
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
from ddt import ddt,data,unpack

import unittest
from getData import getData
from login import login

@ddt
class LoginTest(unittest.TestCase):
    def setUp(self) -> None:
        print("-----setUp-----")
        options = Options()
        options.add_experimental_option("detach", True)
        driver = webdriver.Chrome(options=options)
        self.driver=driver

    def tearDown(self) -> None:
        print("-----tearDown-----")
        self.driver.quit()

    @data(*getData("data.csv"))
    @unpack
    def testlogin(self,username,userpwd,title):
        driver=self.driver
        login.Login(driver,username,userpwd)
        actualtitle=driver.title
        #  断言测试结果
        self.assertEqual(actualtitle,title)

if __name__=="__main__":
    unittest.main()

```

## 2. 理论

### 1. Unittest(单元测试)

#### 1.断言
```
方法                            校验条件                            应用实例
assertEqual(a,b[,msg])              a===b                           msg对象用于说明失败原因
assertNotEqual(a,b[,msg])           a!=b                            

assertTrue(x[,msg])                 bool(x) is True                 检验给出的表达式:
assertFalse(x[,msg])                bool(x) is False                    检验一个元素是否出现在页面
assertNot(a,b[,msg])                a is not b                          assertTrue(element.is_displayed())

assertRaises(exc,fun,*args,**kwds)  fun(*args,**kwds)raises exc     检验特定异常是否被具体测试步骤抛出
assertRaisesRegrexp(exc,fun,*args,**kwds)

assertAlmostEqual(a,b)              round(a-b,7)===0                将给定的数值四舍五入
assertNotAlmostEqual(a,b)           round(a-b,7)!=0                 有助于统计由于四舍五入产生的错误


assertGreater(a,b)                  a>b                              逻辑判定条件
assertGreaterEqual(a,b)             a>=b
assertLess(a,b)                     a<b
assertLessEqual                     a<=b


assertRegexpMatches(s,r)            r.search(s)                    检查文本是否符合正则匹配 
assertNotRegexpMatches(s,r)         not.search(s)


assertMultiLineEquak(a,b)           strings                         assertEqual的特殊形式，为多行字符串设计。

assertListEqual(a,b)                lists                           对于下拉列表选项字段的检验非常有用

fail()                                                              无条件失败。当上面的方法不适用时,
                                                                    通过此方法可以创建定制的条件模块
```

#### 2. ElementFind(元素定位)
1. 获取单个元素
```
1. elementfind(By.ID,"")                
2. elementfind(By.NAME,"")
3. elementfind(By.CLASS_NAME,"")        

4. elementfind(By.TAGNAME,"")           #获取元素标签名
5. elementfind(By.XPATH,"")             #获取元素XPATH
6. elementfind(By.CSS_SELECTOR,"")      #获取元素CSS
7. elementfind(By.LINK_TEXT,"")         #获取文本信息
8. elementfind(By.PARTIAL_LINK_TEXT,"") #获取部分文本信息
```
2. 获取多个元素
```
1. elementfinds(By.ID,"")                
2. elementfinds(By.NAME,"")
3. elementfinds(By.CLASS_NAME,"")        

4. elementfinds(By.TAGNAME,"")           #获取元素标签名
5. elementfinds(By.XPATH,"")             #获取元素XPATH
6. elementfinds(By.CSS_SELECTOR,"")      #获取元素CSS
7. elementfinds(By.LINK_TEXT,"")         #获取文本信息
8. elementfinds(By.PARTIAL_LINK_TEXT,"") #获取部分文本信息
```

#### 3. WebDriver(驱动)
1. WebDriver功能
```
属性/功能
page_source             
name                    获取当前浏览器的名称
title
orientation             获取当前设设备的方位
current_window_handle   获取当前窗口的句柄
current_url             获取当前页面的URL地址
window_handles          获取当前session里的所有窗口的句柄
```
2. WebDriver方法
```
方法
back()
close()                             关闭当前网页
forward()  
get(url)
maximize_window()
quit()                              退出当前Driver，关闭所有窗口
refresh()

switch_to_active_element()          返回当前页面唯一焦点所在的网页或者元素
switch_to_alert()                   把焦点切换至当前页面弹出的警告
switch_to_default_content()         切换焦点至默认框架内
switch_to-frame("")                 
switch_to_window(window_name)       切换焦点到指定的窗口名称或者句柄

implicity_wait(time)                等待目标元素被找到，或目标指令完成
set_page_load_timeout(time)         页面完全加载完成  
set_script_timeout(time)            设置脚本执行的超时时间
```

#### 4. WebElememt(接口)
1. WebElememt功能
```
属性/功能
size
tag_name
text
```
2. WebElememt方法
```
clear()
click()
get_attribute("name")               获取元素的属性值
is_displayed()                      检查元素对于用户是否可见
is_enable()                         检查元素是否可用
is_selected()                       检查元素是否可选中
send_keys(*Value)                   模拟输入文本
value_of_css_property("")               获取CSS属性的值
```

#### 5. Select(操作下拉菜单)
select = Select(driver,elemnetfind(By.ID,"id"))
1. Select功能
```
all_selected_options                获取下拉菜单和列表中选择的所有选项内容
first_selectedP_option              获取下拉菜单和列表的第一个选项、当前选择项
options                             获取下拉菜单和列表的所有选项
```
2. Select方法
```
deselect_all()                      清除多选清除下拉菜单和列表的所有选项
deselect(By.INDEX,"index")          根据索引清除下拉菜单和列表的所有选项
deselect(By.VALUE,"value")          清除所有选项值和给定参数匹配的下拉菜单和列表的所有选项
deselect(By.VISIBLE_TEXT,"text")    清除所有展示文本和给定参数匹配的下拉菜单和列表的所有选项

select(By.INDEX,"index")
select(By.VALUE,"value")
select(By.VISIBLE_TEXT,"text")
```

#### 6. Alert(警告)
alert = driver.switch_to_alert()
1. Alert功能
```
text                    获取警告窗文本
```
2. Alert方法
```
accept()                接受JavaScript警告信息，单机OK按钮         
dismiss()               驳回JavaScript警告信息
send_keys(*value)       模拟元素输入信息
```

#### 7. 键盘和鼠标事件
```
click(on_element=None)              单击元素

click_and_hold(on_elemnet)          对元素按住左键

double_click(on_element=None)       双击元素操作

drag_and_drop(source,target)        源元素拖动到释放元素

key_down(value,element=None)        仅按下(Keys.SHIFT) ->  send_keys('n')
key_up(value,element=None)          仅释放(Keys.SHIFT)

move_to_element(to_element)         将鼠标移动至元素的中央

perform()                           提交已保存的动作

release(on_element=None)            释放鼠标

send_keys(keys_to_send)             对当前焦点元素的键盘操作

send_keys_to_element(element,keys_to_send)      对指定元素的键盘操作
```

#### 8. JavaScript
driver.execute_script("return)
```
1. execute_async_script(script,*args)       异步代码
2. execute_acript(script,*args)             同步代码
```