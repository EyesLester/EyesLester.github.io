---
layout: post
title: "JavaScript DOM编程艺术笔记1"
subtitle: "JavaScript DOM编程艺术第1~4章的要点笔记"
date: 2019-04-01 00:00:00
author: "Lester Tan"
catalog: true
tags: 
    - JavaScript
    - DOM
    - html
    - 笔记

---

## 第1章（JavaScript简史）

**DOM**是一种API（应用编程接口），W3C对DOM的定义是：“一个与系统平台和编程语言无关的接口，程序和脚本可以通过这个接口动态地访问和修改文档的内容、结构和样式。”，它可以让*任意一种*程序设计语言对使用*任何一种*标记语言编写出来的*任何一份*文档进行操控。



## 第二章（JavaScript语法）

### 数组

向数组中添加元素的操作称为**填充（populating）**

声明数组并填充：

```javascript
var beatles = Array(4);//也可以在声明数组时不给出元素个数
beatles[0] = "John";
beatles[1] = "Paul";
beatles[2] = "George";
beatles[3] = "Ringo";
```

有一种相对简单的填充数组方式：

```javascript
//两者皆可
var beatles = Array("John","Paul","George","Ringo")；
var beatles = ["John","Paul","George","Ringo"];
```

关联数组(字符串下标)：

```javascript
var lennon = Array();
lennon["name"] = "John";
lennon["year"] = 1940;
lennon["living"] = false;
```

-----

**To be continued.**

