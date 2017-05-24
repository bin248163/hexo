---
title: BEM——高效的CSS命名方案
date: 2017-05-02 09:39:59
tags: css
---

官网：[http://bem.info/](http://bem.info/)
BEM，即块（block）、元素（element）、修饰符（modifier）,是由Yandex团队提出的一种前端命名方法论。

使用方法示例：
```css
.div{} /* 块 */
.div__element{} /* 元素 */
.div--modifier{} /* 修饰符 */
```
<!--more-->
.div 代表了更高级别的抽象或组件。
.div__element 代表.div的后代，用于形成一个完整的.div的整体。
.div--modifier代表.div的不同状态或不同版本。

BEM是一个高效、简单的命名约定，让我们的css代码更容易阅读和理解，维护起来也更加的容易。