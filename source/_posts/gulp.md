---
title: gulp配置
date: 2017-03-22 10:18:08
tags: gulp
---

### 搭建gulp环境前需要安装node与git
node: [http://nodejs.cn/download/](http://nodejs.cn/download/)
git: [https://git-for-windows.github.io/](https://git-for-windows.github.io/)

### 打开git bash全局安装全局安装 gulp
这里我们将 npm的注册表源设置为淘宝镜像来提升安装速度<!--more-->
```
npm install -g cnpm --registry=https://registry.npm.taobao.org
```
作为项目的开发依赖（devDependencies）安装
```
cnpm install -g gulp 
```
### 定位到放置项目的位置，将gulp安装到项目本地
```
cnpm install —-save-dev gulp
```
### 在项目根目录新建gulpfile.js文件，运行gulp
假设我们的项目需要如下任务：

+ 检查Javascript
+ 编译Sass（或Less之类的）文件
+ 合并Javascript
+ 压缩并重命名合并后的Javascript

安装依赖
```
cnpm install gulp-jshint gulp-sass gulp-concat gulp-uglify gulp-rename --save-dev 
```
将如下代码粘贴到gulpfile.js
```
// 引入 gulp
var gulp = require('gulp'); 

// 引入组件
var jshint = require('gulp-jshint');
var sass = require('gulp-sass');
var concat = require('gulp-concat');
var uglify = require('gulp-uglify');
var rename = require('gulp-rename');

// 检查脚本
gulp.task('lint', function() {
    gulp.src('./js/*.js')
        .pipe(jshint())
        .pipe(jshint.reporter('default'));
});

// 编译Sass
gulp.task('sass', function() {
    gulp.src('./scss/*.scss')
        .pipe(sass())
        .pipe(gulp.dest('./css'));
});

// 合并，压缩文件
gulp.task('scripts', function() {
    gulp.src('./js/*.js')
        .pipe(concat('all.js'))
        .pipe(gulp.dest('./dist'))
        .pipe(rename('all.min.js'))
        .pipe(uglify())
        .pipe(gulp.dest('./dist'));
});

// 默认任务
gulp.task('default', function(){
    gulp.run('lint', 'sass', 'scripts');

    // 监听文件变化
    gulp.watch('./js/*.js', function(){
        gulp.run('lint', 'sass', 'scripts');
    });
});
```
分段解释下这段代码。

引入组件

var gulp = require('gulp'); 
var jshint = require('gulp-jshint');
var sass = require('gulp-sass');
var concat = require('gulp-concat');
var uglify = require('gulp-uglify');
var rename = require('gulp-rename');
这一步，我们引入了核心的gulp和其他依赖组件，接下来，分开创建lint, sass, scripts 和 default这四个不同的任务。

Lint任务

gulp.task('lint', function() {
    gulp.src('./js/*.js')
        .pipe(jshint())
        .pipe(jshint.reporter('default'));
});
Link任务会检查 js/ 目录下得js文件有没有报错或警告。

Sass任务

gulp.task('sass', function() {
    gulp.src('./scss/*.scss')
        .pipe(sass())
        .pipe(gulp.dest('./css'));
});
Sass任务会编译 scss/ 目录下的scss文件，并把编译完成的css文件保存到 /css 目录中。

Scripts 任务

gulp.task('scripts', function() {
    gulp.src('./js/*.js')
        .pipe(concat('all.js'))
        .pipe(gulp.dest('./dist'))
        .pipe(rename('all.min.js'))
        .pipe(uglify())
        .pipe(gulp.dest('./dist'));
});
scripts任务会合并 js/ 目录下得所有得js文件并输出到 dist/ 目录，然后gulp会重命名、压缩合并的文件，也输出到 dist/ 目录。

default任务

gulp.task('default', function(){
    gulp.run('lint', 'sass', 'scripts');
    gulp.watch('./js/*.js', function(){
        gulp.run('lint', 'sass', 'scripts');
    });
});
这时，我们创建了一个基于其他任务的default任务。使用 .run() 方法关联和运行我们上面定义的任务，使用 .watch() 方法去监听指定目录的文件变化，当有文件变化时，会运行回调定义的其他任务。

现在，回到命令行，可以直接运行gulp任务了。

gulp
这将执行定义的default任务，换言之，这和以下的命令式同一个意思

gulp default
当然，我们可以运行在gulpfile.js中定义的任意任务，比如，现在运行sass任务：

gulp sass