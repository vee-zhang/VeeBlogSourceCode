---
title: "学习Makefile"
subtitle: ""
date: 2023-04-10T09:26:26+08:00
lastmod: 2023-04-10T09:26:26+08:00
draft: false
authors: []
description: ""

tags: []
categories: []
series: []

hiddenFromHomePage: false
hiddenFromSearch: false

featuredImage: ""
featuredImagePreview: ""

toc:
  enable: true
math:
  enable: false
lightgallery: false
license: ""
---

<!--more-->

## 语法

```makefile
<target1 > <target2>.... : <prerequisites1> <prerequisites2>...
[TAB] <command1>
[TAB] <command2>
...
```

- target：可以是object file（目标文件）、可执行文件、标签(label)
- prerequisites：要生成那个target所需的文件或目标
- command：make所需执行的指令。

