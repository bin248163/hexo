---
title: 使用CSS修改HTML5 input placeholder颜色的实现
date: 2017-02-15 11:03:14
tags: css
---

```
::-webkit-input-placeholder { /* WebKit browsers */
    color:    #fff;
}
:-moz-placeholder { /* Mozilla Firefox 4 to 18 */
   color:    #fff;
   opacity:  1;
}
::-moz-placeholder { /* Mozilla Firefox 19+ */
   color:    #fff;
   opacity:  1;
}
:-ms-input-placeholder { /* Internet Explorer 10+ */
   color:    #fff;
}
```
<!--more-->
(可在冒号前面添加类选择器)

单冒号(:)用于CSS3伪类，双冒号(::)用于CSS3伪元素。

css伪类：CSS 伪类用于向某些选择器添加特殊的效果。

css伪元素：CSS 伪元素用于向某些选择器设置特殊效果。

伪元素由双冒号和伪元素名称组成。双冒号是在当前规范中引入的，用于区分伪类和伪元素。但是伪类兼容现存样式，浏览器需要同时支持旧的伪类， 如:first-line,:first-letter,:before,:after等等。因此对于css2之前已经有的伪元素两种写法的作用是一样的，但是为了兼容IE浏览器还是使用单冒号的写法。

opacity: 1;是为了修改FF的默认透明度导致颜色偏差。