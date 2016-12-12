---
title: grub2_基本操作
tags:
  - linux
  - 操作系统
  - debian
categories: linux
kind: linux
date: 2016-11-17 15:45:04
---

#### grub2配置文件

    /boot/grub/grub.cfg
    /etc/default/grub

系统启动后读取grub.cfg文件，而/etc/default/grub是用来修改grub.cfg文件的配置文件，修改/etc/default/grub,然后使用update-grub2命令使得修改生效。当然你也可以直接修改grub.cfg文件。grub.cfg文件是一个shell脚本，如果不懂shell的同学，不要轻易修改，以免系统无法启动，那样就需要修复该shell文件。

#### 修改grub2启动时间
修改timeout属性的数值，单位为秒

#### 修改grub2启动顺序
根据你安装的操作系统数目，以0为索引起点，如果你想让grub2开机菜单中的第三个行为启动点，请将/boot/grub/grub.cfg中的default修改为2
