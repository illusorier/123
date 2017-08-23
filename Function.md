## Types of functions

In ECMAScript there are three function types and each of them has its own features.

How each type influences *variables object*

#### Function Declaration

- has a required name;
- position: either at the Program level or directly in the body of another function;
- is created on entering the context stage;
- influences variable object;

#### Function Expression

- in the source code can only be 
- can have an optional name;
- it's definition has no effect on variable object;


## General theory

Before the discussion of closures directly in ECMAScript, it is necessary to specify a number of definitions from the general theory of **functional programming**.

As is known, in functional languages (and ECMAScript supports this paradigm and stylistics), functions are data,

### Definitions

A functional argument("Funarg") - is an argument which value is a function.

    function exampleFunc(funArg) {
      funArg();
    }
    
    exampleFunc(function () {
      console.log('funArg');
    }
    
The actual parameter related with "funArg" in this case is the anonymous function passed to the `exampleFunc` function.

In turn, the function which receives another function as the argument is called a **higher-order function (HOF)**.

A function can also be returned as a value from another function.

The functions which return other functions are called *functions with functional value*.

Functions which can participate as

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

A *closure* is combination of a *code block* and *data* of 

#### Algorithm of function creation

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


## 相关概念
Function.caller - this property returns the function that invoked the specified function.

If the function f was invoked by the top level code,the value of f.caller is null.

#### Function.prototype.call()

The call() method calls a function with a given this value and arguments provided individually.

    fun.call(thisArg, arg1, arg2, ...)

A 

#### Function.prototype.apply()

The **apply()** method calls a function with a given this value, and arguments provided as an array (or an array-like object).

    fun.apply(thisArg, [argsArray])
    
While the syntax of this function is almost identical to that of call(), the fundamental difference is that call() accepts an argument list, while apply() accepts a single array of arguments.

You can 
    
#### Function.prototype.bind()

The **bind()** method creates a new function that, when called, has its this keyword set to the provided