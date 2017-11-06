第一个问题是我们为什么需要AngularJS，它解决了远古前端开发流程中的哪些问题？

Why AngularJS?

HTML is great for declaring static documents, but it falters when we try to use it for declaring dynamic views in web-applications.

HTML本身是用来声明静态文档，在如今前后端分离，web-app的开发背景下，它显然无法很好的满足现有需求。

AngularJS提出了MVC模式，相关概念在如今的前端开发中被广泛使用。

**基本的AngularJS的结构**：

Component / Directive + `{{}}` => Template

Controller + Template => View

什么是Template?   

Template: HTML with additional markup.

In AngularJS, templates are written with HTML that contains AngularJS-specific elements and attributes.

AngularJS combines the template with information from the model and controller to render the dynamic view that a user sees in the browser.

在Angular中，我们书写的HTML有所不同，它包含了一些专属的元素和属性，甚至语法(如 `{{}}` )

从面向对象的角度去理解AngularJS。

Controller其实就是一个类。

In AngularJS, a Controller is defined by a JavaScript **constructor function** that is used to augment the AngularJS Scope.

When a Controller is attached to the DOM via the ng-controller directive,  AngularJS will instantiate a new Controller object,

实际开发中，我们并不会实际使用 `ng-controller` 。

以上的一些概念实际上足够我们开发一个简单的，可维护性、可读性低的web-app了。