---
title: django_创建项目
tags:
  - django
  - web框架
  - python
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

模板文件可以设置多个文件夹，应该也可以整合其他模板引擎,如jinja2,后面做demo尝试一把
模板文件的路径设置，修改HelloWorld/settings.py，修改 TEMPLATES 中的 DIRS 为 [BASE_DIR+"/templates",]，如下所示:
```{bash}
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [BASE_DIR+"/templates",],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```

### view中使用模板
我们使用了渲染器render，变量从context字典中赋值
```{bash}
#from django.http import HttpResponse
from django.shortcuts import render

def hello(request):
    context          = {}
    context['hello'] = 'Hello World!'
    return render(request, 'hello.html', context)
```