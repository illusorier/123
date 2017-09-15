ng1项目的目录结构：所有项目代码放在根目录的app文件夹下, 一些配置文件如package.json, bower.json等直接放在根目下。

angular-phonecat这个项目中并没有使用任何构建工具。

而用generator-gulp-angular生成的目录结构更适合实际项目，它使用了gulp作为构建工具。

我们为什么需要前端路由？

在ng1中我们有angular-ui-router, 在vue中有vue-router.

在angular和vue这样的框架中都涉及到一个bootstrap的问题，因为用这些框架写的html中都有一些具有特殊含义的语法，需要在浏览器渲染之前进行“编译”。

比如ng1中有很多特殊含义的directive，浏览器并不认识它们。

我们会有一个需求：根据某数组的内容去生成一个ul，数组的每一项分别填充如相应的li中。

##### ngApp

Use this directive to **auto-bootstrap** an AngularJS application.

The `ngApp` directive designates the **root element** of the application 

`ngApp`应当写在哪个html中：作为app入口的index.html中。

ngApp应当写在哪个标签上：`ngApp` is typically placed near the root element of the page: `<body>` or `<html>` tags.

##### Conceptual Overview 

- Template: HTML with additional markup

- Model: the data shown to the user in the view and with which the user interacts

- Scope

##### Module

You can think of a module as a container for the different parts of your app - controllers, services, filters, directives, etc.

        // declare a module
        var myAppModule = angular.module( 'myApp', []);
        
那么在实际项目中，应该设置多少模块，这些模块之间的关系又是如何的？

##### Scope

Scopes provides APIs ($watch) to observe model mutations.

Scope 

##### HTML Compile

AngularJS's HTML compiler allows the developer to teach the browser new HTML syntax.

The compiler allows you to attach behavior to any HTML element or attribute and even create new HTML elements or attributes with custom behavior.

AngularJS calls these behavior extensions `directives`.

Compiler is an AngularJS service which traverses the DOM looking for attributes.

The compilation process happens in two phases: 



A directive is just a function which executes 

在ng1中应当如何实现数据绑定？

In AngularJS applications, you move the job of filling page templates with data from the server to the client.

`$digest()`

Processes all of the watchers of the current scope and its children.