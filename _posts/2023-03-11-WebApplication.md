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

别人已经写好的一堆`CSS`



# Django



# 关于PyWebIO

python can share variables between scripts, but not variables within a function. 

However, you can share variables when using **PyWebIo**, this may be because you get variables from the front-end: like pin.Input_DNA

