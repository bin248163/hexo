---
title: 页面滚动触发CSS3动画的简单实现
date: 2017-02-15 11:02:52
tags: css
---

这篇教程将介绍如何在页面滚动时触发CSS3动画，这种效果使用JQuery和CSS就能做到。

实现原理为在页面加载时通过js给元素添加一个样式，当页面滚动到该元素位置时添加另外一个样式从而实现动画效果（此方法不兼容IE10以下浏览器）。

### HTML

首先写好HTML标签，给需要滚动时触发的元素添加ID。
```html
<div class="w-1000 pc-30" id="jsn">
```
<!--more-->
### CSS

在样式表中编写好动画样式：

.t-3为页面加载时添加的样式，.t-3h为页面滚动到该元素位置时添加的样式。（样式使用CSS预处理器SASS书写，需了解SASS请点击这里）
```css
@mixin hover($value:.2s){-webkit-transition: all $value;-o-transition: all $value;-moz-transition: all $value;transition: all $value;}
.t-3{transform: translate(0, 200px);@include hover(.8s);opacity: 0;filter: alpha(opacity=0);}
.t-3h{transform: translate(0, 0);opacity: 1;filter: alpha(opacity=100);}
```
### JQuery

判断元素滚动到页面底部的时候加载.t-3h样式。
```javascript
var jsn=$('#jsn')；
$(window).scroll(function() {
        if ($(window).scrollTop() > 0) {
            jsn.addClass('t-3');
        }
        if ($(window).scrollTop() > $jsn.offset().top - $(window).height()) {
            jsn.addClass('t-3h');
        }else{
            jsn.removeClass('t-3h');
        }  
});
```

ps：通过一些插件可以更简单的实现该类效果，如scrollReveal.js、wow.js等，该类插件将在后面介绍。