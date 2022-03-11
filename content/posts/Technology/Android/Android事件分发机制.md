---
title: "Android事件分发机制"
subtitle: ""
date: 2022-03-10T18:52:30+08:00
lastmod: 2022-03-10T18:52:30+08:00
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
## 传递流程
Activity->PhoneWindow->DecorView->Content->ViewGroup->View

## 三大函数

- `dispatchTouchEvent`，是事件传递的主要方法，首先判断是否需要拦截事件（ViewGroup中），如果需要拦截，就会调用自己的onTouchEvent，如果无需拦截，就遍历子View，由子View处理事件。
- `onInterceptTouchEvent`，用来判断是否需要拦截下事件并且由自己的onTouchEvent处理。
- `onTouchEvent`，用来处理消费事件，返回true代表消费掉事件，不再向上冒泡。