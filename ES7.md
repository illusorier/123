## Decorators

The similarities between JavaScript and Python continue to increase over time.

You can apply by prefixing the decorator with an `@` 

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
        
#### Decorating a class

In this case, a decorator takes the target constructor.