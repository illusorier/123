## Execution Contexts && Variable Object

执行上下文是从JS引擎角度理解JS的一个出发点。

背景：

Always in programs we declare functions and variables which then successfully use building our systems.

But how and where the interpreter finds our data (functions, variable)?

What occurs, when we reference to needed objects?

Variables are closely related with execution context.

从数据结构的角度理解，执行上下文们本身是一个栈。

从JS引擎执行代码的过程来看，可执行的代码可以被分为两类:全局代码和函数代码，分别对应

当执行JS中上述两类代码时，

Every time when control is transferred to ECMAScript executable code, control is entered an execution context.

Set of active execution contexts forms a stack.

The bottom of this stack is always a global context, the top - a current(active) execution context.

所有被激活的执行上下文形成一个栈。

For examples, we define the stack of execution contexts as an array:

    ECStack = [];

The stack is modified ( pushed/popped ) during the entering and exiting various kinds of EC.

The stack is pushed every time on entering a function ( even if the function is called recursively or as the constructor), and also at built-in eval function work.

It is necessary to notice that the code of concrete function does not include codes of the inner functions.

#### Types of executable code

执行上下文 可执行代码的类型

With abstract concept of an execution context, the concept of type of an executable code is related.

可执行代码的类型也可以理解为执行上下文的类型。

- Global code: This type of code is processed at level `program`.

- Function code: On entering the function code (all kinds of functions),`ECStack` is pushed with new elements.

It is necessary to notice that the code of concrete function dose not include codes of the inner functions.

## Variable Object





If variables are related with the execution context,it should know where its data are stored and how to get them

This mechanism is called a *variable object*.

*A variable object(VO)* is a special object related with an execution context and which stores:

- variables (`var`,VariableDeclaration)
- function declarations
- function formal parameters

It is possible to present variable object as a normal ECMAScript object:

    VO = {};

VO is a property of an execution context:

    activeExecutionContext = {
      VO: {
        // context data (var, FD, function arguments)
      }
    };

**VO is a property of an execution context.**

Indirect referencing VO is possible in global context.

For other contexts, it is purely mechanism of implementation.

### Variable object in different execution contexts

#### Variable object in global context

*Global object* is the object which is created before entering any execution context; this object exists in the single copy,its properties are accessible from any place of the program,the life cycle of the global object ends with program end.

At creation the global object is initialized with such properties as `Math`,`String`,`Date`,`parseInt` etc.,and also by additional

#### Variable object in function context

    VO(functionContext) === AO;
    
An activation object is created on entering the context of a function and initialized by property `argument` which value is the Argument object:

    AO = {
      arguments: <Arg0>
    };  
    
*Arguments* object is a property of the activation object.It contains the following properties:

- callee - the reference to the current function;
- length - quantity of *real passed* arguments;


#### Phases of processing the context code

Processing of the execution context code is divided on two basic stages:

1. Entering the execution context;
2. Code execution

Modifications of the variable are closely related with these two phases.

Notice, that processing of these two stage are the general behavior and independent from the type of the context.

#### Entering the execution context
On entering the execution context(but before the code execution), VO is filled with the following properties:

- for each *formal parameter* of a function (if we are in function execution context), - a property of the variable object with a name and a value of formal parameter is created; for not passed parameters - property of VO with a name of formal parameter and value undefined is created;

- for each *function declaration* (FunctionDeclaration,FD) - a property of the variable object with a name and a value of a function-object is created; if the variable object already contains a property with the same name, replace its value and attributes.

- for each *variable declaration* - a property of the variable object with a name and a value undefined is created; if the variable name is the same as name of already declared formal parameter or a function, the variable declaration does not disturb the existing property.


    console.log(x);
        
    var x = 10;
    console.log(x);
    
    x = 20;
    
    function x() {}
    
    console.log(x);
      
## This value

`this`是JavaScript中十分令人困惑的概念，因为在不同的环境下，它指向的值是不一样的。

One of the most confused mechanisms in JavaScript is the `this` keyword.

It's a special identifier keyword that's automatically defined in the scope of every function.

If the `this` mechanism is so confusing,even to seasoned JavaScript developers, one may wonder why it's even useful?

我们为什么需要`this`：

The motivation and utility of `this`:

        function identify() {
          return this.name.toUpperCase();
        }
          
        function speak() {
          var greeting = "Hello, I'm " + identify.call( this );
          console.log( greeting );
        }
        
        var me = {
          name: "Kyle"
        };
        
        var you = {
          name: "Reader"
        };
        
        identify.call( me );
        identify.call( you );
        
        speak.call( me );
        speak.call( you );
        
我们知道，代码（函数）有其相应的执行上下文。

如果某个函数的执行，依赖于某个对象中包含的数据；那么，除了显式得将该对象作为参数传入函数，是否还有其他解决方法？

利用作用域链：可以将这些数据作为局部变量声明在函数调用的上下文中，但这显然会造成很多问题。
    
This code snippet allows the `identify()` and `speak()` functions to be re-used against multiple context (`me` and `you`) objects.

Instead of relying on `this`, you could have explicitly passed in a context object to both `identify()` and `speak()`.

        function identify(context) {
        	return context.name.toUpperCase();
        }
        
        function speak(context) {
        	var greeting = "Hello, I'm " + identify( context );
        	console.log( greeting );
        }
        
        identify( you ); 
        speak( me ); 

`this` mechanism provides a more elegant way of implicitly "passing along" an object reference, leading to cleaner API design and easier re-use.

The more complex your usage pattern is, the more clearly you'll see that passing context around as an explicit parameter is often messier than passing around a `this` context.

#### call vs apply

它们的作用是什么，有什么区别？

Calls a function with a given this value and arguments provided individually.

区别在于参数的格式

        fun.call(thisArg, arg1, arg2, ...)
        
        fun.apply(thisArg, [argsArray])

#### Call-site

We must inspect the call-site (the location in code where a function is called) to answer the question: what's this `this` a reference to?

#### Default Binding

默认情况下，`this`指向全局对象

`this` points to the global object.

Applied when function called with a plain,un-decorated function reference.

If `strict mode` is in effect,`this` set to `undefined`.

#### Implicit Binding

Another rule to consider is: does the call-site have a context object, also referred to as an owning or containing object.

If so, the implicit binding rule says that it's that object which should be used for the function call's this binding.

##### Implicitly Lost

One of the most common frustrations that `this` binding creates is when an implicitly bound function loses that binding,which usually means it falls back to the default binding.


    function foo() {
      console.log( this.a );
    }
    
    var obj = {
      a: 2;
      foo:foo
    };
    
    var bar = obj.foo;
    
    var a = "oops, global";
    
    bar();
    
Even though
    
The more subtle,more common,and more unexpected way this occurs is when we consider passing a callback function:

    function foo() {
      console.log( this.a );
    }
    
    function doFoo(fn) {
      fn();
    }
    
    var obj = {
      a: 2,
      foo: foo
    }
    
    var a = "oops, global";
    
    doFoo( obj.foo );
    
    

#### Explicit Binding

If we want to force a function call to use a particular object for the `this` binding,without putting a property function reference on the object?

#### `new` binding

When a function is invoked with `new` in front of it,otherwise known as a constructor call,the following things are done automatically:

1. a brand new object is created(aka,constructed) out of thin air

this is a property of the execution context.It's a special object in which context a code is executed.

    activeExecutionContext = {
      VO:{...},
      this:thisValue
    };

A `this` value is a special object which is related with the execution context.Therefore,it may be named as a `context object`.

Any object can be used as `this` value of the context.

The `this` value is a property of the execution context, but not a property of the variable object.

The value is determined on entering the context and is immutable while the code is running in the context.

#### Binding Exceptions

##### Ignored `this`





## Scope chain 作用域链

If to describe briefly and showing the main point, a scope chain is mostly related with inner functions.

As we know, ECMAScript allows creation of inner functions and we can even return these functions from parent functions.

The scope chain is exactly this list of all (parent) variable objects for the inner contexts.

This chain is used for variables lookup.

The scope chain of a function context is created at function call and consists of the AO and the internal [[Scope]] property of this function.

    activeExecutionContext = {
      VO: {...},
      this: thisValue,
      Scope: []
    };
    
where Scope by definition is:

    Scope = AO + [[Scope]]
    
### Function life cycle
    
#### Function creation

It is logical to assume that function should have access to the variable object of a higher context.

In effect,it is exactly

[[Scope]] is a hierarchical chain of all parent variable objects which are above the current function context;the chain is saved to the function at its creation.