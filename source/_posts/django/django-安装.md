---
title: django_安装
tags:
  - django
  - web框架
  - python
categories: django
kind: django
date: 2016-07-04 15:05:39
---

### django的安装
#### windows

[Django下载地址](https://www.djangoproject.com/download/)

解压下载包，安装：
```{bash}
$ python3 setup.py install
```

配置环境变量：
path中添加C:\Python34\Lib\site-packages\django

验证：
```{bash}
python3               
import django
django.get_version()
```
