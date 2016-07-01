---
title: git使用
date: 2016-07-01 08:49:17
permalink: git_2
tags:
- git
- 开发工具
categories: 开发工具
---

我们通过程序员惯用的思维方式展开，从问题出发，看用git该如何操作

### 如何将本地已有代码交给git托管
以nodejs-hexo这个项目为例
1.在远程服务器建立相应的repository
2.在本地你的代码根目录H:/github/blog/nodejs-hexo运行
命令：
```{bash}
$ git init
```
Initialized empty Git repository in H:/github/blog/nodejs-hexo/.git/
3.hexo项目有一些动态生成的文件是不需要交给git托管的，我们在代码根目录编辑文件**.gitignore** 添加如下不需要托管的内容
```{bash}
.DS_Store
Thumbs.db
db.json
*.log
node_modules/
public/
.deploy*/
```

### git诞生的原因

