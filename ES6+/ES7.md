## Decorators

The similarities between JavaScript and Python continue to increase over time.

You can apply by prefixing the decorator with an `@`.

An ES2016 decorator is an expression which returns function and can take a target, name and property descriptor as arguments.

#### Decorating a property

Let's take a look at a basic Cat class:

        class Cat {
            meow() {}
        }
        
Evaluating this class results in installing the meow function onto `Cat.prototype`, roughly like this:

        Object.defineProperty(Cat.prototype, 'meow', {
            value: '',
            enumerable: false,
            configurable: true,
            writable: true
        });
        
Imagine we want to mark a property or method name as not being writable.

We could thus define a `@readonly` decorator:

        function readonly(target, key, descriptor) {}
        
#### Decorating a class

In this case, a decorator takes the target constructor.

本文主要内容参考(复制)：https://medium.com/google-developers/exploring-es7-decorators-76ecb65fb841