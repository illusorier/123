Angular1当中的directive主要由两种用法：一种作为HTML element的attribute，另一种是作为自定义的element(即component)。

首先我们先来看一些angular自带的directive，它们实现了哪些功能，又是如何实现的。

angular1的官方文档中详细介绍了directive的common use cases.

1. Manipulates the DOM
2. Wraps Other Elements
3. Adds Event Listeners

其中第一种用法的示例非常非常有意思，它向我们演示了如何不使用scope属性来实现数据的单向绑定。

https://docs.angularjs.org/guide/directive#creating-a-directive-that-manipulates-the-dom

## Components

#### differences from directive

The `return {};` statement inside the `.directive()` becomes the Object definition inside `.component()`.

directive定义时的第二个参数是函数，该函数返回一个对象，而component的第二个参数就是一个对象。

`scope` and `bindToController`,  to `bindings`.

#### 
