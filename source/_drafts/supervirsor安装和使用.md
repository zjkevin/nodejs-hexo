---
title: supervirsor安装和使用
kind: 进程监控管理
tags:
---


#### 安装

Supervisor is known to work with Python 2.4 or later but will not work under any version of Python 3.

Python2.4以上，但是暂不支持Python3

pip install supervisor

或者
下载压缩包安装
```{bash}
    wget <网址>supervisor-3.3.1.tar.gz
    tar -xzvf supervisor-3.3.1.tar.gz 
    cd supervisor-3.3.1
    python setup.py install
```

检查你的环境变量，supervisor的命令在 /usr/local/python2.7/bin/下，根据你系统的python安装情况自行匹配位置
确保/usr/local/python2.7/bin/ 加入PATH中，否则你只能cd到/usr/local/python2.7/bin/去操作
```{bash}    
    /etc/profile.d/
    vim supervirsor.sh
    加入一行 export PATH=/usr/local/python2.7/bin:$PATH 
```