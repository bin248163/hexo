---
title: JQuery常用代码段整理
date: 2017-02-15 10:56:46
tags: jquery
---

### 禁用页面右键菜单
```
$(document).ready(function(){
    $(document).bind("contextmenu",function(e){
        return false;
    });
});
```
<!--more-->
### 在新窗口打开页面
```
 $(document).ready(function(){
    $('a[href^="http://www.baidu.com"]').attr("target","_blank");
});
//use
<a href="http://www.baidu.com"></a>
```
### 判断浏览器类型
```
 $(document).ready(function() {
    //firefox 2 and above
    if($.browser.mozilla && $.browser.version > = "1.8") {
        //do something
    }
    //safrri
    if($.browser.safari) {
        //do something
    }
    //chrome
    if($.browser.chrome) {
        //do something
    }
    //opera
    if($.browser.opera) {
        //do something
    }
    //ie6 and below
    if($.browser.msie && $.browser.version < 6) {
        //do something
    }
    //anything above ie6
    if($.browser.msie && $.browser.version > 6) {
        //do something
    }
    //chrome
    if($.browser.) {
        //do something
    }
});
```
jQuery 从 1.9 版开始，移除了 $.browser 和 $.browser.version ， 取而代之的是 $.support 。
```
<script src=”http://libs.baidu.com/jquery/1.8.3/jquery.min.js”></script>
```
### 输入框文字获取和失去焦点
```
$(document).ready(function() {
$("input.text1").val("Enter your search text here");
   textFill($('input.text1'));
});
    function textFill(input){ //input focus text function
     var originalvalue = input.val();
     input.focus( function(){
          if( $.trim(input.val()) == originalvalue ){ input.val(''); }
     });
     input.blur( function(){
          if( $.trim(input.val()) == '' ){ input.val(originalvalue); }
     });
}
```
### 返回顶部滑动动画
```
 $top.click(function() {
        var speed = 300; //滑动的速度
        $('body,html').animate({
            scrollTop: 0
        }, speed);
        return false;
    });
```
### 获取鼠标位置
```
 $(document).ready(function() {
    $(document).mousemove(function(e){
        $('#XY').html("X:" + e.pageX + "|Y:" + e.pageY)
    });
});
```
### 判断元素是否存在
```
 $(document).ready(function() {
    if(("#id").length){
        //do something
    }
});
```
### 点击div跳转
```
 $("div").click(function(){
    window.location=$(this).find("a").attr("href");
    return false;
});
//use
<div><a href="http://www.baidu.com"></a></div>
```
### 判断浏览器宽度添加不同样式
```
 $(document).ready(function() {
    function checkWindowSize(){
        if ($(window).width() > 1200) {
            $('body').addClass('large');
        } else{
            $('body').removeClass('large');
        }
    }
    $(window).resize(checkWindowSize);
});
```
### 回车提交表单
```
 $(document).ready(function() {
    $("input").keyup(function(e){
        if(e.watch=="13"){
            alert("提交！")
        }
    });
});
```
### textarea高度自适应
```
 <textarea name="" rows="" cols="" class="text5" onpropertychange="this.style.height=this.scrollHeight+'px';" oninput="this.style.height=this.scrollHeight+'px';"></textarea>
```
### 将一个元素的背景链接赋值到另一个元素上
```
 var img1 = $(".banner").css("backgroundImage").replace(' url(', '').replace(' )', '');
 var img2 = 'background-image:' + img1;
 $('.head').attr('style', img1).addClass('position');
```