---
layout:     post
title:      "Nginx教程"
author:     "Cooper"
header-img: "img/post-bg-2015.jpg"
catalog: true
typora-root-url: ../
tags:
     - Web application
---

# Introduction to NGINX

- It can handle a higher number of concurrent requests.
- It has faster static content delivery with low resource usage.



# Install Nginx

```
vi /etc/yum.repos.d/nginx.repo
```

写入：

```
[nginx] 
name = nginx repo 
baseurl = https://nginx.org/packages/mainline/centos/7/$basearch/ 
gpgcheck = 0 
enabled = 1
```

wq保存退出

用``yum`安装`nginx`

```
yum install -y nginx
```

配置`default.conf` 文件

```
vim /etc/nginx/conf.d/default.conf
```

写入：



```
server {
    listen       80;
    root   /usr/share/nginx/html;
    server_name  localhost;
    #charset koi8-r;
    #access_log  /var/log/nginx/log/host.access.log  main;
    #
    location / {
          index index.php index.html index.htm;
    }
    #error_page  404              /404.html;
    #redirect server error pages to the static page /50x.html
    #
    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
      root   /usr/share/nginx/html;
    }
    #pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
    #
    location ~ .php$ {
      fastcgi_pass   127.0.0.1:9000;
      fastcgi_index  index.php;
      fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
      include        fastcgi_params;
    }
}
```

wq保存退出

#### 启动`nginx`

```
systemctl start nginx
```

如果报错，可能是`80`端口已被占用，在上面文件中改其他端口，如81

查看端口：

```
lsof -i tcp:80
```

## 停止`nginx`

```
systemctl stop nginx
```



#### 开机启动

```
systemctl enable nginx 
```

#### 本地浏览器测试

```
http://服务器IP
```

默认端口为：80，如果改了81则为：

```
http://服务器IP：81	
```

![Screenshot 2022-12-30 at 11.01.46](/img/md-post/2022-12-30-Nginx%20tutorial/Screenshot%202022-12-30%20at%2011.01.46.png)



# Configure Nginx





#### 参考材料

[Nginx极简教程](https://github.com/dunwu/nginx-tutorial#%E4%B8%80nginx-%E7%AE%80%E4%BB%8B)