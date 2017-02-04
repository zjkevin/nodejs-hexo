---
title: python3安装
type: "tags"
tags:
  - python
  - 开发语言
categories: python
kind: python
date: 2016-07-05 10:11:54
permalink: python1
---

### windows下安装
[python官网](https://www.python.org/)
如果是windows版本，在安装界面选中pip安装，path环境变量也可以在安装界面上勾选，如果忘记请自行添加。

### centos6.8下安装
#### tar.xz包安装方式
```{bash}
   如果没有xz工具 安装 apt-get install xz-utils
   xz -d Python-3.4.4.tar.xz 先用xz解压(压缩比非常高的一个工具，缺点是慢)
   tar xvf Python-3.4.4.tar 
   #依赖包
   yum install gcc 
   yum install openssl.x86_64
   yum install openssl-devel.x86_64
   debian下安装 apt-get install libssl-dev
   ./configure 
   make
   make install
```

#### tgz包安装方式
```{bash}
    yum -y install wget
    yum -y install gcc
    yum -y install make
    wget http://www.python.org/ftp/python/3.4.4/Python-3.4.4.tgz
    tar -xzvf Python-3.4.4.tgz 
    cd Python-3.4.4
    mkdir /usr/local/python3
    ./configure --prefix=/usr/local/python3 --enable-shared
    make all
    make install
    rm -r Python-3.4.4 --force
    rm Python-3.4.4.tgz --force
    
    #make clean
    #make distclean 
    cd /usr/lib64 && ln -s /usr/local/python3/lib/libpython3.4m.so.1.0  libpython3.4m.so.1.0
    cd /usr/bin/ && ln -s /usr/local/python3/bin/python3 python3
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

### CentOS上升级Python2.6到Python2.7
```{bash}
    # 安装python2.7.6
    tar -xzvf Python-2.7.6.tgz 
    cd Python-2.7.6
    ./configure --prefix=/usr/local/python2.7
    make
    make install
    cd /usr/bin
    ln -fs /usr/local/python2.7/bin/python2.7 python
    # 据说yum只能由CPython2.6解析,打开yum的程序文件，将首行解析器指定声明修改为2.6
    which yum
    vim /usr/bin/yum
    #!/usr/bin/python  --> #!/usr/bin/python2.6
```

### pip安装
    https://pip.pypa.io/en/stable/installing/

### debain8下dist-packages不在sys.path中
```{bash}
vim /etc/profile.d/python3.sh
#!/bin/bash
export PYTHON_HOME=/usr/local/python3
export PATH=$PYTHON_HOME/bin:$PATH
export PYTHON_DIST_HOME=/usr/local/lib/python3.4/dist-packages
export PYTHONPATH=$PYTHON_DIST_HOME:$PYTHONPATH
```