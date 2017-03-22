---
title: HTML5新增表单验证整理
date: 2017-02-15 11:03:01
tags: html
---

### HTML5新增语义input类型：

email 定义用于 e-mail 地址的文本字段

tel 定义用于电话号码的文本字段。

url 定义用于 URL 的文本字段。

number 定义带有 spinner 控件的数字字段
<!--more-->
time 定义日期字段的时、分、秒（带有 time 控件）

date 定义日期字段（带有 calendar 控件）

datetime 定义日期字段（带有 calendar 和 time 控件）

datetime-local 定义日期字段（带有 calendar 和 time 控件）

month 定义日期字段的月（带有 calendar 控件）

week 定义日期字段的周（带有 calendar 控件）

range 定义带有 slider 控件的数字字段。

search 定义用于搜索的文本字段。

color 定义拾色器。

### 强制用户必须提交有效数据
```html
 <input type="email" name="email" id="youremail" required>
```
使用min, max和step进行数字验证

当发现用户输入的数字大于max或小于min的值的时候，会返回一个错误提示。
```html
 <input type="number" name="age" id="yourage" min="18" max="120">
```
step这个属性规定了用户只能按照等差数列的方式输入数字。例如给输入框添加step=“2”这个属性值，那么用户只能输入差值为2的倍数的数字。
```html
 <input type="number" name="" id="" min="2" max="1024" step="4">
```
文本长度验证：maxlength

maxlength属性让我们可以定义输入框的最大字符限制，在限定用户的输入文本长度的时候，也可以使用该属性。
```html
 <textarea name="msg" id="" cols="25" rows="4" maxlength="500"></textarea>
```

textarea元素，俗称“文本域”，或者“多行文本框”，其自带原生的HTML属性rows表示行的意思，可以改变textarea的可视区域高度，cols表示列，可以改变textarea的可视区域宽度。（兼容性差，推荐使用CSS控制宽度、高度）

pattern：Regex验证

pattern这个属性允许我们在验证过程中使用 正则表达式，下面的例子需要用户输入最少8个字符的密码，而且字符串中必须含有至少一个字母以及至少一个数字：
```html
 <input type="password" name="" id="" required pattern="^(?=.*[A-Za-z])(?=.*\d)[A-Za-z\d]{8,}$">
```