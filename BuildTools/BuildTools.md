## Browserify

我们为什么需要browserify?

        Uncaught ReferenceError: require is not defined
        
为什么会出现上述的报错？

因为在浏览器中我们只能通过`script`元素来引入JS库，浏览器并不认识node中的`require`，目前也并没有广泛支持ES6的模块系统，因此我们需要为浏览器transform我们的代码，比较常用的工具是browserify和webpack。

Use a node-style `require()` to organize your code and load modules installed by npm.

##### b.transform

Transform source code before parsing it for `require()` calls.

## babelify

Babel browserify transform.

         .pipe($.babel())
         .pipe($.browserify())
         
如上的gulp工作流在某种类型的项目结构中会出现以下报错：

        ParseError: 'import' and 'export' may appear only with 'sourceType: module
        
这是因为我们仅仅用babel编译了一个js文件，其他作为依赖的js文件并没有进行编译，因此会报错。

## Browsersync

There's no official 

## Yemoman

Yeoman helps you to **kickstart** new projects, prescribing **best practices** and tools to help you stay **productive**.

