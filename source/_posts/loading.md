---
title: 实现基于javascript的页面加载loading动画
date: 2017-02-15 11:52:14
tags: javascript
---

页面loading动画能够更好的反应当前网页的加载进度情况，动画的形式从开始0%到100%完成网页加载这一过程可以给用户一个温馨的提示，用户体验很不错。

loading动画的制作非常容易，难点在于如何判断当前页面的加载进度，目前没有方法可以直接获取正在加载对象的大小。所以我们无法通过数据大小来实现0-100%的加载显示过程。

我们知道当页面加载时html代码是逐行进行加载的，因此我们可以通过这个特性来间接达到效果。

首先我们需要定义一个页面的加载动画：<!--more-->
```css
@mixin hover($value:.2s){-webkit-transition: all $value;-o-transition: all $value;-moz-transition: all $value;transition: all $value;}
.loading{width: 0;height: 2px;background: #f00;position: absolute;top: 0;left: 0;@include:hover(1s);}
```
然后根据实际情况将当前页面分成若干份，然后插入相关节点如下：
```html
<div class="div1"></div>
<script>
$('.loading').animate({'width':'20%'});
</script>
<div class="div2"></div>
<script>
$('.loading').animate({'width':'40%'});
</script>
<div class="div3"></div>
<script>
$('.loading').animate({'width':'60%'});
</script>
 ...
```
最后在页面的最底部让loading动画达到100%并隐藏动画即可：
```html
<script>
$('.loading').animate({'width':'100%'}).fadeOut();
</script>
```