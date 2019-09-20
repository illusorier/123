本节讨论对象。

什么是对象？

所有编程语言都提供抽象机制。

可以认为，人们所能够解决的问题的复杂性直接取决于抽象的类型和质量。

所谓"类型"指"所抽象的是什么?"。

就我目前所接触到的高级语言来说，不管它是否OOP，

理解Object引用类型的角度：

Object是一种数据结构，就像基本数据类型Number、String或Arrays、Lists等较为复杂的数据结构。

## 本节所用词汇

Reference type 

Value type

值类型 引用类型

Reference value (== object)

objects are considered to be *instances* of a particular *reference type*.

对象是某个特定引用类型的实例

比如所Array就是一种reference type,而Array的实例则被称为对象

In ECMAScript, reference types are structures used to group data and functionality together.

Although instances of Objects don't have much functionality, they are ideally suited to storing and transmitting data around an application.

Object的实例可用于在应用程序中存储和传输数据。

ECMA-262 defines an object as an "unordered collections of properties each of which contains a primitive value, object or function."

## Objects

在JavaScript中如何创建对象？

Objects come in two forms: the declarative (literal) form, and the constructed form.

创建Object实例的方式有两种:

        var myObject = {
            a: 2
        };

        var myObject = new Object();
        myObject.a = 2;

第一种是我们在日常编程中使用的


The only difference really is that 

Java中创建对象的方式只有后者。

    MyClass a = new MyClass();

对象字面量是对象定义的一种简写形式，目的在于简化创建包含大量属性的对象的过程。

It's extremely uncommon to use the "constructed form" for creating objects.

You would pretty much always want to use the literal syntax form.

The same will be true of most of the built-in objects.

### Contents

The contents of an object consists of values (any type) stored at specifically named locations, which we call properties.

对象中保存的是一系列键值对。

    var myObject = {
        a:2 
    };

    myObject.a;

    myObject[a];

To access the value at the location `a` in `myObject`, we need to use either `.` operator or the `[]` operator.

They both access the same location.



### Computed Property Names

The `myObject[...]` property access syntax we just described is useful if you need to use a computed expression value as the key name

ES6 adds *computed property names*, where you can specify an 

    var prefix = "foo";
    
    var myObject = {
      [prefix + "bar"]: "hello"
    }
    
    console.log(myObject.foobar); 

The most common usage of *computed property names* will probably be for ES6
    
### Property Descriptors

属性描述符

Prior to ES5, the JavaScript language gave no direct way for your code to inspect or draw any distinction between the characteristics of properties, such as whether the property is read-only or not.

But as of ES5, all properties are described in terms of a **property descriptor**.

也就是说，每个ECMAScript中的对象的每一个属性都有对应的属性描述符，我们可以访问甚至修改它们。

The `Object.getOwnPropertyDescriptor(obj, prop)` method returns a property descriptor for 

We can use `Object.defineProperty(..)` to add a new property, or modify an existing one (if it is `configurable`!).

The static method `Object.defineProperty(obj, prop, descriptor)` method defines a new property directly on an object, or modifies an existing property on an object, and returns the object.

        var myObject = {};
        
        Object.defineProperty(myObject, "a", {
            value: 2,
            writable: true,
            configurable: true,
            enumerable: true
        });
        
        myObject.a; // 2
            
Property descriptors present in objects come in two main flavors:

##### Writable

The ability for you to change the value of a property is controlled by `writable`.

##### Configurable

As long as a property is current configurable, we can modify its descriptor definition, u

Changing `configurable` to `false` is a one-way action, and cannot be undone.

Another thing  `configurable:false` prevents is the 

The `Object.preventExtensions()`

- [[Configurable]] - As long as a property is currently configurable,we can modify its descriptor definition
.
- [[Writable]] - The ability for you to change the value of a property.

- [[Enumerable]] - if the property is enumerable by a `for..in` loop.

- [[Value]]

#### `[[Get]]`

当我们试图获取某个对象的属性的值时，发生了什么？

        var myObject = {
          a: 2
        }
        
        myObject.2;        
    
The `myObject.a` is a property access, but it does not *just* look in the `myObject` for a property of the name `a`, as it might seem. 

According to the spec, the code above actually performs a `[[Get]]` operation (kinda like a function call: `[[Get]]()`) on the `myObject`.

The default build-in  `[[Get]]` operation for an object *first* inspects the object for a property of the requested name.

And if it finds it, it will return the value accordingly. 

遍历原型链

If not, it will traversal the `[[Prototype]]` chain, if any.

若查找不到相应值便发回`undefined`。

One important result of this `[[Get]]` operation is that if it cannot through any means come up with a value for the requested property, it instead returns the value `undefined`.

This behavior is different from when you reference variables by their identifier names.

#### `[[Put]]`

Since there's an internally defined `[[Get]]` operation for getting  a value from a property, it should be obvious there's also a 

### Getters and Setters

The default `[[Put]]` and `[[Get]]` operations for objects completely control 

ES5 introduced a way to override part of these default operation, 

When you define a property to have either a getter or a setter or both, its definition becomes an "accessor descriptor" (as opposed to a "data descriptor").

For accessor descriptor, the `value` and `writable` characteristics of the descriptor are moot and ignored.

And instead JS considers the `set` and `get` characteristics of the property (as well as `configurable` and `enumerable`).

        var myObject = {
            get a() {
                return 2;
            }
        }
        
        Object.definePropert(myObject, "a", {
            get: function() {
                return 2;
            }
        });

The `get` syntax binds an object property to a function that will be called when that property is looked up.

### Prototypes

#### Setting & Shadowing Properties

    myObject.foo = "bar";
    
#### Class

All functions by default get a public,non-enumerable property on them called `prototype`.

    function Foo() {
      // ...
    }
    
    var a = new Foo();
    
    Object.getPrototypeOf(a) === Foo.prototype;
    
When `a` is created by calling

#### Constructors

    function Foo() {
      // ...
    }
    
    Foo.prototype.constructor === Foo;
    
     var a = new Foo();
     a.constructor === Foo;
     
The `Foo.prototype` object by default gets a public,non-enumerable property called `.constructor` ,and this property is a reference back to the function that the object is associated with.

Moreover,we see that object `a` created by the "constructor" call `new Foo()` seems to also have a property called `.contructor` which similarly points to "the function which created it".

Generally,such references should be avoided where possible.


What is the prototype of empty object?

Where exactly does the `[[Prototype]]` chain "ends"?

    Object.getPrototypeOf({}) === Object.prototype;
    
    Object.getPrototypeOf(Object.prototype) === null;
    
    

    


## OOP:The general theory

ECMAScript supports multiple programming paradigms,which are:

ECMAScript is the *object-oriented* programming language with the *prototype based* implementation.

Prototype based model of OOP has a number of differences from the *static class based* paradigm.

With

#### Classes and objects

The class represents a *formal abstract* set of the generalized characteristics of an instance.

Characteristics of instances are: properties(object description) and methods(object activity)

#### Hierarchical inheritance

For improvement of a *code reuse*, 

Resolution of methods when calling methods from instances: if the method is not found in the native class, search in the class-ancestor,in the ancestor of the class-ancestor.

In contrast with methods which at inheritance

#### Key concepts of class based model
- to create an object first it is necessary to define its class;
- being created, the class cannot(because of the static model) change characteristics of their instances.
- instances cannot have neither additional own(unique) behavior,nor the additional properties which are distinct from structure and behavior of the class.

#### Prototype based model
Here the basic concept is dynamic mutable objects.

Such objects can independently store all their characteristics (properties,methods) and do not need the class.

Moreover,because of dynamics, they can easily change (add,delete,modify) their characteristics.

The code reuse in this case is achieved not via extending the classes, but by referencing to, so-called, prototype.

#### Delegation based model
Any object can be used as a prototype of another object and 






## ECMAScript implementation

#### Object type

从数据结构的角度看:

Object is an unordered collection of key-value pairs.

#### Dynamic nature


#### Property attributes

ECMA262-5中定义的这些特性是为了实现JavaScript引擎，因此在JavaScript中不能直接访问它们。为了表示特性是内部值，该规范把它们放在了两对方括号中。

ECMAScript中有两种属性：数据属性和访问器属性。

1. 数据属性


- [[Configurable]] -
- [[Writable]] - attempt to write value to the property is ignored；however,
- [[Enumerable]] - if the property is enumerable by a `for..in` loop.
- [[Value]]

要修改属性默认的特性，必须使用ECMAScript的Object.defineProperty()方法

#### Internal properties and methods

Objects also can have a number of internal properties which are a part of implementation and inaccessible for ECMAScript programs directly.

however as we will see below,some implementations allow the access to some such properties.

These properties by the convention are enclosed with *double square brackets* - [[]]

- `[[Prototype]]` - the prototype of this object;
- `[[Class]]` - a string representation of object's kind (for example,`Object`,`Array`,`Function`,etc);
- `[[Get]]` - a method of getting the property's value;
- `[[Put]]`

## Constructor

Objects in ECMAScript are created via constructors.

Constructor is a function that creates and initializes the newly created object.

For creation(memory allocation) the [[Construct]] internal method of 

## Prototype

Every object has a prototype (exceptions can be with some system objects).

Communication with a prototype is organized via the internal,implicit and inaccessible directly `[[Prototype]]` property.

A prototype can be either an object,or the
 `null` value.
 
#### Property `constructor`

As we can see in algorithm of function objects creation,`constructor` property is set to constructor function at function creation.

The value of this property is the circular reference to the function itself.

    function A() {}
    var a = new A();
    console.log(a.constructor);
    console.log(a.constructor === A);
    
The `constructor` is not a owned property of the created object.
 
The `constructor` belongs to a prototype and is accessible to object via inheritance.
 
Via the inherited `constructor` property instances can indirectly get the reference to the prototype object.
 
    function A() {}
    A.prototype.x = new Number(10);
    
    var a = new A();
    console.log(a.constructor.prototype);
    
    console.log(a.x);
    console.log(a.constructor.prototype.x);
    
Both `constructor` and `prototype` 
 
If we add new or modify existing property in the original prototype via the function's `prototype` property, instances will see the newly added properties.
 
#### Object is independent from its constructor
 
 

虽然Object构造函数或对象字面量都可以用来创建单个对象，但这些方式有个明显得缺点:使用同一个接口创建很多对象，会产生大量的重复代码.

#### 工厂模式
软件工程领域广为人知的设计模式

#### 构造函数
像Object和Array这样的原生构造函数，在运行时会自动出现在执行环境中，此外，也可以创建自定义的构造函数。

按照惯例，构造函数始终都应该以一个大写字母开头，而非构造函数则应该以一个小写字母开头.

要通过构造函数来创建实例，需使用new关键字.



#### 原型模式

我们创建的每个函数都有一个prototype(原型)属性，这个属性是一个指针，指向一个对象，而这个对象的用途是包含可以由特定类型的所有实例共享的属性和方法。

    function Person(){}
    Person.prototype.name = "Nicholas";
    Person.prototype.sayName = function() {
      alert(this.name);
    };
    
在默认情况下，所有原型对象都会自动获得一个constructor属性，这个属性包含一个指向prototype属性所在函数的指针。

当调用构造函数创建了一个新实例后，该实例的内部将包含一个指针（内部属性），指向构造函数的原型对象。ECMA-262-5中管这个指针叫[[Prototype]]。

虽然在脚本中没有标准的方式访问[[Prototype]]，但Firefox,Safari和Chrome在每个对象上都支持一个属性__proto__。

要明确的一点是，这个连接存在于实例与构造函数的原型对象之间，而非与构造函数。

ECMAScript5增加了一个新方法，叫Object.getPrototypeOf(),这个方法返回[[Prototype]]的值。

虽然可以通过对象实例访问保存在原型中的值，但却不能通过对象实例重写原型中的值。如果我们在实例中添加了一个属性，而该属性与实例原型中的一个属性同名，该属性将会屏蔽原型中的那个属性。

使用hasOwnProperty()方法可以检测一个属性是存在于实例中，还是存在于原型中。

#### 更简单的原型语法

#### 原生对象的原型
原型模式的重要性不仅体现在创建自定义类型方面，就连所有原生的引用类型，都是采用这种模式创建的。

####原型对象的问题




#### 原型链

ECMAScript中描述了原型链的概念，并将原型链作为实现继承的主要方法，只在给定属性存在于

组建自定义类型的最常见方式，就是组合使用构造函数模式与原型模式。构造函数模式用于定义实例属性，而原型模式用于定义方法和共享的属性。



对象字面量是对象定义的一种简写形式

一般来说，访问对象属性时使用的都是点表示法，这也是

在使用对象字面量语法时，属性名也可以使用字符串

Object-or

Object类型是ECMAScript原生支持的一种类型。

