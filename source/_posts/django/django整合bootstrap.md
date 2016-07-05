---
title: django整合bootstrap
tags:
  - django
  - bootstrap
  - web框架
  - python
categories: django
kind: django
date: 2016-07-05 14:30:08
---

### 下载
bootstrap就是一堆静态的css,js和字体文件
[bootstrap官网](http://v3.bootcss.com/)

### 和django整合
#### 版本
bootstrap 3.3.6
django 1.9.7

将bootstrap解压后放在django站点根目录的static中
修改bootstrap配置文件settings.py如下

确认INSTALLED_APPS中有django.contrib.staticfiles
```{bash}
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]
```

静态文件夹设置 STATICFILES_DIRS变量如果只有一个元素，一定要写成元组形式，即(x,)，写成(x)这种是错误的
```{bash}
STATIC_URL = '/static/'
STATICFILES_DIRS = (os.path.join(BASE_DIR,"static"),)
]
```

#### 静态资源访问url映射
在django的urls.py中 添加如下代码
```{bash}
from django.contrib.staticfiles.urls import staticfiles_urlpatterns
urlpatterns += staticfiles_urlpatterns()
```

#### 引入静态资源
在html中文件开头加入 
```{bash}
{% load staticfiles %}
```
引用方式: 
```{bash}
{% static 'bootstrap-3.3.6-dist/css/bootstrap-theme.min.css' %}
```
