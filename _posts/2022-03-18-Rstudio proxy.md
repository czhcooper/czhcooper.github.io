---
layout:     post
title:      "Proxy setting for R "
subtitle:   
date:       2022-03-18 14:19:00
author:     "Cooper"
header-img: "img/post-bg-2015.jpg"
catalog: true
typora-root-url: ../
tags:
    - Typora
    
---



The first thing to do is checking what kind of proxy you're using. I'm using V2ray now, so check it's configure:

![image-20220318115258130](/img/md-post/2022-03-18-Rstudio%20proxy/image-20220318115258130.png)



Open Terminal and code the following:



```
vim ~/.Renviron
```



![Screen Shot 2022-03-31 at 10.39.05](/img/md-post/2022-03-18-Rstudio%20proxy/Screen%20Shot%202022-03-31%20at%2010.39.05.png)

Save it . Done!

If the above resolution doesn't work, try this at **Rstudio**: using http proxy

```
Sys.setenv(all_proxy="http://127.0.0.1:8001")
```

