---
title: 如果使用hexo搭建个人blog
date: 2016-06-30 11:10:24
updated: 2016-06-30 11:19:00
permalink: hexoblog
tags:
- hexo
- 站点本身
categories: hexo
---

这是**新的开始**，我用hexo搭建blog并且写了第一篇文章

hexo的安装，用全局安装，加参数-g
```{bash}
$ npm install -g hexo
```

查看一下hexo的版本
```{bash}
$ hexo version
hexo-cli: 1.0.2
os: Windows_NT 6.1.7601 win32 x64
http_parser: 2.7.0
node: 6.2.1
v8: 5.0.71.52
uv: 1.9.1
zlib: 1.2.8
ares: 1.10.1-DEV
icu: 57.1
modules: 48
openssl: 1.0.2h
```

使用hexo创建项目，先cd到你打算放blog源码的文件夹下
```{bash}
$ hexo init <project_name>
```

cd到项目根目录,通过下面的命令，就可以创建新文章
```{bash}
$ hexo new <title>
$ hexo new <title> --kind "<类别名称>" # 对hexo代码做了一些修改，支持--kind参数 指定类别，source/_posts/下会新建类别文件夹，存在则pass

$ hexo new draft new <title> --kind "<类别名称>" # 创建草稿
$ 
```

启动hexo服务器
```{bash}
$ hexo server
```

静态化处理
```{bash}
$ hexo generate
```

发布到github

先安装nexo的git发布工具
```{bash}
$ npm install hexo-deployer-git --save
```

编辑 _config.yml_
```{bash}
deploy:
- type: git
  repo:
      github: git@github.com:zjkevin/zjkevin.github.io.git
      coding: git@git.coding.net:zjkevin/blog.git,coding-pages

- type: rsync
  host: 106.185.49.121
  user: root
  root: /var/www/zhangjiesoftcom/
  port: 22


```

发布
```{bash}
$ hexo deploy
```

参考：
[hexo官网](https://hexo.io/)
[使用hexo搭建静态站点](http://blog.fens.me/hexo-blog-github/)

注意：配置git的deploy，参考链接的方式已经失效，请以本文为准


scp -P <port> -r .deploy_git/* pi@xxx.xxx.xxx:/var/www/hexo