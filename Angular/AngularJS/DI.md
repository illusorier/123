## Dependency Injection

在软件开发中，依赖是一个被广泛运用的概念。

Dependency Injection (DI) is a software design pattern deals with how components get hold of their dependencies.

> 在ng1的文档中，components这个概念有两个含义，一个是UI组件，一个是组成angular的组件。

The AngularJS **injector subsystem** is in charge of 

DI is pervasive 

- Components such as services, directives, filters, and animations are defined by an injectable factory method or constructor function.

- Controllers are defined by a constructor function, which can be injected 

#### Dependency Annotation

##### Implicit Annotation

> If you plan to minify your code, your service names will get renamed and break your code.

The simplest way to get hold of the dependencies is to assume that the function parameter are the names of dependencies.

#### Why Dependency Injection?

There are only three ways a component (object or function) can get a hold of its dependencies: