---
layout:     post
title:      "Web Application with Django"
author:     "Cooper"
header-img: "img/post-bg-2015.jpg"
catalog: true
typora-root-url: ../
tags:
     - Web
     -Django
---



# html

头部信息

```html
<head>
  <meta charset="UTF-8">     # 用UTF-8编码
	<title> something </title> # 浏览器头部显示
<head>
 <body>
   <h1>
     1级标题
   </h1>
   <h2>
     2级标题
   </h2>
   <h3>
     3级标题
   </h3>
 <body>
 

```



div和span

```

```



# 网络请求



GET请求



POST请求

# CSS

`CSS` : 专门美化网页，基本了解，会改模版

1. 在标签上

   ```html
   <img src="..." style ="height:100px" />
   <div style = "color:red;">
     中国联通
   </div>
   ```

2. 在head标签中写style标签

   ```html
   <!DOCTYPE html>
   <html lang= "en">
     <head>
       <meta charset='UTF-8'>
       <title>Title</title>
       <style>
         .cl{		#定义一个style
           color:red;
         }
       </style> 
     </head>
   	<body>
       <h1 class="c1">
         用户登录
       </h1>
       <h2 class='c2'>
         something
       </h2>
     </body> 
     
   </html>
   ```

   

3. write to a file (multiple webpages)

   ```html
   .c1{
   	height:100px
   }
   .c2{
   	color:red;
   }
   ```

   

   ```html
   <!DOCTYPE html>
   <html lang= "en">
     <head>
       <meta charset='UTF-8'>
       <title>Title</title>
       #引入css文件	
       <link rel="stylesheet" href="/static/commons.css">     
     </head>
   	<body>
       <h1 class="c1">
         用户登录
       </h1>
       <h2 class='c2'>
         something
       </h2>
     </body> 
     
   </html>
   ```

   

2和3种居多

## css选择器

标签选择器、ID选择器、类选择器

* ID选择器

  ```html
  #C1{
  
  }
  <div id='c1'>
    
  </div>
  ```

  

* 类选择器（最多）

  ```html
  .c1{
  	color:red;
  }
  ```

  

* 标签选择器

  ```html
  li{
  	color: red;
  }
  ```


## Javascript





# Bootstrap

What is  `BootStrap`  ? --> 别人已经写好的一堆 `CSS`

* 下载 `BootStrap`
* 使用
  * 在页面上引入`BootStrap`
  * 编写`HTML` 时，按照 `BootStrap` 的规定来编写 + 自定制。
  * 









# Django

**Tutorial:** 

[大江狗](https://pythondjango.cn/python/advanced/1-python-object-class-programming/)

[B站web开发全家桶](https://www.bilibili.com/video/BV1rT4y1v7uQ?p=38&spm_id_from=pageDriver&vd_source=ced0bea157308d4d01237ca8f4d21d09)



各个文件解释：

![Screenshot 2024-01-19 at 00.16.28](/_posts/src/img/Screenshot 2024-01-19 at 00.16.28.png)



**静态文件：**

"static/"

`Django` **模版语法**: html 占位符



### Django连接数据库

**ORM**

![Screenshot 2024-01-20 at 11.11.15](/_posts/src/img/Screenshot 2024-01-20 at 11.11.15.png)

 

```
conda install -c anaconda mysql
conda install -c anaconda mysqlclient
```

ORM可以帮助我们创建、修改、删除数据库的表（不用你写SQL语句）。【无法创建数据库】

操作表中的数据。

#### **自己创建数据库**

```
mysql -u root -p
#enter your password
create database django_db DEFAULT CHARSET utf8 COLLATE utf8_general_ci;
```



#### django连接数据库

`setting.py`:

```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'django_db',
        'USER': 'root',
        'PASSWORD': '692410Laobo',
        'HOST': 'localhost',   # 或者你的数据库服务器的 IP
        'PORT': '3306',        # 默认端口
    }
}
```

#### 定义模型

模型是Django ORM的核心，它定义了数据库表的结构。每一个模型类都对应数据库中的一个表。以下是一个简单的模型示例，假设我们要操作一个名为`UserInfo`的表：

在`models.py`：创建类

```
class userInfo(models.Model):                      		
    username = models.CharField(max_length=32)         
    password = models.CharField(max_length=32)
    email = models.CharField(max_length=32)

```

#### 运行迁移

在定义了模型后，你需要运行迁移命令来创建或更新数据库表。首先，生成迁移文件：

```
python manage.py makemigrations
```

然后，应用迁移来实际创建/更新数据库表：

```
python manage.py migrate
```

**你可以在mysql中查看所创建的表：**

```
#进入数据库
 mysql -u root -p

```

```
#查询数据库
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| django2_db         |
| django_db          |
| information_schema |
| mysql              |
| performance_schema |
| sys                |
| we7                |
+--------------------+
7 rows in set (0.00 sec)
```

使用django2_db数据库：

```
use django2_db；
```

**显示表**:

一旦选择了数据库，你就可以使用`SHOW TABLES;`命令来显示该数据库中的所有表了：

```
mysql> SHOW TABLES;
+----------------------------+
| Tables_in_django2_db       |
+----------------------------+
| auth_group                 |
| auth_group_permissions     |
| auth_permission            |
| auth_user                  |
| auth_user_groups           |
| auth_user_user_permissions |
| django_admin_log           |
| django_content_type        |
| django_migrations          |
| django_session             |
| home_sequencingdata        |
| home_userinfo              |
+----------------------------+
12 rows in set (0.00 sec)

```

查看表`home_userinfo`:这会列出表的所有列及其数据类型。

```
mysql> DESCRIBE home_userinfo;
+----------+-------------+------+-----+---------+----------------+
| Field    | Type        | Null | Key | Default | Extra          |
+----------+-------------+------+-----+---------+----------------+
| id       | bigint      | NO   | PRI | NULL    | auto_increment |
| username | varchar(32) | NO   |     | NULL    |                |
| password | varchar(32) | NO   |     | NULL    |                |
| email    | varchar(32) | NO   |     | NULL    |                |
+----------+-------------+------+-----+---------+----------------+
4 rows in set (0.01 sec)
```

**查询数据**

为了查看`home_userInfo`表中的数据，你可以执行一个`SELECT`查询：

```
mysql> SELECT * FROM userInfo;
ERROR 1146 (42S02): Table 'django2_db.userinfo' doesn't exist
mysql> SELECT * FROM home_userInfo;
+----+----------+----------+-------+
| id | username | password | email |
+----+----------+----------+-------+
|  1 | test     | 123      |       |
+----+----------+----------+-------+
1 row in set (0.00 sec)
```

#### 使用Django ORM进行CRUD操作

```
from home.models import userInfo
# Create your tests here.


#创建表
test = userInfo(username='test',password='123',SequencingData_url = 'pages/pipeline/pipeline_16S.html',)
test.save()

#读取表
tests = userInfo.objects.all()
test = userInfo.objects.get(id=1)


#更新（Update）:
test = userInfo.objects.get(id=1)
test.username = 'Django for Professionals'
test.save()


test = userInfo.objects.get(id=2)
test.email = '479031941@qq.com'
test.SequencingData_url = 'pages/pipeline/pipeline_rnaseq.html'
test.save()

#删除（Delete）:
test = userInfo.objects.get(id=1)
test.delete()
```

可以用`Visual studio Code`的 `Terminal`中输入：“python manage.py shell” 进行调试

```
python manage.py shell
```



### 创建一个上传测序数据的表单



#### 如何在ModelForm中增加Boostrap样式

![image-20240304101102719](/_posts/src/img/image-20240304101223028.png)

```

```





# 关于PyWebIO

python can share variables between scripts, but not variables within a function. 

However, you can share variables when using **PyWebIo**, this may be because you get variables from the front-end: like pin.Input_DNA





# git开发版本控制

### macos上传

使用git Desktop

### Linux 服务器同步文件

```

```

