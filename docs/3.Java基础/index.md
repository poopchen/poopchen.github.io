---
layout: default
title: Java基础
nav_order: 3
permalink: /Java基础
has_children: true
has_toc: false
---

# Java基础



java虚拟机（JVM）

垃圾回收（GC）

java运行时环境



java中的堆、栈



基本类型

引用类型



基本类型

char：单引号' '

string：不是基本类型，是一个类

浮点类型：double、float。防止精度问题，用bigdecimal



## 表达式、运算符

“+” 除了运算符外，可以连接字符串

字符串比较：== 和equal不一样，要用equal比较值是不是一样；==判断两个对象的地址



## 类和对象

面向对象：封装、继承、多态

Private：

protected：

public：



package：防止类同名冲突

import：告诉编译器去哪个包加载类

## Java集合

接口：Collection、Map、Iterator

![image-20230728151834667](http://img.chenpoop.top/image/202307281518788.png)

实现类有：List、Set、Map

List：有序的，可重复的

Set：无顺序的，不可重复

Map：不可重复，无序的

泛型<>不能使用基本类型，所以是各基本类型的包装类

### List

ArrayList：基于数组，随机访问性能好

LinkedLIst：基于链表，插入删除性能好

### Set

迭代器：hasNext、Next方法

Set：hashSet、TreeSet

### Map

HashMap：哈希表，便于插入删除

TreeMap：红黑树，便于排序

### 线程安全

多线程进行集合操作是否会出问题

vector线程安全

ArrayList、LinkedList、HashMap、TreeMap都不是线程安全的

### 常用方法

comparable：比较方法

sort：升序

reverse：反转

min、max

### 多线程

线程是系统最小单元

同一进程下线程共享资源



使用场景：

tomcat内部采用多线程

后台任务

异步处理



实现方法：继承Thread、Runable接口

互斥和同步



synchronized

### 排序

Comparable ：单一的排序方法

Comparator ：可以定义多种排序方法

## 数据库

### ACID

原子性、一致性、隔离性、持续性

# IDEA快捷键

Getter和Setter方法的快捷键：右键greater