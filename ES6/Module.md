
    // ES6
    import { funA, funB, funC } from 'someModule';

ES6模块不是对象，而是通过`export`命令显式

#### 传统方法
在HTML网页中，浏览器通过`<script>`标签加载JavaScript脚本。

#### 加载规则
浏览器加载ES6模块，也使用`<script>`标签，但是要加入`type="module"`属性。

The HTML `<script>` element is used to embed or reference an executable script.

#### src
This attribute specifies the URI of an external script.

#### type
If this attribute is absent, the script is treated as JavaScript.

If the type specified is `module` the code is treated as a JavaScript module.



#### Basic Exporting

You can use the `export` keyword to expose parts of published code to other modules.In the simplest case,you can place `export` in front any variable,function,or class declaration to export it from the module.

You need not always export a declaration;you can also export references

#### Basic Importing

Once you have a module with exports,you can access the functionality in another module by using `import` keyword.

    import { funA, funB, funC } from 'someModule';

The two parts of an `import` statement are the identifiers you're importing and

The curly braces after `import` indicate the bindings to import from a given module.The keyword `from` indicates 


## NodeJS中的Modules

Node.js has a simple module loading system.In Node.js,files and modules are in one-to-one correspondence (each file is treated as a)

    const PI = Math.PI;
    exports.area = (r) => PI * r * r;
    
To add functions and objects to the root of your module,you can add them to the special `exports` object.

    exports.area = (r) => PI * r ** 2;

If you want the root of your module's export to be a function (such as constructor) or if you want to export a complete object in one assignment instead of building it one property at a time,assign it to  `module.exports` instead of `exports`.

    const square = require('./square.js`);
  
#### Caching

#### Cycles

When there are circular 

#### File Modules

If the exact filename is not found,then Node.js will attempt to load the required filename with the added extension: `.js`, `.json`, and finally `.node`.

A required module prefixed with `'/'` is an absolute path to the file.

A required module prefixed with `'./'` is relative to the file calling `require()`. 

Without a leading  `'/'`, `'./'`, or `'../'` to indicate a file,the module must either be a core module or is loaded from a `node.modules` folder.

#### Folders as Modules

There are three ways in which a folder may be passed to `require()` as an argument.

#### The module wrapper
Before a module's code is executed,Node.js will wrap it with a function wrapper that looks like the following.

    (function (exports, require, module, __filename, __dirname) {
    // Your module code actually lives in here.
    });

#### The `module` Object
In each module, the `module` variable is a reference to the object representing the current module.

For convenience,`module.exports` is also accessible via the `exports`

    var exports = module.exports
    
    exports = function(x) {
      console.log(x);
    }
    
因此，当模块要输出的是一个非Object对象时，只能使用`module.exports`.


#### require

`require`关键字的基本功能是，读入并执行一个JS文件内包含的代码，然后返回该模块的exports对象。


