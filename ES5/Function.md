什么是函数

A function is a code snippet.

A function in JavaScript is also an object.

函数内部特殊的对象

The `arguments` object is an `Array-like` object corresponding to the arguments passed to a function.

        function f (a, b, c) {
            console.log(arguments[0]);
            console.log(arguments[1]);
            console.log(arguments[2]);
        }
       
       
The `length` property specifies the number of arguments expected by the function.

函数的调用

When a function is called, arguments are passed to the function as input, and the function can optionally return an output.

        function f() {}
        
        console.dir(f);
        
看完下面的内容，你应该能回答这个问题：这时候在控制台打印出来的是什么？

### Different types of functions

An *anonymous function* is a function without a function name:

        function () {};
        
        () => {};

首先我们从函数的类型来理解。

In ECMAScript there are three function types and each of them has its own features.

除此之外，函数还有其他的一些分类方式：anonymous function, named function, inner function and outer function。

How each type influences *variables object*.

#### Function Declaration

函数声明是我们最熟悉的一种创建函数的方式。
    
A Function Declaration (FD) is a function which:

- has a required name;
- position: either at the Program level or directly in the body of another function;
- is created on entering the context stage;
- influences variable object;

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

### Arguments

接下来我们从参数的角度理解。

ECMAScript函数的参数与大多数其他语言中函数的参数有所不同，不介意传递进来多少个参数，也不在乎传进来的参数是什么类型。

    function howManyArgs() {
      alert(arguments.length);
    }
    
    howManyArgs("string", 45); // 2
    howManyArgs(); // 0
    howManyArgs(12); // 1
     
这个事实说明了ECMAScript函数的一个重要特点： 命名参数只提供便利，但不是必需的。

其他语言可能需要事先创建一个函数签名，而将来的调用必需与该签名一致。

ECMAScript中的参数在内部是用一个数组来表示的

### A Function is also an Object

接下来我们从函数的对象性理解。

在函数内部，有两个特殊的对象：`arguments`和`this`。

ECMAScript 5也规范化了另一个函数对象的属性：caller。

这个属性中保存着调用当前函数的函数的引用，如果是在全局作用域中调用当前函数，它的值为null。

每个函数都包含两个非继承的方法：`apply`和`call`。

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