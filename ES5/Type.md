一个大的议题就是如何学习和理解一个编程语言。

一些常见的building block，比如变量、常量、值、类型、函数、运算符、语句、数据结构等等。

比如面向对象语言都会共有的一些概念，类，继承等等。

## JavaScript的类型

本文的绝大多数英文内容摘选自《You Don't know JS》 一书的电子版(https://github.com/getify/You-Dont-Know-JS)

由于关于类型的内容分布在本书的若干册中，如 "up & going", "types & grammar" 和 "this & object prototypes",本文对其稍微整理方便自己理解

Most developers would say that a dynamic language (like JS) does not have types.

Let's see what the ES5.1 specification has to say on the topic:

> Algorithm within this specification manipulate values each of which has an associated type.

We're going to use this rough definition: a type is an intrinsic, built-in set of characteristics that uniquely identifies the behavior of a particular value and distinguishes it from other

抛开学术性定义不谈，我们为什么需要类型这个概念 => 类型转换！

Beyond academic definition disagreements, why does it matter if JavaScript has types or not?

Having a proper understanding of each type and 

关于JS类型的其他描述：

JavaScript is weakly typed.

JavaScript is also dynamically typed.

It is most certainly "untyped", but its weakly typed nature allows for a lot of flexibility in terms of implicit conversions.

在比如Java和一些其他语言当中，声明变量除了要给定变量名，还要确定该变量的类型。

相比而言，JS没有这样的限制，JS中的变量是不具有有类型的，而JS中的值是具有类型的，我们可以用`typeof`运算符获得相应值得类型。

JavaScript has typed values, not typed variables.The following built-in **types** are available.

Only values have types in JavaScript; variables are just simple containers for those values.

JavaScript defines seven built-in types:

- `string`
- `number`
- `boolean`
- `null` and `undefined`
- `object`
- `symbol` -- added in ES6!

All of these types except `object` are called "primitive".

原始类型

ECMAScript变量可能包含两种不同数据类型的值。

基本类型值指的是简单的数据段，而引用类型值指那些可能由多个值构成的对象。

在将一个值赋给变量时，解析器必须确认这个值是基本类型值还是引用类型值。

我们可以通过 `typeof` 运算符来获得某个变量的类型。

JavaScript provides a `typeof` operator that can examine a value and tell you what type it is.

奇妙的是，`typeof`的返回值和变量的类型并不是一一对应的关系。

Surprisingly, there's not an exact 1-to-1 match with the seven built-in types we just listed.

    typeof undefined    // "undefined"
    typeof true     // "boolean"
    type of 17      // "number"
    typeof "17"     // "string"
    typeof { id: 17 }   // "object"
     
    typeof Symbol()     // "symbol"
    
在原始类型中，null是一个比较特殊的例子。
       
`type of null` is an interesting case, because it returns `"object"`, when you'd expect `"null"`.

        typeof null === "object";   // true
        
那么，为什么不去修复这个bug？

Also, note `a = undefined`. We're explicitly setting a to the undefined value, but that is behaviorally no different from a variable that has no value set yet.

        typeof function a(){ /* .. */ } === "function";     // true
        


## Objects

Objects are the general building block upon which much of JS is built.

They are one of the 7 primary types (called "language types" in specification) in JS.

**It's a common mis-statement that "everything in JavaScript is an object". This is clearly not true.**

*Simple primitives* (`string`, `number`, `boolean`, `null`, and `undefined`) are not themselves `objects`.

There are a few special object sub-types, which we can refer to as *complex primitives*.

`function` is a sub-type of object (technically, a "callable object").

`typeof` returns `"function"`,which implies that a `function` is a main type -- and can thus have properties,but you typically will only use function object properties in limited cases.

`array` are also a form of objects, with extra behavior. The organization of contents in arrays is slightly more structured than for general objects.

#### Built-in Objects

There are several other object sub-types, usually referred to as built-in objects.

- `String()`
- `Number()`
- `Boolean()`
- `Object()`
- `Function()`
- `Array()`
- `Date()`
- `RegExp()`
- `Error()`

These built-ins have the appearance of being actual types, even classes.

But in JS, these are actually just built-in functions.

Each of these built-in functions can be used as a constructor, with the result being a newly *constructed* object of the sub-type.

There are a couple of other value types that you will commonly interact with in JavaScript programs:*array* and *function*.

But rather than being proper built-in types, these should be thought of more like subtypes -- specialized versions of the `object` type.

## Arrays

As compared to other type-enforced languages, JavaScript `array`S are just containers for any type of value, from `string` to `number` to `object` to even another `array`.

### Array-Likes

For example, various DOM query operations return lists of DOM elements that are not true `array`S but are `array`-like enough for our conversion purposes

Some JavaScript objects,such as the *NodeList* returned by *document.getElementsByTagName()*  or the *arguments* object made available within the body of a function, look and behave like arrays on the surface but do not share all of their methods.

JavaScript's standard, built-in objects, including their methods and properties.

Other objects in the global scope are either created by the user script or provided by the host application.

### Typed Arrays

JavaScript typed arrays are array-like objects and

As you already know, *Array* objects grow and shrink dynamically 

### internal [ [ Class ] ]

Values that are `typeof "object"` (such as an array) are additionally tagged with an internal `[[Class]]` property (think of this more as an ).

This property cannot be accessed directly, but can generally be revealed indirectly by borrowing the default `Object.prototype.toString(..)` method called against the value.

    Object.prototype.toString.call( [1,2,3] ); // "[object Array]"
    
In most cases, this internal `[[Class]]` value correspond to the built-in native constructor that's related to the value, but

    Object.prototype.to
    

### Boxing Wrapper

基本包装类型

为了便于操作基本类型值，ECMAScript还提供了3个特殊的引用类型: Boolean、Number和String.

These object wrappers serve a very important purpose.

Primitive values don't have properties or methods, so to access `.length` or `toString()` you need an object wrapper around the value.

Thankfully, JS will automatically box (aka wrap) the primitive value to fulfill such accesses.

    var a = "abc";
    
    a.length; // 3
    a.toUpperCase(); // "ABC"
    
##### instanceof

The **instanceof operator** tests whether an object in its prototype chain has the prototype property of a constructor

    object instanceof constructor
    
##### typeof

The **typeof** operator returns a string indicating the type of the unevaluated operand.

    typeof operand

##### Object.prototype.toString()

The **toString()** method returns a string representing the object.

If this methods is not overridden in a custom object,toString() returns "[object type]",where *type* is the object type.

    var o = new Object();
    o.toString(); // returns [object Object]


Every object has a toString() method that is automatically called when the object is to be represented 
    
Using toString() to detect object class: toString() can be used with every object and allows you to get its class.

To use the Object.prototype.toString() with every object, you need to call *Function.prototype.call()* or *Function.prototype.apply()* on it, passing the object you want to inspect as the first parameter called thisArg.

构成某字符串的字符都是数字，如何将该字符串转换成相应的数？

"123" => 123

The `parseInt()` function parses a string argument and returns an integer of the specified radix.



