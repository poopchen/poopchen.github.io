---
layout: default
title: 前端基础
nav_order: 7
permalink: /前端基础
has_children: true
has_toc: false
---

# 前端基础

## Html

不是编程语言，是标签语言



## css

css：层叠样式，是样式语言，不是编程语言

### 三种连接方法

1、外部文件。在head中添加<link>标签，链接css文件

![image-20230802095303253](http://img.chenpoop.top/image/202308020953334.png)

​	选择器：选择元素

​	声明：大括号里就是声明，声明里面是属性值

2、内部样式

3、内联样式：用style写样式，并放在元素中

### 层叠

顺序：顺序会影响样式

优先级：选择器有优先级关系

继承：可以继承父元素的样式。这个继承可以控制

### 选择器

元素选择器

ID选择器

类选择器

属性选择器

伪类选择器

### 盒子模型

![image-20230802100147552](http://img.chenpoop.top/image/202308021001640.png)

内边距：可以填充颜色

外边距：不能填充颜色

#### 块盒子（block）

div、img

每个盒子都换行

#### 内联盒子（inline）

不会产生换行

高度和宽度的属性不起作用

### 值和单位

时间单位：s

长度单位：

​	绝对长度：cm、mm、px

​	相对长度：em（相对父元素的字体大小）、rem

颜色值：十六进制RGB、RGBA（包含透明度）

### CSS布局

#### 显示绘制

布局：流式布局，从上到下，从左到右

绘制过程：

![image-20230802103145828](http://img.chenpoop.top/image/202308021031906.png)

#### 布局属性

absolute：相对父级元素（定位不为static的首个父元素），不保留原先元素的位置

relative：相对父级元素（定位不为static的首个父元素），保留原先元素的位置。会出现元素覆盖

fixed：相对视窗的定位（不是流式布局）

sticky：相对视窗，但是一开始是可以移动的。当它当固定的位置时，就粘在那里了（不是流式布局，一般用于导航栏，一维）

float：浮动布局。left、right

flex：弹性布局

grid：网格布局



z-index：覆盖的元素的层级高度，越大越前面

## JavaScript

脚本语言，用于创建动态更新的内容

通过<stript>标签添加外部js文件



### 基本语法和对象

#### 事件

为网页添加交互



### 文档对象模型DOM

Html和Xml的编程接口，对DOM树进行增删改查

- document.querySelector("p")：返回找到的第一个
- document.createElement("p")：创建js中的一个对象节点
- element.appendChild("p")：把创建的节点挂载到dom树中
- element.style：对dom的style进行操作



> VUE：不像Jquery，它是通过虚拟DOM树对真实dom进行监控，不用一直遍历查询，性能更好。

### 浏览器对象模型BOM

浏览器相关对象：

1. Window：窗口函数
2. location：地址栏相关
3. Navigator：浏览器本身信息
4. screen：屏幕对象
5. history：访问的堆栈



### 其他浏览器API

- 音视频：
- 客户端存储：
- 三维WebGL：



### Json

