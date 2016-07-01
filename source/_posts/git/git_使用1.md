---
title: git使用(1)
date: 2016-07-01 08:49:17
permalink: git_2
tags:
- git
- 开发工具
categories: 开发工具
---

我们通过程序员惯用的思维方式展开，从问题出发，看用git该如何操作


### 如何将本地已有代码交给git托管
有一种项目是先有代码后来才想用git进行代码管理，以nodejs-hexo这个项目为例
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
4.将文件添加到本地库
```{bash}
$ git add *
$ git add .gitignore
```
5.提交到本地库
```{bash}
git commit -m "第一次签入"
```
6.本地库和远程库关联
```{bash}
git remote add origin git@github.com:zjkevin/nodejs-hexo.git
```
7.由于我们远程库中创建了一个README.md,所有要同步本地库跟远程库
```{bash}
git pull origin master
```
8.将本地的所有已经commit到本地库的文件push到远程库中
```{bash}
git push -u origin master
```

### 注
push -u参数 Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就不用再使用-u参数。也不必指定origin master

