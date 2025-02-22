---
title: dataview语法
author:
  - charlie
created: 
description: 这是一篇记录dataview插件学习的笔记
categories:
  - 读书笔记
  - 小说
tags:
  - "#笔记"
  - "#总结"
  - "#dataview"
  - "#obsidian"
rating: "9"
banner: "[[lovley.png]]"
---
[最简单的教程](https://forum-zh.obsidian.md/t/topic/195)

> [!note] 
> **先上实操和应用,介绍之类的待会再讲,先看看他能做什么**


# 最小示例

### 下边是一段代码，查询出所有包含标签 `#word` 的笔记：

代码:


```dataview
table
from #word 

```

### 下边是一段代码，查询出所有包含标签 `#总结 `的笔记：

```dataview
LIST
from #总结 
```
### 下边是一段代码，查询出所有包含作者 `charlie` 的笔记：

```dataview
list
from ""
where contains(author, "charlie")
```

```dataview
table
from #clippings
```


1.  list , table ,task, CALENDAR



