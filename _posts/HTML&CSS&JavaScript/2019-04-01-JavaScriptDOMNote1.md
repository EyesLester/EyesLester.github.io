---
layout: post
title: "JavaScript DOM编程艺术笔记1"
subtitle: "JavaScript DOM编程艺术第1~4章的要点笔记"
date: 2019-04-01 13:00:00
author: "Lester Tan"
catalog: true
tags: 
    - JavaScript
    - DOM
    - html
    - 笔记

---

## 第1章（JavaScript简史）

**DOM**是一种API（应用编程接口），W3C对DOM的定义是：“一个与系统平台和编程语言无关的接口，程序和脚本可以通过这个接口动态地访问和修改文档的内容、结构和样式。”，它可以让<span style="text-decoration: underline">任何一种</span>程序设计语言对使用<span style="text-decoration: underline">任何一种</span>标记语言编写出来的<span style="text-decoration: underline">任何一份</span>文档进行操控。



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
var beatles = Array("John","Paul","George","Ringo");
var beatles = ["John","Paul","George","Ringo"];
```

关联数组(字符串下标)：

```javascript
var lennon = Array();
lennon["name"] = "John";
lennon["year"] = 1940;
lennon["living"] = false
```

通过`Array`对象的`length`属性可以获得数组元素个数，例如`beatles.length`

### 操作符

`==`不表示严格相等，如表达式`false == ""`的值为真，因为相等操作符认为空字符串和false含义相同。要进行严格比较时使用全等操作符`===`，它会比较值和类型。

相似地，表示不相等的`!=`和`!==`也是如此。

### 对象

JavaScript中对象分为**用户定义对象（user-defined object）**、**内建对象（native object）**、**宿主对象（host object）**。

内建对象包括`Array`、`Math`、`Date`等。

宿主对象包括`Form`、`Image`、`Element`等。我们可以通过这些对象获得关于网页上表单、图像和各种表单元素等的信息。`document`也是宿主对象，它可以用来获得网页上任何一个元素的信息。

## 第3章（DOM）

**DOM**: document, object, model(把文档表示为一棵树)

DOM的原子是**元素节点（element node）**，元素节点包含**文本节点（text node）**和**属性节点（attribute node）**。（注：XHTML文档中，文本节点总是被包含在元素节点内部）

| API                                                          | 描述                                               |
| ------------------------------------------------------------ | -------------------------------------------------- |
| getElementById(id)                                           | 通过元素id获取元素节点，返回一个对象               |
| getElement<span style="text-decoration: underline red">s</span>ByTagName(tag) | 通过标签获取元素节点，返回一个对象数组             |
| getElement<span style="text-decoration: underline red">s</span>ByClassName(class) | 通过class属性类名获取元素节点，返回一个对象数组    |
| object.getAttribute(attribute)                               | 似乎只能获取属性初始值，使用object.attribute可解决 |
| object.setAttribute(attribute, value)                        | 修改属性节点的值                                   |

## 第4章（案例研究：JavaScript图片库）

当给某个元素添加了事件处理函数后，相应的JavaScript代码就会得到执行。被调用的JavaScript代码可以返回一个值，这个值将被传递给那个事件处理函数。例如，我们可以给某个链接添加一个`onclick`事件处理函数，并让这个处理函数所触发的JavaScript代码返回布尔值`true`或`false`。这样一来，当这个链接被点击时，如果那段JavaScript代码返回的值是`false`，`onclick`事件处理函数就认为"这个链接没有被点击"。

例如以下代码：

```html
<a href="https://lestertan.ink" onclick="return false;">Click me</a>
```

<a href="https://lestertan.ink" onclick="return false;">Click me</a> 当点击这个链接时，因为`onclick`事件处理函数触发的JavaScript代码返回值是`false`，所以这个链接的默认行为没有被触发。

利用这个原理，可以防止用户被带到目标链接窗口：

```html
<!--showPic(this)表示调用showpic()函数时传入的参数为该对象本身-->
<a href="images/fireworks.jpg" onclick="showPic(this); return false;">Click me</a> 
```

把`window.onload = countBodyChildren;`语句添加到代码段尾部可以使 `countBodyChildren`函数在页面加载时被调用。

| 属性                        | 描述                                                         |
| --------------------------- | ------------------------------------------------------------ |
| element.childNodes          | 包含这个元素全部子元素的数组                                 |
| node.nodeType               | 获取节点的属性值，一共有12种可能，其中有实用价值的有3种（1：元素节点，2：属性节点，3：文本节点） |
| node.nodeValue              | 获取节点的值（对于\<p\>元素，其文本为.childNodes[0].nodeValue，而非其本身的nodeValue），也可以用来设置节点的值 |
| node.firstChild / lastChild | node.childNodes[0] 与 node.childNodes[node.childNodes.length-1] |

