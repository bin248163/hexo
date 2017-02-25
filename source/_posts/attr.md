---
title: JQuery在IE下 attr 对src取值的问题
date: 2017-02-15 11:19:14
tags: javascript
---

JQuery的写法
```
 $('.videoA').click(function() {
        var spUrl = $(this).attr("href");
        $('.video object').attr("date",spUrl);
        $('.video-w').show();
        return false;        
    });
```
<!--more-->
需兼容IE则可以不用attr，而使用.html替换整个div内部的内容
```
 $('.videoA').click(function() {
        var spUrl = $(this).attr("href");
        var object_str='<object data="'+spUrl+'" style="width: 100%;height: 100%;display: block;" />';
        $('.video').html(object_str);
        $('.video-w').show();
        return false;
    });
```