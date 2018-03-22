Angular1(AngularJS)当中的directive主要由两种用法：一种作为HTML element的attribute，另一种是作为自定义的element(即component)。

首先我们先来看一些angular自带的directive，它们实现了哪些功能，又是如何实现的。

angular1的官方文档中详细介绍了directive的common use cases.

1. Manipulates the DOM
2. Wraps Other Elements
3. Adds Event Listeners

其中第一种用法的示例非常非常有意思，它向我们演示了如何不使用scope属性来实现数据的单向绑定。

https://docs.angularjs.org/guide/directive#creating-a-directive-that-manipulates-the-dom

一般来说，我们通过scope或者bindings属性来实现将父组件数据传入子组件的功能。

## Components

#### differences from directive

The `return {};` statement inside the `.directive()` becomes the Object definition inside `.component()`.

directive定义时的第二个参数是函数，该函数返回一个对象，而component的第二个参数就是一个对象。

`scope` and `bindToController`,  to `bindings`.

#### Inputs and Outputs

AngularJS中不同层级的directive之间可以实现单向或者双向数据绑定。

For components however, only the component that owns the data should modify it, to make it easy to reason about.

因此 `=` 不会在bindings中出现。

- Inputs should be using `<` and `@` bindings.
- Outputs are realized with `&` bindings, which function as callbacks to component events.
- Instead of manipulating Input Data, the component calls the correct Output Event with the changed data.

#### Using Angular 1.5's Multiple Transclusion Slots

在组件的开发中，常常会有这样一个需求：我们希望自定义模板中的某些部分。

Most (well maintained) Angular projects eventually reach the point where they would benefit from having a few generic components that use transclusion.

Prior to Angular 1.5 a component could only transclude a single entry: whatever you gave it was had to be used as a whole.

那么如果实现这样的一一对应关系呢？

相比之下，Vue的实现方式简洁很多，AngularJS中还需要在JS中进行声明。

Components can be registered using the `.component()` method