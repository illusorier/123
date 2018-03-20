# Decorators

装饰器其实就是函数？

A *Decorator* is a special kind of declaration that can be attached to a class declaration, method, 

Decorators use the form `@expression`, where `expression` must evaluate to a function that will be called at runtime with information about the decorated declaration.

A *Class Decorator* is declared just before a class declaration.

The class decorator is applied to the constructor of the class

The expression for the class decorator will be called as a function at runtime, with constructor of the decorated class as its only argument.



