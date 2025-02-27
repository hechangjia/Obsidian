---
title: Git学习总结
author:
  - charlie
date: 2025-02-25-11-18
description: This is a self-concluded tutorial to "master" and apply git.
categories:
  - 资料整理
  - 笔记
  - git
tags:
  - notes
  - git
  - 个人总结
created: 
rating: 9
banner: "[[lovley.png]]"
---
> [!key] 阅读提示
> 有关git的介绍我放到了文章最后[^1],想要了解的话,可以自行上网查询,以下是有关链接:
>
> 1. [Wikipedia](https://zh.wikipedia.org/wiki/Git)
> 2. [廖雪峰的Git教程](https://liaoxuefeng.com/books/git/introduction/index.html)
> 3. [git入门网站](https://learngitbranching.js.org/?locale=zh_CN)


# git基本操作

## $\aleph 1$`git -v`or`git --version`

查询当前git的安装版本.确保自己已经安装了**git**.😜
```bash
(base) charlie@charlie:~$ git -v
git version 2.43.0
```

若没有正常的信息显示的话🤣,先去官网安装.[git官网安装地址](https://git-scm.com/downloads)😆

## $\aleph 2$`git init`

**顾名思义,就是使当前文件夹被git初始化,也就是开始被git追踪.**

***假定我们创建了这样一个文件夹`git-demo`[^2]***

现在打开这个文件夹的终端,进行操作:
```bash
(base) charlie@charlie:~/桌面/git-demo$ git init
提示：使用 'master' 作为初始分支的名称。这个默认分支名称可能会更改。要在新仓库中
提示：配置使用初始分支名，并消除这条警告，请执行：
提示：
提示：	git config --global init.defaultBranch <名称>
提示：
提示：除了 'master' 之外，通常选定的名字有 'main'、'trunk' 和 'development'。
提示：可以通过以下命令重命名刚创建的分支：
提示：
提示：	git branch -m <name>
已初始化空的 Git 仓库于 /home/charlie/桌面/git-demo/.git/
```

表明这个文件夹`git-dmeo`已经被git追踪了,并且还会在该文件夹下生成一个`.git`文件:

![[Pasted image 20250225114651.png]]

## `git help`以及`git [command] -help`

输入git help命令会显示所有的帮助,当然我们不需要这么多,那么当我们想要查询特定某条命令的帮助时,比如上文提到的`git init`命令,以及接下来的命令`git status`,`git log`,`git branch`等命令,就可以这样操作.
```bash
(base) charlie@charlie:~/桌面/git-demo$ git init -help
用法：git init [-q | --quiet] [--bare] [--template=<template-directory>]
                  [--separate-git-dir <git-dir>] [--object-format=<format>]
                  [-b <branch-name> | --initial-branch=<branch-name>]
                  [--shared[=<permissions>]] [<directory>]

    --[no-]template <模板目录>
                          模板目录将被使用
    --[no-]bare           创建一个纯仓库
    --shared[=<权限>]     指定 git 仓库是多个用户之间共享的
    -q, --[no-]quiet      静默模式
    --[no-]separate-git-dir <git目录>
                          git目录和工作区分离
    -b, --[no-]initial-branch <名称>
                          覆盖初始分支名称
    --[no-]object-format <hash>
                          指定要使用的哈希算法

```

## 比较常用的命令之一:`git status`

查询当前git所追踪的文件的状态.

当我们在上一个命令`git init`后,在输入命令`git status`:
```bash
(base) charlie@charlie:~/桌面/git-demo$ git status
位于分支 master

尚无提交

无文件要提交（创建/拷贝文件并使用 "git add" 建立跟踪）
```
其中有三行消息:
1. 位于分支 master:显示当前分支:默认是master分支.有时也会是main等分支.
2. 尚无提交:commit命令
3. 无文件要提交（创建/拷贝文件并使用 "git add" 建立跟踪）

现在第二三条都有点不明了,是因为,我们还没有在该文件夹下创建相关文件.现在创建一个`readme.md`文档(相当于一个自我介绍.)
```bash
(base) charlie@charlie:~/桌面/git-demo$ git status
位于分支 master

尚无提交

未跟踪的文件:
  （使用 "git add <文件>..." 以包含要提交的内容）
	readme.md

提交为空，但是存在尚未跟踪的文件（使用 "git add" 建立跟踪）
```

好,现在总体上依然是三行信息:
1. 分支还是在master
2. 提示我们使用`git add [文件名]`的命令建立跟踪(track)
3. ??提交为空.

**进入下一条命令.**
## 比较常用的命令之二:`git add`[^3]

新手连招:`git status`+其他命令+`git status`:
```bash
(base) charlie@charlie:~/桌面/git-demo$ git add .
(base) charlie@charlie:~/桌面/git-demo$ git status
位于分支 master

尚无提交

要提交的变更：
  （使用 "git rm --cached <文件>..." 以取消暂存）
	新文件：   readme.md

```
好,现在还是三行提示:
1. 还是位于master分支上
2. 所有文件都追踪了(be tracked)
3. 但有文件没有提交,而提交的文件恰好是我们刚刚提交的文件.[^4]














> [!note]
> 按照脚注4的说法的话,那么`git branch`就相当于给自己找来一个替身来做实验喽.





[^1]: 直接进入实战吧.

[^2]: 位置随意.

[^3]: 建议使用`git add .`or `git add -A`命令,一次性无脑添加所有没有被track或者modefied的文件.

[^4]: 这和Git的运作模式有关.就是刚开始的时候,我们添加readme文件,还没有输入`git add .`命令,就再把readme文件删除或者移除该文件夹,那么输入`git status`就会和之前一样.也就是说:git不会立马自动的对文件夹的文件追踪,需要用户自己使用一系列命令,主流就是`git add .`和`git commit -m "描述"`来追踪.`git add .`使得使文件被追踪,相当于拍照的时候,化妆师而你,觉得怎么样了,不满意可以撤销[^5],`git commit -m "描述"`就相当于你的妆画好了,对摄影师说,拍下现在`美美`的我吧.这样,就会有一张照片记录下了当下你的所有内容.
[^5]: `git rm --cached <文件>...` 以取消暂存.















# Picture

![photo by Jonas Jacobsson(https://unsplash.com/@jonasjacobsson?utm_source=templater_proxy&utm_medium=referral) on Unsplash](https://raw.githubusercontent.com/hechangjia/Picture_Deposit/master/photo-1535488518105-67f15b7cab27)

![photo by Yoksel 🌿 Zok(https://unsplash.com/@yoksel?utm_source=templater_proxy&utm_medium=referral) on Unsplash](https://images.unsplash.com/photo-1631376158521-7055df9fba09?crop=entropy&cs=srgb&fm=jpg&ixid=M3w2NDU1OTF8MHwxfHJhbmRvbXx8fHx8fHx8fDE3NDA0NTM1MDZ8&ixlib=rb-4.0.3&q=85&w=200&h=200)

![photo by Ivana Cajina(https://unsplash.com/@von_co?utm_source=templater_proxy&utm_medium=referral) on Unsplash](https://raw.githubusercontent.com/hechangjia/Picture_Deposit/master/photo-1500534314209-a25ddb2bd429)

![photo by Roma R(https://unsplash.com/@n3moy?utm_source=templater_proxy&utm_medium=referral) on Unsplash](https://images.unsplash.com/photo-1451903978882-b165bd94e45d?crop=entropy&cs=srgb&fm=jpg&ixid=M3w2NDU1OTF8MHwxfHJhbmRvbXx8fHx8fHx8fDE3NDA0NTM1MDV8&ixlib=rb-4.0.3&q=85&w=200&h=200)

