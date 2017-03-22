---
title: robots.txt文件用法整理
date: 2017-03-20 17:50:49
tags: robots
---

robots.txt是搜索引擎中访问网站的时候要查看的第一个文件，文件告诉蜘蛛程序在服务器上什么文件是可以被查看。

robots.txt文件应该放置在网站根目录下。举例来说，当一个搜索蜘蛛访问一个站点时，它会首先检查该站点根目录下是否存在robots.txt，如果存在，搜索机器人就会按照该文件中的内容来确定访问的范围；如果该文件不存在，所有的搜索蜘蛛将能够访问网站上所有没有被口令保护的页面。仅当网站包含不希望被搜索引擎收录的内容时，才需要使用robots.txt文件。如果希望搜索引擎收录网站上所有内容，请勿建立robots.txt文件。

#### 禁止所有搜索引擎访问网站的任何部分  
```css
User-agent: *
  Disallow: /
```
<!--more-->
#### 允许所有的robot访问

```
User-agent: *
  Disallow:
```
或者
```
User-agent: * 
  Allow: / 
```
#### 仅禁止Baiduspider访问您的网站
```
User-agent: Baiduspider
  Disallow: /
```
#### 禁止spider访问特定目录
假设站点上有两个目录需要对搜索引擎的访问做限制，对每一个目录必须分开声明，而不能写成 "Disallow: /img1/ /img2/"。
```
User-agent: * 
  Disallow: /img1/
  Disallow: /img2/
```
#### 允许访问指定目录
```
User-agent: * 
  Allow: /img1/
```
#### 使用"*"限制访问内容
禁止访问/img1/目录下的所有以".htm"为后缀的内容
```
User-agent: * 
  Disallow: /img1/*.htm
```
#### 使用"$"允许访问内容
仅允许访问以".htm"为后缀的内容
```
User-agent: * 
  Allow: .htm$
  Disallow: / 
```
#### 禁止访问网站中所有的动态页面
```
User-agent: * 
  Disallow: /*?*
```
#### 禁止抓取网站上所有图片
```
User-agent: *
  Disallow: .jpg$
  Disallow: .jpeg$ 
  Disallow: .gif$ 
  Disallow: .png$ 
  Disallow: .bmp$
```
#### 仅允许Baiduspider抓取网页和.gif格式图片
允许抓取网页和gif格式图片，不允许抓取其他格式图片
```
User-agent: Baiduspider 
  Allow: .gif$ 
  Disallow: .jpg$ 
  Disallow: .jpeg$  
  Disallow: .png$ 
  Disallow: .bmp$
```