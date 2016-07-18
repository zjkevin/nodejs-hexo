---
title: python3安装
tags:
  - python
  - 开发语言
categories: python
kind: python
date: 2016-07-05 10:11:54
---

### windows下安装
[python官网](https://www.python.org/)
如果是windows版本，在安装界面选中pip安装，path环境变量也可以在安装界面上勾选，如果忘记请自行添加。

### centos6.8下安装
python官网下载tar.xz包
```{bash}
   xz -d Python-3.4.4.tar.xz 先用xz解压(压缩比非常高的一个工具，缺点是慢)
   tar xvf Python-3.4.4.tar 
   #依赖包
   yum install gcc 
   yum install openssl.x86_64
   yum install openssl-devel.x86_64
   ./configure 
   make
   make install
```

### 根据你自己的需要设置环境变量
如果想用python直接调用python3，你可以将环境变量python指向python3,方法就是用which命令查看具体路径，然后建立软链接
```{bash}
which python3
ln -s "python3目录" /usr/bin/python
```
也可以直接使用python2 python3显示的调用具体版本
使用以下命令区别python2和3的pip
```{bash}
python3 -m pip install xxxx
python2 -m pip install xxxx
```
