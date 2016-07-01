---
title: git使用(如何将远程库克隆到本地)
date: 2016-07-01 09:40:34
permalink: git_3
tags:
- git
- 开发工具
categories: 开发工具
---

### 如何将远程库克隆到本地
你是一个项目的新加入人员或者你换了一台电脑，想从远程库克隆代码到本地,还是以nodejs-hexo这个项目为例

1.在本地新建一个你想要放代码的目录,如 D:/github/blog

2. cd到D:/github/blog
命令：
```{bash}
$ git clone git@github.com:zjkevin/nodejs-hexo.git
```
你会发现在D:/github/blog下已经有nodejs-hexo项目

### 注
以上所有操作的前提都是你具体远程库的权限，并且在本地库目录下申明了你自己的账户信息
```{bash}
$ git config --global user.email "<youreamil>"
$ git config --global user.name "<username>"
```
