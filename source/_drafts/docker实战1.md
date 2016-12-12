---
title: docker实战1
kind: docker
tags:
---


### 实战内容

听闻微软的mssql数据库可以在linux上运行，十分惊喜，新建一个ubuntu 16.04的容器，安装mssql-server，并测试mssql。

#### 本地下载mssql的linux安装包
```shell
    #添加安装包认证
    curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
    curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server.list > /etc/apt/sources.list.d/
    apt-get update
    #下载安装包
    cd /home/kevin
    mkdir app
    cd app
    apt-get download mssql-server  
```

#### 拉取docker的ubuntu 16.04镜像
```shell
    docker pull ubuntu:16.04  
```

#### 运行docker容器，并将/home/kevin/app 挂载到该容器内
这里是采用离线安装的方式，你也可以采用在线安装的方式，主要目的是练习测试docker的数据卷挂载，所以采用离线安装方式。
docker run -d -it --name mssql -v /home/kevin/app:/opt/webapp ubuntu:16.04 /bin/bash
```shell
容器里面很可能缺少某些命令工具，使用下面的命令查找缺少的包并安装
which curl
dpkg -S /usr/bin/curl
```

物理机内存要求有3.25G才能安装
```error
ERROR: This machine must have at least 3.25 gigabytes of memory to install Microsoft(R) SQL Server(R).
```


