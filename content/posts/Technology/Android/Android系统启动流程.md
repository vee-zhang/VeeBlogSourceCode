---
title: "Android系统启动流程"
subtitle: ""
date: 2022-03-09T17:32:28+08:00
lastmod: 2022-03-09T17:32:28+08:00
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


  1. 按下电源键，首先从加载并运行BootLoader；
  2. BootLoader拉起linux内核；
  3. linux内核启动后会加载init.rc文件，并启动init进程。
  4. init进程会启动属性服务，并启动Zygote进程。
  5. Zygote进程会创建JVM并注册JNI，创建服务端Socket,启动SystemServer进程。
  6. SystemServer启动Binder线程池和SystemServiceManager及各种系统服务。
  7. 启动Launcher。
