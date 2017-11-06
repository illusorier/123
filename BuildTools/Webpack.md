Webpack是什么？我们为什么需要webpack？

Today's websites are evolving into web apps.

As a result there is a lot of code on the client side.

A big code base needs to be organized.

Module systems offer the option to split your code base into modules.

如今的web apps往往依赖许多外部文件


There are multiple standards for how to define dependencies and export values.

- `<script>` - tag style (without a module system)
- CommonJS
- 

Modules should be executed on the client, so they must be transferred from the server to the browser.

在传输modules时

There are two extremes when transferring modules:

- One request per module
- All modules in one request

Why Only JavaScript?



While compiling all modules: Split the set of modules into multiple smaller batches (chunks).

When compiling all these modules, a static analysis tries to find its dependencies.



#### Four Core Concepts

- entry
- output
- loaders
- plugins



Webpack is fed via a configuration object.

There are two ways to pass the `configuration object`.

#### CLI

If you use the CLI it will read a file `webpack.config.js` (or the file passed by the `--config` option)

#### node.js API

    webpack({
      // configuration
    }, callback);
    
### Dependency Graph

Any time one file depends on another, webpack treats this as *dependency*.

### Entry

webpack creates a graph of all of your application's dependencies.

The starting point of this graph is known as an *entry point*.

In webpack we define entry points using the `entry` property in our webpack configuration object.

有多种方法配置`entry`。

There are multiple ways to declare your `entry` property that are specific to your application's needs.

### Code Splitting

For big web apps it's not efficient to put all code into a single file, especially if some blocks of code are only required under some circumstances.

Webpack has a feature to split your codebase into "chunks" which are loaded on demand.

#### ES6 Modules

Webpack `1.x.x` does not natively support or understand ES6 modules.

However, you can get around that by using a transpiler, like Babel, to turn the ES6 `import` syntax into CommonJS or AMD modules.

### Loaders

The goal is to have all of the assets in your project to be webpack's concern and not the browser's.

This doesn't mean that they all have to be bundled together.

webpack treats 

Loaders are transformations that are applied on a resource file of your app.They are functions(running in node.js)

#### Installing loaders

If the loader is available on npm you can install the loader via:

    

### Plugins

The `plugins` option is used to customize the webpack build process in a variety of ways

### Resolving

Resolve is used to find "import" and "require" references that are not immediately available in the current path.

For example

The dependency module can be from the application code or a third party library. 

    import "/home/me/file"; // 此路径为磁盘根目录
    
    import "C:

以下是webpack配置的文档。

### Configuration Object Content

`context`

The base directory (absolute path) for resolving `entry` option.

Default:`process.cwd()`

`entry`

In webpack we define *entry points* using the `entry` property in our webpack configuration object.

`output`

`output.filename`

Specifies the name of each output file on disk.

single entry

    {
      entry: './src/app.js`,
      output: {
        filename: 'app.js',
        path: path.resolve(__dirname, '../dist")
      }
    }
    
multiple entries

If your configuration creates more than a single "chunk" (as with multiple entry points)

    {
      
        
        
`output.path`

`module`

`module.loaders`

An array of automatically applied loaders.

Each item can have these properties:





### Code Splitting - Libraries

A typical application uses third party libraries for framework/functionality needs.Particular versions of these libraries are used and code does not change often.However,the `application code` changes frequently.

Building `application code` with `third party code` would be inefficient.This is because the browser can cache asset files

We can do this only when we separate the bundles for
 
### webpack-dev-server

The webpack-dev-server is a little Node.js Express server, which uses 

### webpack-dev-middleware

### webpack-hot-middleware
 
 