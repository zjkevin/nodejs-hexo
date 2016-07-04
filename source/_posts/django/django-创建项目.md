---
title: django_创建项目
tags:
  - django
  - 默认
categories: django
kind: django
date: 2016-07-04 15:31:50
---

### django创建项目

创建一个项目:
```{bash}
$ django-admin.py startproject cmdb_web
```

启动web服务
```{bash}
$ python3 manage.py runserver 0.0.0.0:8000
```

### 新建视图

站点根目录 新建view.py
```{bash}
from django.http import HttpResponse

def hello(request):
    return HttpResponse("Hello world ! ")
```

### 设置路由

打开文件urls.py
```{bash}
from django.conf.urls import *
from HelloWorld.view import hello

urlpatterns = patterns("",
    ('^hello/$', hello),
)
```

### 使用模板
根目录下创建templates目录并建立hello.html文件
```{bash}
<h1>{{ hello }}</h1>
```


