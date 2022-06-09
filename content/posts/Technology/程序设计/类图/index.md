---
title: "类图"
subtitle: ""
date: 2022-06-04T17:26:13+08:00
lastmod: 2022-06-04T17:26:13+08:00
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
## 类描述

```yuml
// {type:class}
[≪IDisposable≫;Customer|+forname: string;+surname: string;-password: string|login(user,pass)]
```

一个类可以分为`类描述`、`变量常量描述`、`方法描述`三个区。

### 类图表示：

- 普通类，粗体；
- 接口，类名前要加`<<interface>>`修饰符；
- 抽象类，一般用粗斜体字，但是yuml没有这个字体，所以我只能`<<abstruct>>`。

#### 可见性修饰符

| 作用域    | 描述符 |
| --------- | ------ |
| public    | +      |
| protected | #      |
| private   | -      |
| package   | 空     |

### yuml语法

```
// {type:class}
[≪IDisposable≫;Customer|+forname: string;+surname: string;-password: string|login(user,pass)]
```

## 关系

类与类（接口）之间的关系有6种：

- 泛化（继承）
- 实现
- 关联
- 聚合
- 组合
- 依赖

### 泛化 空心箭

在JAVA中表示**继承**关系，采用空心箭头指向父类，yuml符号为^

```yuml
// {type:class}

[Person]^[Student]
```

### 实现  虚线空间箭

实现关系：是一种**继承**关系，表示子类继承父类的所有特征和行为。
关系连线：空心箭头指向父类。
yuml符号：^