---
title: "Android系统启动流程"
subtitle: ""
date: 2021-07-28T16:15:50+08:00
lastmod: 2021-07-28T16:15:50+08:00
draft: false
authors: []
description: "xxxx什么垃圾玩意儿，看的头疼"

tags: [Android]
categories: []
series: [AndroidFramework]

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
### 内核空间流程

1. 按下开机键。
2. 加载启动引导程序bootloader到内存并执行。
3. 拉起linux内核，设置缓存，加载驱动.

### 用户空间流程

1. 内核启动后，启动init进程(pid=1)调用init的入口main函数。
2. 创建和挂载文件目录。
3. 初始化并启动【属性服务】。
4. 注册子进程信号处理函数，用来处理进程终止信号，防止僵尸进程。
5. 解析init.rc文件，并启动Zygote。          
6. 根据不同系统读取不同的init。zygotexx.rc启动zygote进程（孵化器）。
7. 启动SystemServer
8.  创建launcher

### Zygote启动流程

1. 创建JVM;
2. 通过JNI调用`ZygoteInit`这个类的`main`函数，开始**进入java框架层*(´▽`ʃ♡ƪ)；
3. 创建一个Socket服务端；
4. fork出SystemServer进程（该进程中启动系统服务）；
5. 调用`zygote.runSelectLoop`死循环，开始监听AMS的请求。   

### SystemServer的处理过程

`SystemServer`进程用来创建系统服务，如AMS、WMS和PMS等。

1. `ZygoteInit.java`的`startSystemServer`中启动`SystemServer`进程。
2. 启动`PathClassLoader`