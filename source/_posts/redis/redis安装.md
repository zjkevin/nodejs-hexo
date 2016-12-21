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
nohup src/redis-server /usr/local/redis-3.2.5/redis.conf &
```

### 客户端
RedisDesktopManager

### 设置密码
```{bash}
vim redis.conf 
requirepass XXXXXXXX
```

### 测试
# 本地测试
redis-cli -h 127.0.0.1 -a 1234567890 ping
# 其他IP
redis-cli -h 192.168.1.111 -a 1234567890 ping

### 待研究
redis主从