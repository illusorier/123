## OOP

JavaScript is a bit confusing for developers experienced in class-based languages (like Java or C++), as it is dynamic and does not provide a `class` implementation per se (the `class` keyword is introduced in ES2015, but is syntactical sugar, JavaScript remains prototype-based).

JavaScript中面向对象的实现方式与Java不同。

在Java中，每一个对象都是某一个类的实例；而在JavaScript中，每一个对象都有一个原型对象。

> The prototypal inheritance model is more powerful than the classic model.

原型对象

Each object has a private property which holds a link to another object called its **prototype**.

That prototype object has a prototype of its own, and so on until an object is reached with `null` as its prototype.

By definition, `null` has no prototype, and acts as the final link in this **prototype chain**.

        Object.getPrototypeOf(Object.prototype) === null

JavaScript中的每个对象都有一个内部属性，它是另一个对象的引用。

Following the ECMAScript standard, the n2otation `someObject.[[Prototype]]`

Since ECMAScript 2015, the `[[Prototype]]` is accessed using the accessors `Object.getPrototypeOf` and `Object.setPrototypeOf`

This is equivalent to the JavaScript property `__proto__` which is non-standard but implemented by many browsers.

要注意的是：对象并没有prototype这个属性。

It should not be confused with the `func.prototype` property of functions, which instead specifies the `[[Prototype]]` to be assigned to all instances of 

### Different ways to create objects and the resulting prototype chain

        var o = {a:1};
        
        // Object.getPrototypeOf(o) === Object.prototype
        // o.__proto__ === Object.prototype
        
        // o ---> Object.prototype ---> null
        
        function f() {}
        
        // Object.getPrototypeOf(f) === Function.prototype
        
        o ---> Function.prototype ---> Object.prototype ---> null
        
通过对象字面量创建的对象的原型对象是 `Object.prototype`。


All objects will have a `constructor` property.

每一个对象都有一个constructor属性，但在打印这个对象时，这个属性并不会显示出来。

Objects created without the explicit use of a constructor function





Objects in JavaScript have an internal property, denoted in the specifications as `[[Prototype]]`, which is simply a reference to another object.

What is the `[[Prototype]]` reference used for?

原型链

Where exactly does the `[[Prototype]]` chain "end"?

The top-end of every normal `[[Prototype]]` chain is the built-in `Object.prototype`.

When trying to access a property of an object, 

Why does one object need to link to another object?

Following the ECMAScript standard, 

有趣的是，在

## Prototype

Every object has a prototype (exceptions can be with some system objects).

Communication with a prototype is organized via the internal, implicit and inaccessible directly `[[Prototype]]` property.

A prototype can be either an object, or the `null` value.
 
`Constructor` property is set to function's `prototype` property at function creation.The value of this property is the circular reference to the function itself.
 
 The `constructor` belongs to a prototype and is accessible to object via inheritance.
 
Via the inherited `constructor` property instances can indirectly get the reference to the prototype object.
 
If we add new or modify existing property 

All objects will have a `constructor` property.

Object created without the explicit use of a constructor function
 
#### Non-standard `_proto_` property

 
#### Object is independent from its constructor
 
 

虽然Object构造函数或对象字面量都可以用来创建单个对象，但这些方式有个明显得缺点:使用同一个接口创建很多对象，会产生大量的重复代码.

#### 工厂模式
软件工程领域广为人知的设计模式

#### 构造函数
像Object和Array这样的原生构造函数，在运行时会自动出现在执行环境中，此外，也可以创建自定义的构造函数。

按照惯例，构造函数始终都应该以一个大写字母开头，而非构造函数则应该以一个小写字母开头.

要通过构造函数来创建实例，需使用new关键字.



#### 原型模式

看完下面的内容，你应该能回答这个问题：对象和函数中的哪些属性是与原型的实现相关的（包括内部属性和浏览器提供的特殊属性）？

我们创建的每个函数都有一个`prototype属性，这个属性是一个指针，指向一个对象，而这个对象的用途是包含可以由特定类型的所有实例共享的属性和方法。

    function Person(){}
    
    Person.prototype.name = "Nicholas";
    Person.prototype.sayName = function() {
      alert(this.name);
    };
    
在默认情况下，所有原型对象都会自动获得一个`constructor`属性，这个属性包含一个指向prototype属性所在函数的指针。

当调用构造函数创建了一个新实例后，该实例的内部将包含一个指针（内部属性），指向构造函数的原型对象。ECMA-262-5中管这个指针叫[Prototype]]。

虽然在脚本中没有标准的方式访问[[Prototype]]，但Firefox, Safari和Chrome在每个对象上都支持一个属性`__proto__`。
        
        function Person(){}
        
        let p = new Person();
        
        console.log(Person.prototype === p.__proto__); // true
        
        console.log(Person.prototype.__proto__);

要明确的一点是，这个连接存在于实例与构造函数的原型对象之间，而非与构造函数。

还要注意的一点是，原型对象也是一个普通对象，它也有`__proto__`属性。

ECMAScript5增加了一个新方法，叫`Object.getPrototypeOf()`,这个方法返回[[Prototype]]的值。

虽然可以通过对象实例访问保存在原型中的值，但却不能通过对象实例重写原型中的值。如果我们在实例中添加了一个属性，而该属性与实例原型中的一个属性同名，该属性将会屏蔽原型中的那个属性。

使用hasOwnProperty()方法可以检测一个属性是存在于实例中，还是存在于原型中。

#### 更简单的原型语法

#### 原生对象的原型
原型模式的重要性不仅体现在创建自定义类型方面，就连所有原生的引用类型，都是采用这种模式创建的。

####原型对象的问题




#### 原型链

ECMAScript中描述了原型链的概念，并将原型链作为实现继承的主要方法，只在给定属性存在于

组建自定义类型的最常见方式，就是组合使用构造函数模式与原型模式。构造函数模式用于定义实例属性，而原型模式用于定义方法和共享的属性。

#### 相关概念

Object.prototype.isPrototypeOf()


"Class/Inheritance" describes a certain form of code organization and  architecture - a way of modeling real world problem domains in our software.



Some languages (like Java) don't give you the choice, so it's not very *optional* at all

### JavaScript "Classes"

JS has had some class-like syntactic elements (like `new` and `instanceof`) for quite awhile, and more recently in ES6, like the `class` keyword.

But does that mean JavaScript actually has classes?

Plain and simple: **No**.

JS tries to satisfy the extremely pervasive desire to design with classes by providing seemingly class-like syntax.

Classes are an optional pattern in software design, and you have the choice to use it or not.

The traditional metaphor for "class" and "instance" based thinking comes from a building construction.

A class is a blue-print. To actually get an object we can interact with, we must build (aka, "instantiate") something from the class.

The end result of such "construction" is an object, typically called an "instance", which we can directly call all methods on and access any public data properties from.

This object is a copy of all the characteristic described by the class.

You don't generally use an object instance to directly access and manipulate its class.

### Class Inheritance

In class-oriented languages, not only can you define a class which can be instantiated itself, but you can define another class that **inherits** from the first class.

The second class is often said to be a "child class" whereas the first is the "parent class".

    class Vehicle

### Polymorphism

Any method can reference another method (of the same or different name) at a higher level of the inheritance hierarchy.

In many languages, the keyword `super` is used.

Another aspect of polymorphism is that a method name can have multiple definitions at different level of the inheritance chain
