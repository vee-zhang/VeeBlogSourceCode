---
title: Android虚拟机
date: 2021-06-21 16:24:04
tags: [Android]
---

## Dex文件格式

![dex文件结构](/images/dex文件详解.png))

从图中可以看出：

当java程序编译成class文件后，Android编译器会使用dx工具把所有的class文件的各个部分（成员、常量等）**整合到一个dex文件**，目的是使其中的类可以共享数据，在一定程度上降低了荣誉，同时也使文件结构更加紧凑。

好处就是当Android虚拟机加载类时，只需要一次IO就可以加载很多类，提高了加载效率。

>我尝试弄了个Apk文件，解压之后发现只有一个`classes.dex`文件，而如果是jar包的话经解压会出现多个`.class`文件。

## Android虚拟机Dalvik

每一个运行的应用都有一个Dalvik实例。Dalvik虚拟机用来处理dex文件。

JVM是基于虚拟栈的，而Dalvik是基于寄存器的。

## ART与Dalvik

- Dalvik 执行dex字节码，解释执行，从Android2.2开始支持JIT即时编译。（在程序运行时选择热点代码进行编译或者优化）。
- ART Android5.0默认使用预先AOT编译，Apk在安装时会把dex提取出来，转为odex文件，其实就是把字节码编译成机器码，所以ART虚拟机可以直接执行机器码。

从Android7.0起开始使用混合编译，apk安装之后不再预先AOT了，而是直接JIT运行，对于JIT编译后的方法记录到一个profile，当设备闲置时通过守护进程，对profile中的常用代码进行AOT编译。

## Android的ClassLoader

```java
public abstract class ClassLoader{...}

class BootClassLoader extends ClassLoader{...}
```

在抽象类ClassLoader的文件中，存在一个`BootClassLoader`，负责加载JVM内置的类。

>以前我记得是不可以在同一个.java文件中写多个类的，今天看到这里傻了眼，百度后得知，如果一个文件中写了多个类，那么只能有一个可以用public标注。

BootClassLoader负责系统framework中的类的加载。

PathClassLoader负责第三方库中的类的加载。

为什么要双亲委派？

1. 避免重复加载，造成IO浪费；
2. 考虑安全性，防止核心库API被篡改。

热修复插入补丁的时机：

在Application的`attchBaseContext()`方法中检测是否存在补丁包，如果存在，就主动去加载补丁包，由于ClassLoader只加载一次的策略，旧的类就不会被加载了，这样就完成了热更新、热修复。