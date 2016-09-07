---
title: hexo的使用细节
date: 2016-06-30 16:35:31
tags:
 - hexo
 - 站点本身
categories: hexo
---

### hexo的原始日志文件 归档

hexo的原始日志文件位于source/_posts目录中，一旦文件一多，管理起来不方便，一种是按照年月归档，配置文件__config.yml中修改参数new_post_name: :year/:month/:title.md。

这种方式其实并不可取，因为按照人的思维方式应该按照分类归档更方便，一种方法是修改hexo的源代码增加分类参数，也可以直接在source/_posts下按照分类添加目录，创建新的md文件，直接在sublime等第三方编辑器中编写，不通过hexo命令行将不能使用hexo的模块，这部分欠缺通过sublime等支持模板功能的编辑器弥补。

修改hexo如下配置实现按类管理
```{bash}
修改配置文件__config.yml
此处添加自定义参数
permalink_defaults:
  kind: default

以下两次调用自定义参数
permalink: :kind/:title/
new_post_name: :kind/:title.md # File name of new posts

新建文章命令：
$ hexo new md_语法 --kind markdown
INFO  Created: H:\github\blog\nodejs-hexo\source\_posts\markdown\md-语法.md

```

使用第二种方法，这里不再赘述，每个人都有自己喜爱的编辑器

### 正文中不能使用的字符
```{bash}
正文中不能出现{% %}，要用这一类模板符号请包含在```{bash}   ```段中，有没有模板符号的转义符有待进一步了解
```