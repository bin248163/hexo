---
title: javascript判断移动端实现自动跳转的方法
date: 2017-02-15 10:36:32
tags: javascript
---

在网站建设的时候，因为一些原因我们可能在pc端和移动端做出两个不同的网站版本，但又不想在用户从移动端的搜索结果进入到pc端的页面，因此在用户使用手机等移动端工具打开pc页面时跳转到移动端的页面。
实现方法为在页面的头部加入以下代码：
```
<script>
            /*
             * pc 跳转到 phone
             */
            try {
                var urlhash = window.location.hash;
                if (!urlhash.match("fromapp")) {
                    if ((navigator.userAgent.match(/(iPhone|iPod|Android|ios|iPad)/i))) {
                        window.location = "/mobile";
                    }
                }
            } catch (err) {}
</script>
```
<!--more-->
```
window.location = "/mobile";
```
这句为移动端首页所在的路径。