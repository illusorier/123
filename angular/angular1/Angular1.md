
Model View Controller or MVC as it is popularly called, is a software design pattern for developing web application.

- Model - It is the lowest level of the pattern responsible for maintaining data.

- View - It is responsible for displaying all or a portion of the data to the user.

- Controller - It is a software Code that controls

我的理解是：在过去前后端不分离的开发背景下，动态的HTML是由后台生成的，数据的处理和填充也是后台完成的，前端JS只负责与DOM相关的操作。但在如今前后端分离的时代， 后台仅仅负责提供API，前端调用API获取数据、处理数据、填充数据，因此我们就需要一些传统的软件开发思想，如MVC，指导前端的开发过程。

ng1项目的目录结构：所有项目代码放在根目录的app文件夹下, 一些配置文件如package.json, bower.json等直接放在根目下。

angular-phonecat这个项目中并没有使用任何构建工具。

而用generator-gulp-angular生成的目录结构更适合实际项目，它使用了gulp作为构建工具。

在远古angular开发中，我们甚至会看到这样的代码，哈哈哈。

        <script src="bower_components/angular-perfect-scrollbar/src/angular-perfect-scrollbar.js"></script>

我们为什么需要前端路由？

在ng1中我们有angular-ui-router, 在vue中有vue-router.

AngularJS lets you extend HTML vocabulary for your application.

在angular和vue这样的框架中都涉及到一个bootstrap的问题，因为用这些框架写的html中都有一些具有特殊含义的语法，需要在浏览器渲染之前进行“编译”。

比如ng1中有很多特殊含义的directive，浏览器并不认识它们。

我们会有一个需求：根据某数组的内容去生成一个ul，数组的每一项分别填充如相应的li中。

在ng1中，directives和components的区别是什么？

据我了解，在ng1中，components这个概念是在后期版本 (1.5.x) 中引入的，因此这两个概念的功能本身就有重叠的部分。

##### ngApp

Use this directive to **auto-bootstrap** an AngularJS application.

The `ngApp` directive designates the **root element** of the application 

`ngApp`应当写在哪个html中：作为app入口的index.html中。

ngApp应当写在哪个标签上：`ngApp` is typically placed near the root element of the page: `<body>` or `<html>` tags.

## Conceptual Overview 

- Template: HTML with additional markup

- Model: the data shown to the user in the view and with which the user interacts

- Scope

- Controller: the business logic behind views

## Module

You can think of a module as a container for the different parts of your app - controllers, services, filters, directives, etc.

        // declare a module
        var myAppModule = angular.module( 'myApp', []);
        
那么在实际项目中，应该设置多少模块，这些模块之间的关系又是如何的？

## Services

A Service is just a function for the business layer of the application, it's just a simple function.

It acts as a `constructor` function and is invoked once at runtime with `new`, much like you would with plain JavaScript (Angular is just calling a `new` instance under the hood for us).

>  `.service()` 并不是 `.factory()` 的一种简化写法。

A factory is not just "another way" for doing services.

It can however, give you the same capabilities of a `.service()`, but is much more powerful and flexible.

#### Creating Services

## Scopes

我们为什么需要scopes这个概念？

当有了数据，我们就需要对其进行管理，就会有作用域、命名空间等等概念。

Scopes provides APIs ($watch) to observe model mutations.

Scope

##### Integration with the browser event loop

1. The browser's event-loop waits for an event to arrive.

## Interpolation

Interpolation markup with embedded expressions is used by AngularJS to provide data-binding to text nodes and attribute values.

        <a ng-href="img/{{username}}.jpg">Hello {{username}}!</a>

## Decorators

## HTML Compile

AngularJS's HTML compiler allows the developer to teach the browser new HTML syntax.

The compiler allows you to attach behavior to any HTML element or attribute and even create new HTML elements or attributes with custom behavior.

AngularJS calls these behavior extensions `directives`.

Compiler is an AngularJS service which traverses the DOM looking for attributes.

The compilation process happens in two phases: 

1. **Compile**:

1. `$compile` traverses the DOM and matches directives. 

    If 

2.  Once all directives matching a DOM element have been 

3. `$compile` links the template 

A directive is just a function which executes 

在ng1中应当如何实现数据绑定？

In AngularJS applications, you move the job of filling page templates with data from the server to the client.

`$digest()`

Processes all of the watchers of the current scope and its children.

## Bootstrap

AngularJS initialization process and manually initialize AngularJS.

AngularJS initializes automatically的时间点。

##### $event

Directives like `ngClick` and `ngFocus` expose a `$event` object within the scope of that expression.

The object is an instance of a JQuery Event Object.

        <button ng-click="clickMe($event)">Event</button>