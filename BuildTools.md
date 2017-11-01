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

## Yemoman

Yeoman helps you to **kickstart** new projects, prescribing **best practices** and tools to help you stay **productive**.

