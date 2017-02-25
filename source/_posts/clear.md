---
title: css清除浮动较常用的三种方法
date: 2017-02-15 10:36:59
tags: css
---

在页面布局中浮动是一个很常用的属性，但使用浮动也会使元素脱离正常文档流造成父级高度的塌陷，因此随时清除浮动是css书写时的一个良好的习惯，以下介绍清除浮动的几种常用的方法：

### 1.使用空标签清除浮动。

实现方法为在父级元素内所有的浮动元素后添加一个空元素
```
<div class="f">
 <div class="a"></div>
 <div class="b"></div>
 <div class="clear"></div>
</div>
```
<!--more-->
其css样式为
```
.f{background: #00f;padding: 10px;width: 400px;}
.a{width: 100px;height: 50px;float: left;background: #f00;margin: 10px;}
.b{width: 150px;height: 100px;float: left;background: #0f0;margin: 10px;}
.clear{clear: both;}
```
此方法的弊端在于为页面增加了无意义的结构元素。

### 2.使用overflow属性。

通过为父级元素定义overflow属性来清除浮动。

其css样式为
```
.f{background: #00f;padding: 10px;width: 400px;overflow: hidden;}
.a{width: 100px;height: 50px;float: left;background: #f00;margin: 10px;}
.b{width: 150px;height: 100px;float: left;background: #0f0;margin: 10px;}
```
此方法有效地解决了通过空标签元素清除浮动而使文档中出现多余空元素的弊端。

### 3.使用伪元素清楚浮动。

使用:after伪元素来在元素内部插入两个元素块，从面达到清除浮动的效果。其实现原理类似于clear:both方法，只是区别在于:clear在文档中插入一个div.clear标签，而此方法为使用其伪类在元素内部增加一个类似于div.clear的效果。

其css样式为
```
.f{background: #00f;padding: 10px;width: 400px;}
.f:after{display: block;content: "";clear: both;}
```
以上为css清除浮动的三种较常用的方法。