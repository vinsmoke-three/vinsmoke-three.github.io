---
layout: post
title: java学习笔记：面向对象的内存分析
category: java
tags: [java]
---

程序的执行过程中，内存到底发生了什么变化？

Java虚拟机的内存可以分为三个区域：栈stack、堆heap、方法区method area。

※方法区method area实际上属于堆heap

## 栈的特点

　　1. 栈描述的是方法执行的内存模型。每个方法被调用都会创建一个栈帧(存储局部变量、操作数、方法出口等)

　　2. JVM为每个线程创建一个栈，用于存放该线程执行方法的信息(实际参数、局部变量等)

　　3. 栈属于线程私有，不能实现线程间的共享!

　　4. 栈的存储特性是“先进后出，后进先出”

　　5. 栈是由系统自动分配，速度快!栈是一个连续的内存空间!

## 堆的特点

　　1. 堆用于存储创建好的对象和数组(数组也是对象)

　　2. JVM只有一个堆，被所有线程共享

　　3. 堆是一个不连续的内存空间，分配灵活，速度慢!

## 方法区（又叫静态区）特点

　　1. JVM只有一个方法区，被所有线程共享!

　　2. 方法区实际也是堆，只是用于存储类、常量相关的信息!

　　3. 用来存放程序中永远是不变或唯一的内容。(类信息【Class对象】、静态变量、字符串常量等)

## 关于JVM执行代码的图解

   1.被调用的方法会依次堆栈，执行的时候是从栈顶开始执行，执行完毕该栈块就会被释放掉！即先进后出，后进先出

   2.所有的对象都存活于可被垃圾回收的堆上

   3.变量存在于哪个空间要看它是哪种变量，实例变量 或 局部变量（栈变量）

![](/assets/images/java/2020/20200119.jpg)
