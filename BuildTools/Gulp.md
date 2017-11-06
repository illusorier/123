### gulp.src(globs[,options])

Emits files matching provided glob or an array of globs.

Returns a stream of Vinyl files that can be piped to plugins.

什么是globs？

In computer programming, in particular in a Unix-like environment, **glob** patterns specify sets of filenames with wildcard characters.

gulp当中的路径问题，我们将目标路径以字符串的形式传入如`gulp.src()`中，那么应当如何书写这个字符串？

`gulp.dest()`中填写的是相对路径。

gulp.src()和node的fs模块对比。

目前的感觉是基于globs的文件匹配十分强大。

#### options

##### options.read

### gulp.dest(path[,options])

Can be piped to and it will write files.

The write path is calculated by appending the file 

### gulp.task()

Define a task.

##### fn

Type: `Function`

The function performs the task's main operation.

### gulp-inject

A stylesheet, javascript and webcomponent reference injection plugin for gulp.

在前端自动化工作流中，将打包、压缩好的js和css注入html文件是非常重要的一个步骤。

在webpack中我们通过插件`html-webpack-plugin`来实现这一需求。

而在gulp中，我们用插件`gulp-inject`来完成。

除此之外，`gulp-inject`拥有更为丰富的功能。

`gulp-inject` takes a stream of source files, transforms each file to a string and injects each transformed string into placeholders in the target stream files.

### gulp-uglify

Minify JavaScript with UglifyJS3. 

