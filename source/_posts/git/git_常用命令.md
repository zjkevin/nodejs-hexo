---
title: git 常用命令
date: 2016-07-01 10:28:34
permalink: git_4
tags:
- git
- 开发工具
categories: 开发工具
---

### git 常用命令

#### git库查看远程服务器信息
```{bash}
$ cat .git/config
}
```

#### git库查看本地分支
```{bash}
$ git branch
```

#### git库查看远程分支
```{bash}
$ git branch -r
```

***


做个翻译人员
```{bash}
usage: git [--version] [--help] [-C <path>] [-c name=value]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p | --paginate | --no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
           <command> [<args>]
```

#### 以下是git命令的不同应用场景
These are common Git commands used in various situations:

#### 开始一个工作域
```{bash}
start a working area (see also: git help tutorial)
   clone      Clone a repository into a new directory  
              从库中克隆一个项目到新的目录下
   init       Create an empty Git repository or reinitialize an existing one
              创建一个空的git库或者重新初始化一个已经存在的库
```

#### 日常操作
```{bash}
work on the current change (see also: git help everyday)
   add        Add file contents to the index
              添加文件内容到索引
   mv         Move or rename a file, a directory, or a symlink
              移动或者重命名一个文件、目录或者链接
   reset      Reset current HEAD to the specified state
              重置当前HEAD到一个指定的状态，HEAD 就是当前活跃分支的游标
   rm         Remove files from the working tree and from the index
              从本地工作区和索引去移除文件
```

#### 检查历史和状态
```{bash}
examine the history and state (see also: git help revisions)
   bisect     Use binary search to find the commit that introduced a bug
              二进制搜索查看引入bug的版本
   grep       Print lines matching a pattern
              筛选符合条件的行
   log        Show commit logs
              显示提交日志
   show       Show various types of objects
              显示详细信息
   status     Show the working tree status
              显示工作树状态
```

#### 分支操作
```{bash}
grow, mark and tweak your common history
   branch     List, create, or delete branches
              分支操作
   checkout   Switch branches or restore working tree files
   commit     Record changes to the repository
              提交到本地库
   diff       Show changes between commits, commit and working tree, etc
              差异比较
   merge      Join two or more development histories together
              合并
   rebase     Reapply commits on top of another base tip
              复用提交在另一个基础分支上
   tag        Create, list, delete or verify a tag object signed with GPG
              tag操作
```

#### 协作              
```{bash}
collaborate (see also: git help workflows)
   fetch      Download objects and refs from another repository
              下载
   pull       Fetch from and integrate with another repository or a local branch
              拉取
   push       Update remote refs along with associated objects
              推送
```