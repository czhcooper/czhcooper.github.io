---
layout:     post
title:      "Deploy Shiny App"
author:     "Cooper"
header-img: "img/post-bg-2015.jpg"
catalog: true
typora-root-url: ../
tags:
     - Web application
     - Shiny
     - R
---

# Introduction

Deploy Shiny App on CentOS 7

what you need:

- R

- shiny 

- shiny server

  

  # Install R  and R packages with conda

  step 1: configure yours `.condarc` file, add 清华源:

  ```
  channels:
    - defaults
  show_channel_urls: true
  default_channels:
    - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
    - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
    - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2
  custom_channels:
    conda-forge: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
    msys2: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
    bioconda: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
    menpo: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
    pytorch: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
    pytorch-lts: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
    simpleitk: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  ```

  step 2: install r-base by using conda

  ```
  conda search r-base
  conda install r-base=4.2.0
  ```

  step 3: install devtools,  shiny, tidyverse, DT

```
conda install r-devtools
```

```
conda install r-shiny
```

```
conda install r-tidyserver
```

```
conda install r-DT
```

# Install Shiny Server

```
wget https://download3.rstudio.org/centos6.3/x86_64/shiny-server-1.5.7.907-rh6-x86_64.rpm
yum install --nogpgcheck shiny-server-1.5.7.907-rh6-x86_64.rpm
```

then enable and start `shiny-server`

```
systemctl start shiny-server
systemctl enable shiny-server
```

# Enable port

`shiny-server` has default index webpage by using 3838 port,  you can enable 3838 port 

by using `firewall-cmd` as follows:

```
firewall-cmd --permanent --zone=public --add-port=3838/tcp
firewall-cmd --reload
```

Alternatively, you can enable it on the console provided by the cloud server.

# Run shiny app

Finally, assuming you have an R script `app.R`in current directory , then run the code:

```
R -e "shiny::runApp('app.R',port=3737,host='0.0.0.0')"
```

Notice:`host='0.0.0.0' ` should be added, or you can not access the shiny app from the internet. It means the Shiny app will accept connections on all network interfaces of the machine, making it accessible from any IP address that can reach your server. 

