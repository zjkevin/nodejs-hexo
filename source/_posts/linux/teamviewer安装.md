---
title: teamviewer安装
tags:
  - linux
  - 默认
categories: linux
kind: linux
date: 2017-02-04 14:18:16
permalink: teamviewer_install
---

#### 在debian 8上安装
```{bash}
sudo dpkg -i teamviewer_12.0.71510_i386.deb
#添加32位架构
sudo dpkg --add-architecture i386
sudo dpkg --print-architecture  
sudo dpkg --print-foreign-architectures
#尝试安装离线包
sudo dpkg -i ia32-libs-i386_0.4_i386.deb
#离线包有依赖项，以下语句安装依赖项  
sudo apt-get -f --force-yes -y install
#再次安装离线包
sudo dpkg -i ia32-libs-i386_0.4_i386.deb
#安装32位teamviewer包，64位包跟当前机器上的其他软件依赖的包冲突，安装32位包可以使用       
sudo dpkg -i teamviewer_12.0.71510_i386.deb
```
