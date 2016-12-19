---
title: git服务器搭建
permalink: git_server
tags:
  - git
  - 默认
categories: git
kind: git
date: 2016-12-19 20:27:30
---

### 创建裸仓库
git init --bare xxxx.git

### 添加用户和组
groupadd git
adduser git -g git

### 修改git的shell
chsh git
修改为 /usr/bin/git-shell

### 修改裸仓库的所有权限
chown -R git:git xxx.git

### 管理公钥
/home/git/.ssh/authorized_keys

管理大量公钥，研究Gitosis
变态的权限控制，研究Gitolite

git clone git@xxxxxxxxx:/var/www/hexo_web.git
git clone ssh://xxxxxxxxxxx:<port>/var/www/hexo_web.git



