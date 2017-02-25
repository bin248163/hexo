---
title: push本地代码到github出错的解决办法
date: 2017-02-15 11:19:37
tags: git
---

创建的github版本库，在push代码时出现如下错误：
```
 To github.com:***/***.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'git@github.com:***/***.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```
<!--more-->
出现上面错误的原因是因为远程repository和本地的repository冲突导致的，在创建版本库后，在github的版本库页面点击了创建README.md文件的按钮创建了说明文档，但是却没有pull到本地。这样就产生了版本冲突的问题。

解决方法如下：

1.使用强制push的方法：
```
 $ git push -u origin master -f
```
这样做会使远程文件丢失，一般不可取。

2.push前先将远程repository修改pull下来
```
$ git pull origin master
$ git push -u origin master
```
3.若不想merge远程和本地修改，可以先创建新的分支：
```
 $ git branch [name]
```
然后push
```
 $ git push -u origin [name]
```