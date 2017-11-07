## Components

#### differences from directive

The `return {};` statement inside the `.directive()` becomes the Object definition inside `.component()`.

directive定义时的第二个参数是函数，该函数返回一个对象，而component的第二个参数就是一个对象。

`scope` and `bindToController`,  to `bindings`.

##### Creating a Directive that Manipulates the DOM

Directives that want to modify the DOM typically use the `link` option to register