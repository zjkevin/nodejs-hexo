---
title: redis安装
tags:
  - redis
  - 默认
categories: redis
kind: redis
date: 2016-12-20 10:54:09
permalink: redis_install
---

### 安装
```{bash}
cp redis-3.2.5.tar.gz /usr/local/
cd /usr/local/
tar -xvzf redis-3.2.5.tar.gz
cd redis-3.2.5
make
cd src/
make test
# 如果缺少tcl请安装
yum install tcl.x86_64
make test
```

### 配置
```{bash}
vim redis.conf 
```

### 启动
```{bash}
nohup ./redis-server &
```

### 客户端
RedisDesktopManager

### 待研究
redis主从