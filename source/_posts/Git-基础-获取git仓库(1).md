---
title: Git 基础-获取git仓库
categories: Git
resources: ''
date: 2022-11-09 10:40:07
tags: git
comments: true
copyright: true
---

#### 获取Git仓库

两种方式：

1. 将尚未进行版本控制的本地目录转换为 Git 仓库；
2. 从其它服务器 **克隆** 一个已存在的 Git 仓库。

##### 在已经存在的目录中初始化

切换到项目目录，执行

```powershell
ericr@Think-Eric MINGW64 /e/Documents/GitHub/gitnotes
$ git init
Initialized empty Git repository in E:/Documents/GitHub/gitnotes/.git/

ericr@Think-Eric MINGW64 /e/Documents/GitHub/gitnotes (main)
$
```

该命令将创建一个名为 `.git` 的子目录，这个子目录含有你初始化的 Git 仓库中所有的必须文件。

<!--more-->

接下来就应该追踪这些文件并进行初始提交。 可以通过 `git add` 命令来指定所需的文件来进行追踪，然后执行 `git commit` ：

```powershell
ericr@Think-Eric MINGW64 /e/Documents/GitHub/gitnotes (main)
$ echo "git study notes" >> README.md
ericr@Think-Eric MINGW64 /e/Documents/GitHub/gitnotes (main)
$ ll
total 1
-rw-r--r-- 1 ericr 197609 16 Nov  9 10:53 README.md
ericr@Think-Eric MINGW64 /e/Documents/GitHub/gitnotes (main)
$ git add README.md
warning: in the working copy of 'README.md', LF will be replaced by CRLF the next time Git touches it
ericr@Think-Eric MINGW64 /e/Documents/GitHub/gitnotes (main)
$ git commit -m 'initial gitnotes version'
[main (root-commit) 36f316a] initial gitnotes version
 1 file changed, 1 insertion(+)
 create mode 100644 README.md

```

##### 克隆现有的仓库

执行`git clone` ,与源仓库同名

```shell
ericr@Think-Eric MINGW64 /e/Documents
$ git clone https://github.com/x-artspace/blogs.git
Cloning into 'blogs'...
```

如果你想在克隆远程仓库的时候，自定义本地仓库的名字，你可以通过额外的参数指定新的目录名：

```shell
ericr@Think-Eric MINGW64 /e/Documents
$ git clone https://github.com/x-artspace/blogs.git myblogs
Cloning into 'blogs'...
```

##### Git传输协议

Git 支持多种数据传输协议。 

上面的例子使用的是 `https://` 协议，不过你也可以使用 `git://` 协议或者使用 SSH 传输协议，比如 `user@server:path/to/repo.git` 。