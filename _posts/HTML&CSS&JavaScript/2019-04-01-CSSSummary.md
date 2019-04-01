---
layout: post
title: "CSS个人常用样式"
subtitle: "CSS个人常用的属性及其取值的总结和演示"
date: 2019-04-01 18:00:00
author: "Lester Tan"
catalog: true
tags: 
    - CSS
    - html
    - 笔记
---

## 文本（Text）

|      属性       |            描述            |                             取值                             |           示例属性            |                           示例效果                           |
| :-------------: | :------------------------: | :----------------------------------------------------------: | :---------------------------: | :----------------------------------------------------------: |
|      color      |       设置文本的颜色       |                            颜色；                            |          color: blue          |         <span style="color:blue">For example</span>          |
| letter-spacing  |      增减字符间的空白      |     normal(默认)；<br/>*length*(px, em等，可以为负值)；      |    letter-spacing: 0.25em     |   <span style="letter-spacing: 0.25em">For example</span>    |
|   text-align    |   规定文本的水平对齐方式   |               left；<br/>right；<br/>center；                |              无               |                              无                              |
| text-decoration |    规定添加到文本的修饰    | none(默认)；<br/>underline；<br/>overline；<br/>line-through； | text-decoration: line-through | <span style="text-decoration: line-through">For example</span> |
|   text-indent   | 规定文本块中首行文本的缩进 |    *length*(默认为0)；<br/>*%*(基于父元素宽度的百分比)；     |              无               |                              无                              |
| text-transform  |      控制文本的大小写      | none(默认)；<br/>capitalize(每个单词的首字母大写)；<br/>uppercase；<br/>lowercase； |   text-transform: uppercase   |  <span style="text-transform: uppercase">For example</span>  |
|   white-space   |  设置如何处理元素内的空白  | normal(默认，空白合并，换行忽略)；<br/>pre(保留空白，保留换行)；<br/>pre-wrap保留空白，保留换行，有折行)；<br/>pre-line(合并空白，保留换行，有折行)；<br/>nowrap(空白合并，换行忽略，禁止折行)； |              无               |                              无                              |
|  word-spacing   |   增加或减少单词间的空白   |                normal(默认)；<br/>*length*；                 |     word-spacing: -0.2em      |    <span style="word-spacing: -0.2em">For example</span>     |
|   text-shadow   |  向文本添加一个或多个阴影  | (逗号分隔的阴影列表，每个阴影有两个或三个长度值和一个可选的颜色值进行规定。省略的长度是 0。)<br/>*h-shadow*(必需。水平阴影距离)；<br/>*v-shadow*(必需。垂直阴影距离)；<br/>*blur*(可选。模糊的距离)；<br/>*color*(可选。阴影的颜色)； |   text-shadow: 2px 2px red    |  <span style="text-shadow: 2px 2px red">For example</span>   |

## 字体（Font）

|     属性     | 描述                                 |                             取值                             |         示例属性         |                         示例效果                          |
| :----------: | ------------------------------------ | :----------------------------------------------------------: | :----------------------: | :-------------------------------------------------------: |
|     font     | 简写属性在一个声明中设置所有字体属性 | *font-style*；<br/>*font-variant*；<br/>*font-weight*；<br/>*font-size/line-height*；<br/>*font-family*； |            无            |                            无                             |
| font-family  | 规定元素的字体系列                   |               *family-name* *generic-family*；               |    font-family: serif    |    <span style="font-family: serif">For example</span>    |
|  font-size   | 设置字体的尺寸                       | xx-small；<br/>x-small；<br/>
small；<br/>
medium(默认)；<br/>
large；<br/>
x-large；<br/>
xx-large；<br/>smaller(比父元素小)；<br/>larger(比父元素大)；<br>*length*；<br/>*%*； |    font-size: larger     |    <span style="font-size: larger">For example</span>     |
|  font-style  | 定义字体的风格                       |             normal；<br/>italic；<br/>oblique；              |    font-style: italic    |    <span style="font-style: italic">For example</span>    |
| font-variant | 所有字母转换为小型大写               |                  normal；<br/>small-caps；                   | font-variant: small-caps | <span style="font-variant: small-caps">For example</span> |
| font-weight  | 设置文本的粗细                       | normal(400)；<br/>bold(700)；<br/>bolder；<br/>lighter；<br/>100~700； |    font-weight: bold     |    <span style="font-weight: bold">For example</span>     |

## 边框（Border和Outline）

|                    属性                     |                             描述                             |                             取值                             |                        示例属性                         |                           示例效果                           |
| :-----------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :-----------------------------------------------------: | :----------------------------------------------------------: |
|                   border                    |             简写属性在一个声明设置所有的边框属性             |  *border-width*；<br/>*border-style*；<br/>*border-color*；  |                           无                            |                              无                              |
|     border-bottom / left / right / top      |         在一个声明中设置所有的下/左/右/上边框属性。          |                              略                              |                           无                            |                              无                              |
|                border-color                 |                      设置四条边框的颜色                      |                          *color*；                           |                  border: solid yellow                   |    <span style="border: solid yellow">For example</span>     |
|                border-style                 | 设置元素所有边框的样式，或者独立为各边设置：<br/>上、右、下、左<br/>上、右左、下<br/>上下、右左 | none；<br/>hidden；<br/>dotted；<br/>dashed；<br/>solid；<br/>double；<br/>groove；<br/>ridge；<br/>inset；<br/>outset； |                   border-style:dotted                   |     <span style="border-style:dotted">For example</span>     |
|                border-width                 | 为元素的所有边框设置宽度，或者单独地为各边边框设置宽度：规则同上 |     thin；<br/>medium(默认)；<br/>thick；<br/>*length*；     |                   border: solid thin                    |     <span style="border: solid thin">For example</span>      |
|                   outline                   | 绘制于元素周围的一条线，位于边框边缘的外围，可起到突出元素的作用 |     *outline-color*；*outline-style*；*outline-width*；      |                           无                            |                              无                              |
|                outline-color                |                      设置整个轮廓的颜色                      |                          *color*；                           |                  outline:yellow solid                   |    <span style="outline:yellow solid">For example</span>     |
|                outline-style                |                   设置元素的整个轮廓的样式                   |                        同border-style                        |                     outline:double                      |       <span style="outline:double">For example</span>        |
|                outline-width                |                    设置元素整个轮廓的宽度                    |                        同border-width                        |                  outline: solid thick                   |    <span style="outline: solid thick">For example</span>     |
| border-bottom-left-radius(同理的另外三种略) |                     定义左下角边框的形状                     | (第一个值为水平半径，第二个值为垂直半径。只有一个值时为半径)；<br/>*length*；<br/>*%*； | border-style:dotted;<br/>border-bottom-left-radius: 1em | <span style="border-style:dotted;border-bottom-left-radius: 1em">For example</span> |
|                border-radius                |            简写属性设置四个 border-*-radius 属性             |                     *length*；<br/>*%*；                     |       border-style:dotted;<br/>border-radius: 1em       | <span style="border-style:dotted;border-radius: 1em">For example</span> |

---

<span style="font-size: 1.5em; font-family: 'Times New Roman'; border: solid rgb(150,0,200); border-radius: 0.75em; padding: 0.4em; margin: 0.4em; ">To be continued.</span>