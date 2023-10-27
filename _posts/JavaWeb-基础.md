---
layout: javascript
title: JavaWeb 基础
date: 2023-01-02 18:49:46
description:  # 副标题
sticky:             #置顶
toc:                #显示文章TOC（默认为设置中toc的enable配置）
toc_number:         #显示toc_number（默认为设置中toc的number配置）
abbrlink: 997804fe
updated:                #页面更新日期
type: JavaScript   #【必需】标签、分类和友情链接三个页面需要配置
tags: 
- JavaWeb
- 基础
# - Python      #文章标签  
# tags: Python
categories: 
- JavaWeb       #文章分类
- 基础
keywords:   #页面关键词
cover:   'img/25.png'    #文章缩略图（如果没有设置top_img，文章页顶部将显示缩略图，可设为false/图片地址/留空）

comments:         #显示页面评论模块 默认 true
top_img: 'img/25.png'       #页面顶部图片
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

# 1.JSP标签
### 1.java 变量转 jsp
```
</pre>1.java 变量转 jsp<p></p><p></p><pre code_snippet_id="1800145" snippet_file_name="blog_20160801_2_2452946" name="code" class="html"><% String value = request.getParameter("key");%>  
<label><%=value %></label>  
```
### 2.jsp 变量转 js
```
<input type="text" name="firstname">test</input>  
<script>  
var test = document.getElementById("firstname");  
</script>  
```
### 3.js 转 Java
```
//虚拟表单提交  
var temp = document.createElement("form");  
temp.action = URL;//提交的地址  
temp.method = "post";//也可指定为get  
temp.style.display = "none";  
var opt = document.createElement("textarea");  
opt.name = key;  
opt.value = value;  
temp.appendChild(opt);  
document.body.appendChild(temp);  
temp.submit();  
  
//java 代码  
  
String var = request.getParameter("key");//此时var的值就是value  
``` 

### 4.jsp转Java
```
String var = request.getParameter("key");//jsp表单提交了，就可以从request中获取。也可以虚拟表单提交。  
```
### 5.js转jsp
```
var test = "test";  
document.getElementById("demo").innerHTML=test;  
```
### 6.java 转 js
```
<% String temp = request.getParameter("key");%>  
<label name="test" hidden="hidden"><%=temp %></label>  
<script>  
var temp = document.createElement("test");  
</script>  
```

# 2.JSP内置对象

### JSP提供9个内置对象:
     对象名称         	衍生类     					功能简述	
(1)request		Javax.servelet.ServletRequest.HttpServletRequest 	取得客户端与系统的信息		

(2)response	Javax.servlet.Servlet Request.HTTP Servlet.Response	响应客户端信息

(3)application	Javax,servlet.ServletContext			记录和处理上线者共享的数据

(4)session		Javax.servlet.Http.Session			记录和处理上线者的个别数据

(5)out		Javax.servlet.jsp.writer			控制数据输出的操作

(6)config		Javax.servlet.servletConfig			取得JSP编译后Servlet信息

(7)PageContext	Javax.servlet.jsp.PageContext			存储和处理系统运行时的各种信息

(8)page		Javax.lang.Object				代表目前的这个JSP网页对象

(9)exception	Javax.lang.Throwable			异常处理机制


### 内置对象生命周期
  application > session > page > request


### Request内置对象:
	
####	一:Request内置对象的常用方法
	    方法				                               说明
	     (1)  getAttribute( String name)	       返回 name 所指的值
	     (2) setAttribute( String name , Object obj)  设定name所指定的属性为 obj
	     (3) removeAttribute( String name)	       删除name所指定的属性
	     (4) getAttributeNames()		       返回request对象所有的属性名称集合
	     (5) getParameter( String name)	       从客户端获取name所指定的参数
	     (6) getParameter Names()		       从客户端获取所有参数名称
	     (7) getParameterValues( String name)	       从客户端获取所指定参数的所有值
	     (8) setCharacterEncoding( String encoding)设定请求正文中所使用的字符编码(只支持post提交的数据)
#####	 Request内置对象应用实例
```	    
         <% 
		Enumeration enu = request.getParameterNames(); //page标签导入 import="Java.util.*" 
		while(enu.hasMoreElements()){
			String parameterName = (String) enu.nextElement();
			String parameterValue = request.getParameter(parameterName);
			out.print("参数名称:"+parameterName);
			out.print("\t参数内容:"+parameterValue);
		}
	    %>
```
###	二:Response内置对象
	方法				说明
	    (1) setContentType( String type)	       动态响应content Type属性
	    (2) setHeader( String name,String value)     设置HTTP应答报文的首部字段和值及自动更新
	    (3) setRedirect( String redirectURL)	       将客户端重定向到指定URL 
	    (4) setStatus( int n)		       设定HTTP返回的状态值
	    (5) addCookie( Cookie cookie)	       添加一个Cookie对象 


# 3.JSP语法


### 一、JSP脚本标记
####    1.脚本段
        <% Java程序段 %>
####    2.JSP声明 
        <%! 声明1;声明2; %>
        PS: 1.可以在 <%@ page %>直接使用已经声明的变量和方法
            2.多个页面声明，写成单独的一个文件用 
                <%@ include %>/<jsp:include>
####    3.JSP表达式
        <%= 变量/表达式 %>
####    4.JSP注释
        <%--  --%>

### 二、JSP指令标记

####    1.page页面指令标记: 
    　　<%@ page 属性1="value1" 属性2="value2“ %>
        属性（每次一个属性）:
           (1)language: 脚本语言 Java
            (2)import  在程序中导入的类和包
            (3)session: true / false  设定HTTP Session
            (4)autoFlash: true / false  设置缓冲区填满时 缓冲自动刷新
            (5)isThreadSafe: true / false  设置JSP　页面支持多线程
            (6)isErrorPage: false / true 　　指定当前页面作为另一页面的错误处理页码
            (7)errorPage　　指定当前网页的错误处理页码的ＵＲＬ
            (8)contentType: text/html;charset=gb2312
                            页面响应的MIME类型；指定字符编码

####    ２.include静态包含指令标记：
        <%@　include file＝＂相对位置＂%>
        相同文件夹下   建议以 .jspf(jps fragment)
	(PS: 由于键值对,除import,pageEncoding,不可以引入其他相同属性)

####    3.taglib指令标记
        <%@taglib  url="标签库url"  prefix="自定义标签前缀" %>
        <publi:loop>
            ...
        </publi:loop>

### 三、JSP动作标记

####    1.<jsp:include>:(传参详列:Page 25)
        不带参数：<jsp:include page="相对url" flush="true/false"/>
           带参数：<jsp:include page="相对url" flush="true/false"/>
                              <jsp:param name="属性名" value="属性值"/>    // 传递多个参数给动态文件
                             <jsp:param...>
                       </jsp:include>
            
####    2.<jsp:forward>:(服务器端跳转,浏览器地址栏不做变化)
         不带参数:  <jsp:forward page="URL">
            带参数:   <jsp:forward page="URL">
		 <jsp:param name="属性名" value="属性名"/>
		  ...
	           </jsp:forward>

####     3.<jsp:param>:
          <jsp:aram name="参数名"  value="参数值"/<%=表达式%>  />
	传递的参数通过request.getParameter("属性名")获取参数的值.
	单独使用<jsp:param>没有意义

####     4.<jsp:plugin>:
	<jsp:plugin>动作用于jsp网页加载Java Applet 或 JavaBean 程序组件,
	       与HTML的<Applet>和<Object>标签有类似的功能.
	常用属性表:
	       (1)  type:加载Java程序类型,可设置值Applet,Bean
	       (2)  code:加载Java程序编译后的类名称, showpic.class
	       (3)  codebase:  编译后Java程序类所在的目录,可设置绝对值路径或相对路径.  默认执行当前网页的目录默认值.
	       (4)  name:  用来加载Java Applet 和 JavaBean程序设置一个用以识别的名称.
	       (5)   align:  设置加载的程序在窗口的对齐方式,可设置由bottom,top,middle,left,right.
	       (6)  height:  加载程序在窗口中显示的高度
	       (7)  width:  加载程序在窗口中显示的宽度
	       (8)  hspace:  加载程序的显示器和网页其他内容的水平间距
	       (9)  vspace:  加载程序的显示区与网页其他内容的垂直距离
	       (10)  <jsp:params>:  将参数传递给加载程序,必须在<jsp:params>  </jsp/params>中使用 <jsp:param> 来设置.

####   5.<jsp:userBean> <jsp:setProperty> 和 <jsp:getProperty>动作标记
	<jsp:userBean>动作标记用来加载JSP页面中使用的JavaBean
		<jsp:userBean id="Java Bean实列名称" scope"page / request / session / application"  class="package.class">
		属性:
		        (1) id:  JavaBean实列名称
		        (2) scope:  指定该Bean变量的有效范围.
		        (3) class:  导入的Java包 例如:需求时间 导入 Java.util.Date
	
       	<jsp:setProperty>动作标记用于设置已经实列化的Bean对象属性
```
		<jsp:setProperty
			name="JavaBean实列名称"
			{ 
			property="*"  /
			property="属性名"  [param="参数"] /
			property="属性名'  value"{String<%=表达式%>"
			}
		/>
```
	(PS:  <jsp:setProerty>中 name值 必须和 <jsp:useBean>中 id值相同, 且大小写敏感.
	
	<jsp:getProerty>动作标记可获得Bean的著性质,用于页面中显示.
		<jsp:getProerty name="JavaBean实列名称" property="属性名"/>



# 数据库导入
## 1.cn.com.Dao
1. cn.com.Dao.JDBCUtils
```
package cn.com.Dao;

import java.sql.*;
public class JDBCUtils {
	//连接数据库，关闭数据库 接口
	private static String url="jdbc:mysql://localhost:3306/student?serverTimezone=UTC";
	private static String user="root";
	private static String pwd="root";

	// JDBC 驱动器
	public static Connection getConnection() {
		Connection conn = null;
		try {
			Class.forName("com.mysql.cj.jdbc.Driver");
			conn=DriverManager.getConnection(url,user,pwd);
		} catch (Exception e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		return conn;
	}	

	// 验证链接是否正常
	public static void CloseAll(Connection conn,PreparedStatement prestmt,Statement stmt,ResultSet rs) {
		if(rs!=null) {
			try {
				rs.close();
				if(stmt!=null) {
					stmt.close();
				}
				if(prestmt!=null) {
					prestmt.close();
				}
				if(conn!=null) {
					conn.close();
				}
			} 
			catch (SQLException e) {
				e.printStackTrace();
			}
		}
	}


}

```

2. cn.com.Dao.UserDAO
```
package cn.com.Dao;

import java.sql.*;
import java.util.ArrayList;
import java.util.List;

import org.omg.CORBA.Request;

import java.sql.Date;
import java.text.SimpleDateFormat;

import cn.com.JavaBean.User;


public class UserDAO {

	/*
	 * 数据库查询
	 * 
	 */
	public List<User> findAllUsers(){
		// 初始化数据
		Connection conn=null;
		Statement stmt=null;
		List<User> users=null;
		ResultSet rs=null;
		
		try {
		// 链接驱动器
			conn =JDBCUtils.getConnection();
		// 读取执行数据库操作命令
			stmt=conn.createStatement();
			String sql="select * from user2";
			rs=stmt.executeQuery(sql);
		
		// 创建对象储存数据
			users=new ArrayList<User>();
		// next() 一行行的执行数据
			while(rs.next()) {
				
				User u=new User();
			// 用数据库的列名，准确性，可读性较高
				u.setID(rs.getInt("ID"));
				u.setName(rs.getString("Name"));
				u.setPwd(rs.getString("Pwd"));
				u.setEmail(rs.getString("Email"));
				u.setSex(rs.getString("Sex"));
				u.setBirthday(rs.getDate("Birthday"));
			// 利用List数据的方法存入链数组
				users.add(u);
			}			
		} catch (SQLException e) {
			e.printStackTrace();
		}finally {
			// 关闭数据库
			JDBCUtils.CloseAll(conn, null, stmt, rs);
		}
		return users;
		
	}



	/*
	 * 数据库删除
	 * 
	 */
	public boolean DeleteUserByID(int id) {

		Connection conn=null;
		PreparedStatement prestmt=null;
		ResultSet rs=null;
		
		try {
			conn =JDBCUtils.getConnection();
			String sql="delete from user2 where ID = ?";
			prestmt=conn.prepareStatement(sql);
			prestmt.setInt(1, id);
			int row=prestmt.executeUpdate();
			if(row>0) {
				return true;
			}

			return false;

		} catch (SQLException e) {
			e.printStackTrace();
		}finally {
			JDBCUtils.CloseAll(conn, prestmt, null, rs);
		}

		return false;

	}


	/*
	 * 数据库增加
	 * 
	 */

	public boolean InsertUserByID(User user) {

		Connection conn=null;
		PreparedStatement prestmt=null;
		ResultSet rs=null;
		
		try {
			conn =JDBCUtils.getConnection();
			String sql="insert into 'user' (Name,password,Email,sex,date) values (?,?,?,?)" ;
			prestmt=conn.prepareStatement(sql);
			prestmt.setString(1, user.getName());
			prestmt.setString(2, user.getPassword());
			prestmt.setString(3, user.getEmail());
			prestmt.setString(4, user.getDate());

			int row=prestmt.executeUpdate();
			if(row>0) {
				return true;
			}
			return false;
		} catch (SQLException e) {
			e.printStackTrace();
		}finally {
			JDBCUtils.CloseAll(conn, prestmt, null, rs);
		}

		return false;

	}
}

```

## 2.cn.com.JavaBean
1. cn.com.JavaBean.User
```
package cn.com.JavaBean;

import java.util.Date;

/*
 * 创建 对象 对映数据库的数据 
 * 作为接口用于读取和写入的操作
 */
public class User {
	private int ID;
	private String Name;
	private String Pwd;
	private String Email;
	private Date Birthday;
	private String Sex;
	public int getID() {
		return ID;
	}
	public void setID(int iD) {
		ID = iD;
	}
	public String getName() {
		return Name;
	}
	public void setName(String name) {
		Name = name;
	}
	public String getPwd() {
		return Pwd;
	}
	public void setPwd(String pwd) {
		Pwd = pwd;
	}
	public String getEmail() {
		return Email;
	}
	public void setEmail(String email) {
		Email = email;
	}
	public Date getBirthday() {
		return Birthday;
	}
	public void setBirthday(Date birthday) {
		Birthday = birthday;
	}
	public String getSex() {
		return Sex;
	}
	public void setSex(String sex) {
		Sex = sex;
	}
	public User() {
		super();
	}
	@Override
	public String toString() {
		return "User [ID=" + ID + ", Name=" + Name + ", Pwd=" + Pwd + ", Email=" + Email + ", Birthday=" + Birthday
				+ ", Sex=" + Sex + "]";
	}
	
}

```

## 3.cn.com.Impl
1. 
```
package cn.com.lmpl;
import cn.com.JavaBean.*;
import java.util.List;
import cn.com.Dao.*;

/*
 * 数据封装 调用方法函数
 */

public class UserImpi {
	public List<User> findAllUsers(){
		UserDAO ud = new UserDAO();
		return ud.findAllUsers();
	}
	public boolean DeleteUserByID(int id) {
		UserDAO ud=new UserDAO();
		return ud.DeleteUserByID(id);
	}
	public boolean InsertUser(User user){
		return ud.InsertUser(user);
	}
}

```

## 4.cn.com.Servlet
1. cn.com.Servlet.DeleteUserByServlet
```
package cn.com.Servlet;

import jakarta.servlet.RequestDispatcher;
import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.util.List;

import cn.com.JavaBean.User;
import cn.com.lmpl.UserImpi;

/**
 * Servlet implementation class DeleteUserByServlet
 */
public class DeleteUserByServlet extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public DeleteUserByServlet() {
        super();
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		response.setCharacterEncoding("utf-8");
		response.setContentType("text/html; charset=utf-8");
		// 调用实现方法的对象
		UserImpi ui =new UserImpi();
		
		// 将前端的请求数据 获取并传入方法
		int id =Integer.parseInt(request.getParameter("id")) ;
		
		// 获取方法返回的数据，判断结果
		boolean f=ui.DeleteUserByID( id);
		if(f) {
			response.getWriter().write("删除成功");
		}else
		{
			response.getWriter().write("删除失败");
		}
		
}

}

```

2. cn.com.Servlet.InsertUserByServlet
```


package cn.com.Servlet;

import jakarta.servlet.RequestDispatcher;
import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.List;

import cn.com.JavaBean.User;
import cn.com.lmpl.UserImpi;

/**
 * Servlet implementation class DeleteUserByServlet
 */
public class InsertUserByServlet extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public DeleteUserByServlet() {
        super();
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		response.setCharacterEncoding("utf-8");
		response.setContentType("text/html; charset=utf-8");
            String name = requset.getParameter("Name");
            String password = requset.getParameter("password");
            String Email = requset.getParameter("Email");
            String sex =  requset.getParameter("sex");
            // String  date = requset.getParameter("date");

            SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd");
			String birthday = request.getParameter("birthday"); 
			Date date = null;
            try{
                dat = new Date(sdf.parse(birthday));
            }catch(ParseException e){
                e.printStackTrace();
            }


            UserImpi ui = new UserImpi();
            User u  = new User();
            u.setName(name);
            boolean flag = ui.InsertUser(u);
            if(flag){
                response.getWriter.write("成功");
            }else{
                response.getWriter.write("失败");
            }
    }
}

```

3. cn.com.Servlet.ShowAllUserByServlet
```
package cn.com.Servlet;

import jakarta.servlet.RequestDispatcher;
import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.util.List;

import cn.com.JavaBean.User;
import cn.com.lmpl.UserImpi;

/**
  * Servlet implementation class ShowAllUsersServlet
 */
public class ShowAllUsersServlet extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public ShowAllUsersServlet() {
        super();
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// 调用方法实现的对象
		UserImpi ui =new UserImpi();
		// 将从数据库获取的对象传入 List 数组
		List<User> users=ui.findAllUsers();
		// 创建服务器对象,缓存数据对象
		request.setAttribute("users", users);

		// 实现页面跳转  显示结果
		RequestDispatcher rd = request.getRequestDispatcher("ShowUsers.jsp");
		rd.forward(request, response);
		
	}
}

```

## 5. InsertUser
```
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>


   <%@taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
   <%@page import="cn.com.JavaBean.*,java.util.*" %>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>数据库插入页面</title>
<style type="text/css">
table {
	border-collapse:collapse;
}
</style>
</head>
<body>
	
    <table>
        <tr>
            <td>用户名</td>
            <td><input type="text" name="Name"></td>
        </tr>
        <tr>
            <td>密码</td>
            <td><input type="text" name="password"></td>
        </tr>
        <tr>
            <td>邮箱</td>
            <td><input type="text" name="Email"></td>
        </tr>
        <tr>
            <td>性别</td>
            <td>
                <input type="radio" value="1" name="sex" checked>
                <input type="radio" value="0" name="sex">
            </td>
        </tr>
        <tr>
            <td>出生日期</td>
            <td>
                <input type="date" name="date"></input>
            </td>
        </tr>
        <tr><td colspan="2"><input type="submit" value="插入"></td></tr>
    </table>

</body>
</html>
```