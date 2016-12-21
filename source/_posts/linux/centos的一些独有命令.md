---
title: centos的一些独有命令
permalink: centos1
tags:
  - linux
  - centos
  - 操作系统
categories: linux
kind: linux
date: 2016-07-18 09:54:13
---

### 查看系统版本
众所周知centos和redhat的关系

    cat /etc/redhat-release

### 禁止IPv6
```{bash}
vim /etc/sysctl.conf
添加
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
net.ipv6.conf.eth0.disable_ipv6 = 1
网卡设备根据实际情况设置

sudo sysctl -p
```


