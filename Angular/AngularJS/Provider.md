## Providers

AngularJS中的Provider是一个非常有趣的概念，它的主要存在意义就是实践了若干种设计模式，提高了代码的复用性和健壮性。

Each web application you build is composed of objects that collaborate to get stuff done.

In AngularJS apps most of these objects are instantiated and wired together automatically by the **injector service**.

要注意的是，下面这个service和`angular.module().service`并不等价。

The injector creates two types of objects, **services** and **specialized objects**.

Services are objects whose API is defined by the developer writing the service.

Specialized objects conform to a specific AngularJS framework API. These objects are 

The injector needs to know how to create these objects.

从设计模式的角度去理解以下几种recipe。

#### Value Recipe

        angular
            .module('myApp', []);
            .value('clientId', 'a12345654321x');

#### Factory Recipe

Factory和Value有什么区别？

The Value recipe is very simple to write, but lacks some important features we often need when creating services.

The Factory recipe adds the following abilities:

- ability to use other service (have dependencies)

- 

angular中的所有service(广义的)都是单例的。

All services in AngularJS are singletons.

That means 

#### Service Recipe

The Service recipe produces a service just like the Value or Factory recipes.

Service和Factory的区别在于，service返回的是一个构造函数，factory返回的是一个对象。

#### Provider Recipe

The Provider recipe is the core 