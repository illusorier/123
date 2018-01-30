要想比较深入进行对比，需要对下面这些概念有所了解。

Single-Page-Applications (SPAs) are Web apps 

MVC, MVP and MVVM are three popular design patterns in software development.

### Model View Controller (MVC)

MVC design pattern divides an application into three major aspects: Model, View, and Controller.

#### Model

Model means data that is required to display in the view.

Model represents a collection of classes that describes the business logic.

#### View

The View represents UI components like XML, HTML etc.

### Model View Presenter (MVP)


### Model View View-model (MVVM)

To start with, MVC design pattern is not specific to AngularJS, you must have seen/implemented this pattern in many other programming language.

In MVC if we make any change in the view it does not gets updated in model.

React did not invent components, but it did take this idea one step further.

Single Responsibility Principle

Think a bit about the kind of data you store in Model on the client side.

The Model is breaking the Single Responsibility Principle.

You do not have a separate way of managing **UI State** and **Application State**.

这两个概念非常重要。

**Application State**: 指View层所依赖的数据。

**UI State**：例如登陆页面中，可分未登陆，登陆中，已登陆三个状态；又如某页面有一个表格，这个表格可存在多个状态，如浏览、编辑、新增等。

## Angular1 vs Vue

启动方法：

Angular1: ng-app / angular.bootstrap()

Vue: id='app' + new Vue({el: 'app'}) / vm.$mount(el)

## Angular2 vs Vue