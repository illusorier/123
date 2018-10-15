什么是函数？

函数对任何语言来说都是一个核心的概念。

通过函数可以封装任意多条语句，而且可以在任何地方、任何时候调用执行。

A function is a code snippet.

### 函数的定义

ECMAScript中的函数使用function关键字来声明，后跟一组参数以及函数体：

      function example(input) {
        console.log(input);
      }

ECMAScript中的函数在定义时不必指定是否返回值。

实际上，任何函数在任何时候都可以通过return语句后跟要返回的值来实现返回值。

位于return语句之后的任何代码都永远不会执行。

另外，return语句也可以不带有任何返回值，这些情况下，函数在停止执行后将返回undefined值。

函数内部特殊的对象

The `arguments` object is an `Array-like` object corresponding to the arguments passed to a function.

      function f (a, b, c) {
          console.log(arguments[0]);
          console.log(arguments[1]);
          console.log(arguments[2]);
      }
       
The `length` property specifies the number of arguments expected by the function.

#### 函数的调用

函数可以通过其函数名来调用，后面还要加上一对圆括号和参数(圆括号中的参数如果有多个，可以用逗号隔开)。

When a function is called, arguments are passed to the function as input, and the function can optionally return an output.

        function f() {}
        
        console.dir(f);
        
### Different types of functions

An *anonymous function* is a function without a function name:

        function () {};
        
        () => {};

首先我们从函数的类型来理解。

In ECMAScript there are three function types and each of them has its own features.

除此之外，函数还有其他的一些分类方式：anonymous function, named function, inner function and outer function。

How each type influences *variables object*.


#### Function Expression

函数表达式对只学过一点C和Java的我来说是个全新的东西。

A Function Expression (FE) is a function which:

- in the source code can only be at the expression position;
- can have an optional name;
- it's definition has no effect on variable object;
- and is created at the code execution stage;


        var foo = function _foo() {
            ...
        };
        
What's important here to note 

#### Functions created via Function constructor

This type of function objects is discussed separately from FD and FE since 

#### 函数的参数

接下来我们从参数的角度理解。

ECMAScript函数的参数与大多数其他语言中函数的参数有所不同，不介意传递进来多少个参数，也不在乎传进来的参数是什么类型。

在函数内部，有两个特殊的对象：`arguments`和`this`。

arguments是一个类数组对象，包含着传入函数中的所有参数。

也就是说，我们甚至可以在定义时不命名任何参数，而在实际运行时通过arguments访问实际传入的参数。



    function howManyArgs() {
      alert(arguments.length);
    }
    
    howManyArgs("string", 45); // 2
    howManyArgs(); // 0
    howManyArgs(12); // 1
     


这个事实说明了ECMAScript函数的一个重要特点:命名参数只提供便利，但不是必需的。

其他语言可能需要事先创建一个函数签名，而将来的调用必需与该签名一致。

虽然arguments的主要用途是保存函数参数，但这个对象还有一个名为callee的属性，该属性是一个指针，指向拥有这个arguments对象的函数。

函数内部的另一个特殊对象是this，其行为与Java和C#中的this大致类似。

#### 函数的对象性

每个函数都是Function类型的实例，而且都与其他引用类型一样具有属性和方法。

对ECMAScript中的引用类型而言，prototype是保存它们所有实例方法的真正所在

ECMAScript 5也规范化了另一个函数对象的属性：caller。

这个属性中保存着调用当前函数的函数的引用，如果是在全局作用域中调用当前函数，它的值为null。

每个函数都包含两个非继承的方法：`apply`和`call`。

这两个方法的用途都是在特定的作用域中调用函数，实际上等于设置函数体内this对象的值。

首先，apply()方法接收两个参数：一个是在其中运行函数的作用域

### Algorithm of function creation

    F = new NativeObject();
            
    // property [[Class]] is "Function"
    F.[[Class]] = "Function"
    
    F.[[Prototype]] = Function.prototype
    
    // reference to function itself
    // [[Call]] is activated by call expression F()
    F.[[Call]] = <reference to function>
    
    // and it is 
    F.[[Construct]] = internalContructor
    
    _objectPrototype = new Object();
    _objectPrototype.constructor = F

## Closure

### General theory

函数式编程

Before the discussion of closures directly in ECMAScript, it is necessary to specify a number of definitions from the general theory of **functional programming**.

As is known, in functional languages (and ECMAScript supports this paradigm and stylistics), functions are data, they can be **assigned** to **variables**, passed as **arguments** to other functions, **returned** from functions.

### Definitions

A functional argument("Funarg") - is an argument which value is a function.

    function exampleFunc(funArg) {
      funArg();
    }
    
    exampleFunc(function () {
      console.log('funArg');
    }
    
The actual parameter related with "funArg" in this case is the anonymous function passed to the `exampleFunc` function.

高序函数

In turn, the function which receives another function as the argument is called a **higher-order function (HOF)**.

A function can also be returned as a value from another function.

The functions which return other functions are called *functions with functional value*.

Functions which can participate as normal data, be passed as arguments, receive functional arguments or be returned as functional value, are called *first-class* functions.

In ECMAScript all functions are first-class.

Local variables which are defined in the passed functional argument are of course accessible at activation of this function, since the variable object which stores the data of the context is created every time on entering the context.

### Funarg problem

In stack-oriented programming languages local variables of functions are stored on a stack which is pushed with function arguments every time when the function is called.

On return from the function the variables are removed from the stack.

This model is a big restriction for using functions as *functional values*.

A *free variable* is a variable which is used by a function, but is neither a parameter, nor a local variable of the function.

    function testFn() {
    
      var localVar = 10;
      
      function innerFn(innerParam) {
        console.log(innerParam + localVar);
      }
      
      return innerFn;
    }
    
    var someFn = testFn();
    someFn(20);
    


### Closure

A *closure* is combination of a *code block* and *data* of a context in which this code block is created.




## Closure

In ECMAScript, functions are the first-class objects.
This terms means that functions may be passed as arguments to other functions. Also functions may be returned from other functions.

There are two conceptual problems related with "funargs" and "functional values".

And to solve these problems, the concept of closures was invented.
 
First problem appears when a function is returned "up" (to the outside) from another function and uses already mentioned above free variables.

To be able access variables of the parent context even after the parent context ends, the inner function at creation moment saves in it's [[Scope]] property.

    function foo() {
      var x = 10;
      return function bar() {
        console.log(x);
      }
    }
    
    var returnedFunction = foo();
    
    var x = 20;
    
    returnedFunction(); // 10

This style of scope is called the static (or lexical) scope. In general theory, there is also a dynamic scope.

The second problem is a "downward problem". In this case a parent context may exist, but may be an ambiguity with resolving an identifier.
    
ECMAScript has complete support of closures, which technically are implemented using [[Scope]] property of functions.

A closure is a combination of a code block (in ECMAScript this is a function) and statically/lexically saved all parent scopes.

**closure is all around you in JavaScript,you just have to recognize and embrace it.


> Closure is when a function is able to remember and access its lexical scope even when that function is executing outside its lexical scope.

    function foo() {
      var a = 2;
      
      function bar() {
        console.log(a);
      }
      
      return bar;
    }
    
    var baz = foo();
    
    baz();
    
The function `bar()` has a *closure* over the scope of `foo()` (and indeed,even over the rest of the scopes it has access to, such as the global scope in our case).

`bar()` close over the scope of `foo()`.

Whatever facility we use to *transport* an inner function outside of its lexical scope

    for (

下面这个例子结合了闭包、单线程和Event Loop相关知识：

        function f() {
        	function fInner() {}
          
        	setTimeout(function(){
                 f1.a = 1;
             },0);
          
             return fInner;
        }
        
        var fReturned = f();
        console.log(fReturned.a);
        
        setTimeout(function(){
          	console.log(fReturned.a);
        },0);

## 相关概念
Function.caller - this property returns the function that invoked the specified function.

If the function f was invoked by the top level code,the value of f.caller is null.
    
#### Function.prototype.bind()

The **bind()** method creates a new function that, when called, has its this keyword set to the provided