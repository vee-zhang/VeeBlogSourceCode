---
title: Android页面绘制流程
date: 2021-06-21 17:49:10
tags: [Android]
---

## WMS(WindowManagerService)

用来管理各个窗口：

- 当前激活(显示)状态的window；
- 后面即将激活(显示)的window;
- StatusBar;
- Sub Window弹出子窗口；
- WallpaperWindow壁纸窗口；
- Input Method Window输入法窗口。

决定各个窗口的显示区域。

## 核心类

- `ViewRoot` ViewTree的管理者，持有mView成员变量，指向的就是它所管理的viewTree的根，而viewRoot主要用来与WMS()进行通信；
- 