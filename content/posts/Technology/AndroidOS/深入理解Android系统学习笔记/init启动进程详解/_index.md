---
title: "Index"
subtitle: ""
date: 2023-04-03T14:52:09+08:00
lastmod: 2023-04-03T14:52:09+08:00
draft: false
authors: []
description: ""

tags: []
categories: []
series: [深入理解Android系统学习笔记]

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

## 从按下电源键那一刻起

从按下电源键的那一刻，会先起动一个小程序`BootLoader`，BootLoader会启动Linux内核，并通过**参数**告诉内核『启动后去运行init进程』。



